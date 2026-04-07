se connecter en ssh
```
ssh -J admin@192.168.202.11 cisco@10.10.30.2
```
IP : 10.10.30.2
Masque : 255.255.255.0
Passerelle : 10.10.10.254

cisco
P@ssword/59

Installation du package mysql-server
- configuration base de donné 
- création d'un user pour la synchronisation site web 





Réalisation :
création bdd

```
CREATE DATABASE wordpress_db;
CREATE USER 'wp_user'@'10.10.30.1' IDENTIFIED BY 'P@ssword/59';
GRANT ALL PRIVILEGES ON wordpress_db.* TO 'wp_user'@'10.10.30.1';
FLUSH PRIVILEGES;
EXIT;
```
