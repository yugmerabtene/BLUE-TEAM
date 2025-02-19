### **Lab 01 : Mise en place d'une architecture réseau vulnérable**  
L'entreprise dispose d'une infrastructure ancienne et vulnérable composée de :  
- **1 serveur Windows Server 2019** avec un service FTP et/ou des fichiers partagés (dedans les factures en pdf, les identifiants du server web linux/wordpress/et bdd/ et tout autre infos sensible, dans un f le tout dans fichier texte) .  
- **1 client Windows XP** utilisé comme client par le service livraison et stock.  
- **1 client Windows 10** utilisé par le service de comptabilité et de gestion, enregistre tout leurs fichiers sur le serveur windows dans un dossier partager ou sur le FTP.  
- **1 serveur Linux** hébergeant le site e-commerce de l'entreprise, basé sur WordPress.

**Objectif :**  
Les élèves doivent reproduire cette infrastructure afin de simuler un environnement vulnérable qui pourra ensuite être analysé et attaqué.

