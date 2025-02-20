**Cryptographie Symétrique et Asymétrique : Concepts et Exemples**

## **1. Introduction à la Cryptographie Symétrique et Asymétrique**

### **Différences entre cryptographie symétrique et asymétrique**  

- **Symétrique :**
  - Utilise **une seule clé** pour chiffrer et déchiffrer.
  - **Avantage** : Très rapide et efficace pour des **volumes importants de données** (fichiers volumineux).
  - **Inconvénient** : La clé doit être partagée en toute sécurité.

- **Asymétrique :**
  - Utilise une **paire de clés** (publique et privée).
  - La clé publique sert à **chiffrer**, la clé privée à **déchiffrer**.
  - **Avantage** : Pas besoin de partager la clé privée. Idéal pour des **communications sécurisées** (mails, signatures numériques).
  - **Inconvénient** : Plus lent que le chiffrement symétrique.

- **Hybride :**
  - Combine les deux approches : l’asymétrique pour échanger la clé symétrique en toute sécurité, puis le symétrique pour chiffrer les données.
  - **Utilisation** : Protocoles SSL/TLS (sécurisation des connexions web), messageries chiffrées.

---

## **2. Cryptographie Symétrique avec OpenSSL sous Linux**

### **Chiffrement avec AES-256 CBC et mot de passe**
```bash
openssl enc -aes-256-cbc -pbkdf2 -salt -in fichier.txt -out fichier_chiffre.txt -k mot_de_passe_tres_fort
```

### **Déchiffrement**
```bash
openssl enc -d -aes-256-cbc -pbkdf2 -in fichier_chiffre.txt -out fichier_dechiffre.txt -k mot_de_passe_tres_fort
```

> **Remarque** : La clé est dérivée du mot de passe avec une fonction PBKDF2, et un sel est utilisé pour renforcer la sécurité.

---

## **3. Cryptographie Asymétrique avec OpenSSL sous Linux**

### **Génération de clés RSA (4096 bits)**
```bash
openssl genpkey -algorithm RSA -out cle_privee.pem -pkeyopt rsa_keygen_bits:4096
openssl rsa -pubout -in cle_privee.pem -out cle_publique.pem
```

### **Chiffrement d’un fichier avec la clé publique**
```bash
openssl rsautl -encrypt -inkey cle_publique.pem -pubin -in fichier.txt -out fichier_chiffre_asym.txt
```

### **Déchiffrement avec la clé privée**
```bash
openssl rsautl -decrypt -inkey cle_privee.pem -in fichier_chiffre_asym.txt -out fichier_dechiffre_asym.txt
```

---

## **4. Cryptographie Hybride avec OpenSSL**

### **Étapes :**

1. **Génération d’une clé symétrique (256 bits)** :
   ```bash
   openssl rand -base64 32 > cle_symetrique.key
   ```

2. **Chiffrement de la clé symétrique avec la clé publique RSA** :
   ```bash
   openssl rsautl -encrypt -inkey cle_publique.pem -pubin -in cle_symetrique.key -out cle_symetrique.key.enc
   ```

3. **Chiffrement des données avec la clé symétrique** :
   ```bash
   openssl enc -aes-256-cbc -salt -pbkdf2 -in fichier.txt -out fichier_chiffre_hybride.txt -kfile cle_symetrique.key
   ```

4. **Déchiffrement complet** :
   - Déchiffrez la clé symétrique avec la clé privée :
     ```bash
     openssl rsautl -decrypt -inkey cle_privee.pem -in cle_symetrique.key.enc -out cle_symetrique.key
     ```
   - Déchiffrez les données :
     ```bash
     openssl enc -d -aes-256-cbc -pbkdf2 -in fichier_chiffre_hybride.txt -out fichier_dechiffre.txt -kfile cle_symetrique.key
     ```

---

## **5. Cryptographie Symétrique en Python (AES-256)**

### **Exemple (AES-256 avec mot de passe)** :
```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2HMAC
from cryptography.hazmat.primitives import hashes
import os

password = b"mot_de_passe_tres_fort"
salt = os.urandom(16)

kdf = PBKDF2HMAC(algorithm=hashes.SHA256(), length=32, salt=salt, iterations=100000)
key = kdf.derive(password)

iv = os.urandom(16)
cipher = Cipher(algorithms.AES(key), modes.CBC(iv))
encryptor = cipher.encryptor()

data = b"Message a chiffrer"
padding_length = 16 - len(data) % 16
data += bytes([padding_length]) * padding_length

chiffre = encryptor.update(data) + encryptor.finalize()
print(f"Message chiffré : {chiffre}")
```

---

## **6. Cryptographie Asymétrique en Python (RSA)**

### **Exemple de code (Génération et chiffrement RSA)** :
```python
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives import serialization, hashes

private_key = rsa.generate_private_key(public_exponent=65537, key_size=4096)
public_key = private_key.public_key()

message = b"Message à chiffrer"
ciphertext = public_key.encrypt(
    message,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
print(f"Message chiffré : {ciphertext}")
```

---

## **7. Cryptographie Hybride en Python (RSA + AES)**

### **Exemple de code :**
```python
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
import os

# Génération de la clé symétrique (AES-256)
key_sym = os.urandom(32)

# Génération des clés RSA
private_key = rsa.generate_private_key(public_exponent=65537, key_size=4096)
public_key = private_key.public_key()

# Chiffrement de la clé symétrique avec la clé publique RSA
encrypted_key = public_key.encrypt(
    key_sym,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# Chiffrement des données avec AES
iv = os.urandom(16)
cipher = Cipher(algorithms.AES(key_sym), modes.CBC(iv))
encryptor = cipher.encryptor()

data = b"Message à chiffrer"
padding_length = 16 - len(data) % 16
data += bytes([padding_length]) * padding_length

ciphertext = encryptor.update(data) + encryptor.finalize()
print(f"Message chiffré (AES) : {ciphertext}")
```

---

## **8. Utilisation de Kleopatra**

1. **Installation** :
   ```bash
   sudo apt install kleopatra
   ```
2. **Génération de clés** : Lancez Kleopatra et cliquez sur "New Certificate".
3. **Chiffrement et déchiffrement** : Utilisez l’interface graphique pour sécuriser vos fichiers avec vos clés.

---

## **9. Utilisation de VeraCrypt**

### **Qu’est-ce que VeraCrypt ?**
VeraCrypt est un outil open-source permettant de créer des volumes chiffrés ou de chiffrer des partitions entières.

### **Installation sous Linux**
```bash
sudo apt install veracrypt
```

### **Création d’un volume chiffré**
1. Lancez VeraCrypt avec la commande :
   ```bash
   veracrypt
   ```
2. Cliquez sur **Create Volume** et suivez les étapes :
   - Choisissez **Create an encrypted file container**.
   - Sélectionnez le type de chiffrement (AES-256 est recommandé).
   - Définissez un mot de passe fort.
   - Choisissez la taille du volume et formatez-le.

### **Montage d’un volume chiffré**
1. Ouvrez VeraCrypt.
2. Cliquez sur **Select File** pour choisir votre volume.
3. Cliquez sur **Mount** et entrez votre mot de passe.

### **Démontage d’un volume**
- Sélectionnez le volume et cliquez sur **Dismount**.
