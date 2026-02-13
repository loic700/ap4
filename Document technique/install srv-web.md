se connecter en ssh
```
ssh -J admin@192.168.202.11 srv-web@10.10.30.1
```
IP : 10.10.30.1
Masque : 255.255.255.0
Passerelle : 10.10.10.254

Installation du package apache2


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