### **Énoncé du Projet : Chiffrement des Dossiers et Base MySQL avec Options Flexibles**  

L'objectif est de développer un script Python complet avec les fonctionnalités suivantes :  

1. **Menu Principal** : Proposer des options pour chiffrer des dossiers, exporter et chiffrer une base de données MySQL, envoyer la clé au serveur FTP, ou quitter.  
2. **Options Nullable** : Si une option ou une information n'est pas fournie par l'utilisateur, le script doit ignorer cette action.  
3. **Chiffrement des Fichiers et Dossiers** : Tous les fichiers des dossiers spécifiés seront chiffrés avec une clé symétrique.  
4. **Chiffrement MySQL avec Exportation** : Option d'exporter la base MySQL sous forme d’un fichier `.sql`, de le chiffrer et de l’envoyer sur un serveur FTP.  
5. **Envoi de la clé de chiffrement au serveur FTP** : La clé générée peut être envoyée au serveur FTP, avec option de suppression locale après l'envoi.  

---

### **Code Complet :**

```python
import os
import mysql.connector
import ftplib
from cryptography.fernet import Fernet
import subprocess

# Fonction pour générer une clé symétrique
def generate_key():
    return Fernet.generate_key()

# Fonction pour chiffrer un fichier
def encrypt_file(file_path, key):
    cipher = Fernet(key)
    with open(file_path, 'rb') as file:
        file_data = file.read()
    encrypted_data = cipher.encrypt(file_data)
    with open(file_path, 'wb') as file:
        file.write(encrypted_data)

# Fonction pour chiffrer tous les fichiers dans un dossier
def encrypt_folder(folder_path, key):
    for root, _, files in os.walk(folder_path):
        for file in files:
            file_path = os.path.join(root, file)
            encrypt_file(file_path, key)
            print(f"Fichier {file_path} chiffré avec succès.")

# Fonction pour exporter et chiffrer une base de données MySQL
def export_and_encrypt_db(host, user, password, database, key):
    try:
        export_file = f"{database}.sql"
        command = f"mysqldump -h {host} -u {user} -p{password} {database} > {export_file}"
        subprocess.run(command, shell=True, check=True)
        encrypt_file(export_file, key)
        print(f"Base de données {database} exportée et chiffrée avec succès.")
        return export_file
    except Exception as e:
        print(f"Erreur lors de l'exportation de la base de données : {e}")
        return None

# Fonction pour envoyer un fichier sur un serveur FTP
def send_file_to_ftp(ftp_host, ftp_user, ftp_password, file_path):
    try:
        with ftplib.FTP(ftp_host) as ftp:
            ftp.login(ftp_user, ftp_password)
            with open(file_path, 'rb') as file:
                ftp.storbinary(f"STOR {os.path.basename(file_path)}", file)
        print(f"Fichier {file_path} envoyé avec succès au serveur FTP.")
    except Exception as e:
        print(f"Erreur lors de l'envoi du fichier au serveur FTP : {e}")

# Fonction pour afficher le menu principal
def display_menu():
    print("\n--- Menu Principal ---")
    print("1. Chiffrer des dossiers")
    print("2. Exporter, chiffrer et envoyer une base de données MySQL")
    print("3. Envoyer la clé de chiffrement au serveur FTP")
    print("4. Quitter")

# Fonction principale
def main():
    # Génération de la clé
    key = generate_key()

    # Demander les informations nécessaires (nullables)
    ftp_host = input("Entrez l'adresse du serveur FTP (laisser vide si non nécessaire) : ").strip()
    ftp_user = input("Entrez le nom d'utilisateur FTP (laisser vide si non nécessaire) : ").strip()
    ftp_password = input("Entrez le mot de passe FTP (laisser vide si non nécessaire) : ").strip()

    db_host = input("Entrez l'adresse du serveur MySQL (laisser vide si non nécessaire) : ").strip()
    db_user = input("Entrez le nom d'utilisateur MySQL (laisser vide si non nécessaire) : ").strip()
    db_password = input("Entrez le mot de passe MySQL (laisser vide si non nécessaire) : ").strip()
    db_name = input("Entrez le nom de la base de données à chiffrer (laisser vide si non nécessaire) : ").strip()

    while True:
        display_menu()
        choice = input("Choisissez une option : ")

        if choice == "1":
            # Chiffrer des dossiers
            folders = input("Entrez les chemins des dossiers à chiffrer, séparés par des virgules (laisser vide pour ignorer) : ").strip()
            if folders:
                for folder in folders.split(','):
                    folder = folder.strip()
                    if os.path.isdir(folder):
                        encrypt_folder(folder, key)
                    else:
                        print(f"Dossier {folder} introuvable.")
            else:
                print("Aucun dossier spécifié, retour au menu principal.")

        elif choice == "2":
            # Exporter, chiffrer et envoyer la base de données MySQL
            if db_host and db_user and db_password and db_name:
                export_file = export_and_encrypt_db(db_host, db_user, db_password, db_name, key)
                if export_file and ftp_host and ftp_user and ftp_password:
                    send_file_to_ftp(ftp_host, ftp_user, ftp_password, export_file)
                    os.remove(export_file)  # Supprimer le fichier local après envoi
            else:
                print("Informations MySQL manquantes, retour au menu principal.")

        elif choice == "3":
            # Envoyer la clé au serveur FTP
            if ftp_host and ftp_user and ftp_password:
                key_file = "encryption_key.key"
                with open(key_file, 'wb') as file:
                    file.write(key)
                send_file_to_ftp(ftp_host, ftp_user, ftp_password, key_file)
                delete_key = input("Souhaitez-vous supprimer la clé localement après l'envoi ? (oui/non) : ").strip().lower()
                if delete_key == "oui":
                    os.remove(key_file)
                    print("Clé supprimée localement.")
            else:
                print("Informations FTP manquantes, envoi de la clé ignoré.")

        elif choice == "4":
            # Quitter le programme
            print("Fin du programme.")
            break

        else:
            print("Option invalide, veuillez réessayer.")

if __name__ == "__main__":
    main()
```

---

### **Explications :**  

1. **Options Nullable** : Si l'utilisateur ne fournit pas d'informations pour MySQL ou FTP, les actions correspondantes sont ignorées sans erreur.  
2. **Menu Principal** : Permet à l'utilisateur de choisir parmi les options disponibles.  
3. **Chiffrement des Dossiers** : Les dossiers spécifiés sont chiffrés avec la clé générée.  
4. **Export et Chiffrement MySQL** : La base MySQL est exportée et chiffrée avant d'être envoyée au serveur FTP.  
5. **Envoi de la Clé** : La clé peut être envoyée au serveur FTP, avec option de suppression locale après envoi.  

---

### **Prérequis :**  
1. **Bibliothèques nécessaires** :  
   Installe les bibliothèques Python avec :  
   ```bash
   pip install cryptography mysql-connector-python
   ```  
2. **Utilisation de `mysqldump`** : Assure-toi que `mysqldump` est installé sur ton système pour exporter la base de données.  

