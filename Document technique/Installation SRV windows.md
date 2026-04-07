IP : 10.10.10.10
Masque 255.255.255.0
passerelle 10.10.10.254

Identifiants
srv-gestion
P@ssword/59


install DHCP 
- Mise en place des plage
- 10.10.10.0 - serveur
- 10.10.20.0 - admin
- 10.10.30.0 - client
Install DNS 
Install AD (HVO.local)
+ Création des Uo
* Création des User
Création des GPO
- Outils  --> strategie de groupes 
* installation des GPO 
	* Nom de la GPO : GPO_COM_Utilisateurs 
		* Interdire l’accès au panneau de configuration 
		* Désactiver l’invite de commandes (cmd) 
		* Interdire PowerShell  
		* Empêcher l’installation de logiciels 

	* Nom de la GPO : GPO_TECH_Utilisateurs  
		* Accès limité au panneau de configuration (lecture seule) 
		* invite de commandes autorisée 
		* PowerShell autorisé

Installation Urbackup
* Configuration du service 





Réalisation: 
install DHCP 
- Mise en place des plage
Install DNS 
Install AD (HVO.local)
+ Création des Uo
 ![Configuration des Gateways pfSense](../images/Pasted%20image%2020260213115404.png)
  ![Configuration des Gateways pfSense](../images/Pasted%20image%2020260213115514.png)
Création des GPO
- Outils  --> strategie de groupes 

Mise en place des GPO , ajout des Groupe au GPO ![Configuration des Gateways pfSense](../images/Pasted%20image%2020260310091555.png)

Mise en place de Urbackup :
admin
P@ssword/59


Configuration sur le server windows siteB un partage de fichier relier a Urbackup
![Configuration des Gateways pfSense](../images/Pasted%20image%2020260331094609.png)
