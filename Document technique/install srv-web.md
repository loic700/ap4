se connecter en ssh
```
ssh -J admin@192.168.202.11 srv-web@10.10.30.1
```
IP : 10.10.30.1
Masque : 255.255.255.0
Passerelle : 10.10.30.254

srv-web
P@ssword/59

Installation du package apache2
- configuration site worldpress
- configuration fichier de synchronisation db










Réalisation :
config sur 


  GNU nano 7.2                         /etc/apache2/sites-available/cli1-srv-web.conf *
  
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName 10.10.30.1

    # Dossier où se trouve ton code source
    DocumentRoot /var/www/html

    <Directory /var/www/html>
        Options -Indexes +FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    # Logs pour débugger en cas de problème
    ErrorLog ${APACHE_LOG_DIR}/cli1_error.log
    CustomLog ${APACHE_LOG_DIR}/cli1_access.log combined
</VirtualHost>
```







configuration d'un fichier 

```
sudo nano /var/www/html/wp-config.php`
```

```
define( 'DB_NAME', 'wordpress_db' );
define( 'DB_USER', 'wp_user' );
define( 'DB_PASSWORD', 'P@ssword/59' );

define( 'DB_HOST', '10.10.30.X' );
```

![Configuration des Gateways pfSense](../images/Pasted%20image%2020260331111237.png)






