[installation docker ](https://doc.ubuntu-fr.org/docker)

config du docker compose 

```
version: '3.8'

services:
  db:
    image: mariadb:10.6
    container_name: nextcloud_db
    restart: always
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW
    environment:
      - MYSQL_ROOT_PASSWORD=K3p5_88_mZqR92_Secure_Root
      - MYSQL_PASSWORD=Nc_User_2026_Lx_Strong_Pass
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
    volumes:
      - /home/fl_ap4_docker01/nextcloud/db:/var/lib/mysql
    networks:
      - proxy-net

  app:
    image: nextcloud:stable-apache
    container_name: nextcloud_app
    restart: always
    ports:
      - "8080:80" # Permet à Nginx (sur la machine) de parler au Docker
    environment:
      - MYSQL_HOST=db
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_PASSWORD=Nc_User_2026_Lx_Strong_Pass
      - NEXTCLOUD_TRUSTED_DOMAINS=cloud.local 10.10.10.1
      - OVERWRITEHOST=10.10.10.1
      - OVERWRITEPROTOCOL=http
      - TRUSTED_PROXIES=127.0.0.1 # Comme Nginx est sur la machine, c'est l'IP locale
    volumes:
      - /home/fl_ap4_docker01/nextcloud/data:/var/www/html
    depends_on:
      - db
    networks:
      - proxy-net

networks:
  proxy-net:
    external: true
```



on fait le nginx 

```
sudo nano /etc/nginx/sites-available/nextcloud
```


```
server {
    listen 80;
    server_name 10.10.10.1 cloud.local;

    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        # Indispensable pour éviter les timeouts sur les gros fichiers
        client_max_body_size 10G;
        proxy_buffering off;
    }
}
```