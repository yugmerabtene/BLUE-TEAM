### **2. ElasticSearch Installation**

#### **Objectif** :
L'objectif de cette section est de guider les participants à travers l'installation et la configuration de base d'Elasticsearch. À la fin de cette section, les participants devraient être en mesure d'installer Elasticsearch sur différentes plateformes, de le configurer, et de vérifier que l'installation fonctionne correctement.

---

#### **Contenu** :

1. **Prérequis système** :
   - **Mémoire** : Elasticsearch est gourmand en mémoire. Il est recommandé d'avoir au moins 4 Go de RAM disponible.
   - **Processeur** : Un processeur multi-cœur est recommandé pour de meilleures performances.
   - **Espace disque** : L'espace disque nécessaire dépend du volume de données à indexer. Un disque SSD est recommandé pour de meilleures performances.
   - **Système d'exploitation** : Elasticsearch est compatible avec Linux, Windows, et macOS.
   - **Java** : Elasticsearch nécessite Java (version 8 ou 11). Assurez-vous que Java est installé et configuré correctement.

2. **Installation d'Elasticsearch sur différentes plateformes** :
   - **Linux** :
     - Téléchargez le package Elasticsearch depuis le site officiel.
     - Installez le package avec la commande appropriée (par exemple, `dpkg` pour Debian/Ubuntu ou `rpm` pour CentOS/RHEL).
     - Configurez Elasticsearch pour qu'il démarre automatiquement au démarrage du système.
   - **Windows** :
     - Téléchargez le fichier ZIP d'Elasticsearch depuis le site officiel.
     - Extrayez le fichier ZIP dans un répertoire de votre choix.
     - Exécutez Elasticsearch en lançant le fichier `elasticsearch.bat` dans le répertoire `bin`.
   - **macOS** :
     - Téléchargez le fichier TAR d'Elasticsearch depuis le site officiel.
     - Extrayez le fichier TAR dans un répertoire de votre choix.
     - Exécutez Elasticsearch en lançant le fichier `elasticsearch` dans le répertoire `bin`.

3. **Configuration de base (fichier `elasticsearch.yml`)** :
   - **Chemin du fichier de configuration** : Le fichier de configuration principal d'Elasticsearch est `elasticsearch.yml`, situé dans le répertoire `config`.
   - **Paramètres de base** :
     - `cluster.name` : Nom du cluster Elasticsearch. Par défaut, c'est `elasticsearch`.
     - `node.name` : Nom du nœud. Par défaut, c'est le nom d'hôte de la machine.
     - `network.host` : Adresse IP ou nom d'hôte sur lequel Elasticsearch écoute. Par défaut, c'est `localhost`.
     - `http.port` : Port HTTP sur lequel Elasticsearch écoute. Par défaut, c'est `9200`.
   - **Exemple de configuration** :
     ```yaml
     cluster.name: my_cluster
     node.name: node-1
     network.host: 0.0.0.0
     http.port: 9200
     ```

4. **Démarrage et arrêt du service Elasticsearch** :
   - **Linux** :
     - Pour démarrer Elasticsearch : `sudo systemctl start elasticsearch`
     - Pour arrêter Elasticsearch : `sudo systemctl stop elasticsearch`
     - Pour vérifier l'état du service : `sudo systemctl status elasticsearch`
   - **Windows** :
     - Pour démarrer Elasticsearch : Exécutez `elasticsearch.bat` dans le répertoire `bin`.
     - Pour arrêter Elasticsearch : Fermez la fenêtre de commande ou utilisez `Ctrl+C`.
   - **macOS** :
     - Pour démarrer Elasticsearch : Exécutez `./elasticsearch` dans le répertoire `bin`.
     - Pour arrêter Elasticsearch : Fermez la fenêtre de terminal ou utilisez `Ctrl+C`.

5. **Vérification de l'installation via des requêtes HTTP simples** :
   - Une fois Elasticsearch démarré, vous pouvez vérifier qu'il fonctionne correctement en envoyant une requête HTTP à l'adresse `http://localhost:9200`.
   - **Exemple de requête** :
     ```bash
     curl -X GET "localhost:9200"
     ```
   - **Réponse attendue** :
     ```json
     {
       "name" : "node-1",
       "cluster_name" : "my_cluster",
       "cluster_uuid" : "abc123",
       "version" : {
         "number" : "7.10.0",
         "build_flavor" : "default",
         "build_type" : "tar",
         "build_hash" : "abc123",
         "build_date" : "2020-11-05T10:36:47.659Z",
         "build_snapshot" : false,
         "lucene_version" : "8.7.0",
         "minimum_wire_compatibility_version" : "6.8.0",
         "minimum_index_compatibility_version" : "6.0.0-beta1"
       },
       "tagline" : "You Know, for Search"
     }
     ```

---

#### **Exemples pratiques** :
- **Installation sur Linux** : Suivez les étapes pour installer Elasticsearch sur une machine Linux et configurez-le pour qu'il démarre automatiquement.
- **Configuration de base** : Modifiez le fichier `elasticsearch.yml` pour changer le nom du cluster et le nom du nœud.
- **Vérification de l'installation** : Utilisez `curl` ou un navigateur web pour vérifier qu'Elasticsearch fonctionne correctement.
