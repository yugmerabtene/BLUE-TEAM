### LAB-06 : Automatisation de la Réponse avec un Playbook Ansible  

**Objectifs du Lab :**  
1. Comprendre ce qu’est un playbook Ansible et son rôle en sécurité.  
2. Créer un playbook Ansible pour automatiser des réponses aux incidents.  
3. Déployer et exécuter ce playbook sur des systèmes simulés.  

---

## I. Préparation  

### A. Environnement de test  
- **Ansible Control Node :** Machine qui exécutera les commandes Ansible.  
- **Cibles distantes (hosts) :** Machines simulant des systèmes vulnérables ou compromis.  
- Installer Ansible sur le Control Node.  

### B. Outils nécessaires  
- **Ansible (version 2.9 ou ultérieure)**  
- **Machines virtuelles pour simuler les incidents**  
- **Playbooks prédéfinis ou créés manuellement**  

---

## II. Introduction aux Playbooks  

Un playbook Ansible est un fichier YAML contenant des tâches automatisées. En réponse aux incidents, les playbooks permettent de :  
1. **Identifier** un incident ou une anomalie.  
2. **Contenir** une menace en isolant des systèmes compromis.  
3. **Nettoyer** les fichiers ou processus malveillants.  
4. **Restaurer** un état fonctionnel.  

---

## III. Création du Playbook Ansible  

### A. Exemples de scénarios d’incidents à automatiser  

1. **Blocage d'une IP malveillante**  
2. **Fermeture de ports ouverts**  
3. **Vérification et suppression de fichiers malveillants**  

---

### B. Structure du Playbook  

Exemple de Playbook de réponse :  

```yaml
---
- name: Réponse à un incident de sécurité
  hosts: all
  tasks:
    - name: Identifier les connexions actives suspectes
      shell: "netstat -tunlp | grep ESTABLISHED"
      register: active_connections

    - name: Bloquer une IP malveillante
      ansible.builtin.command:
        cmd: "iptables -A INPUT -s {{ malicious_ip }} -j DROP"

    - name: Supprimer les fichiers malveillants détectés
      ansible.builtin.find:
        paths: /var/log/
        patterns: "*.malware"
      register: suspicious_files

    - name: Supprimer les fichiers détectés
      ansible.builtin.file:
        path: "{{ item.path }}"
        state: absent
      loop: "{{ suspicious_files.files }}"
```  

---

## IV. Déploiement du Playbook  

1. **Configuration des hosts (inventory)**  
   Créer un fichier `inventory.ini` :  

   ```ini
   [webservers]
   192.168.1.10 ansible_user=admin ansible_ssh_private_key_file=~/.ssh/id_rsa
   192.168.1.11 ansible_user=admin ansible_ssh_private_key_file=~/.ssh/id_rsa
   ```  

2. **Exécution du Playbook**  
   Commande :  
   ```bash
   ansible-playbook -i inventory.ini playbook-incident-response.yml
   ```  

---

## V. Simulation et Validation  

1. Simuler une connexion malveillante et vérifier que le playbook la bloque.  
2. Introduire un fichier malveillant dans le répertoire surveillé et observer sa suppression automatique.  
3. Vérifier les logs et la sortie d’Ansible pour confirmer l’application des règles.  

---

## VI. Évaluation et Améliorations  

1. **Évaluation des résultats :**  
   - Le playbook a-t-il détecté et supprimé les menaces correctement ?  
   - Des étapes manquaient-elles ?  
   - Le playbook a-t-il été exécuté rapidement ?  

2. **Améliorations potentielles :**  
   - Ajouter des notifications par e-mail ou Slack lors d’un incident.  
   - Créer des scénarios plus complexes (ex : détection de ransomware).  
   - Intégration avec un SIEM pour une réponse automatisée.  
