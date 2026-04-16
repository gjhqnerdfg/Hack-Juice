#  Challenge : Nested Easter Egg

##  Methodology

1. **Compréhension de l’objectif**  
   Le but était d’accéder à un fichier caché en contournant les restrictions d’accès.

2. **Utilisation d’un Poison Null Byte**  
   J’ai utilisé une technique de **Poison Null Byte Injection** pour bypass les contrôles sur les extensions de fichiers.

3. **Construction du payload**  
   J’ai utilisé l’URL suivante :  /ftp/eastere.gg%2500.md

   Ce qui permet :
- au serveur d’interpréter le fichier réel (`.gg`)
- au filtre de voir un fichier `.md`

4. **Accès au fichier caché**  
Cette requête m’a permis d’accéder à un fichier contenant une chaîne encodée : L2d1ci9xcmlmL25lci9mYi9zaGFhbC9ndXJsL3V2cS9uYS9ybmZncmUvcnR0L2p2Z3V2YS9ndXIvcm5mZ3JlL3J0dA==


5. **Identification du chiffrement**  
J’ai utilisé un outil en ligne (ex: dcode.fr) pour identifier le type d’encodage → **Base64**.

6. **Décodage Base64**  
Après décodage, j’ai obtenu :  /gur/qrif/ner/fb/shaal/gurl/uvq/na/rnfgre/rtt/jvguva/gur/rnfgre/rtt


7. **Deuxième analyse (ROT13)**  
J’ai réanalysé cette chaîne avec un détecteur de chiffrement et identifié un encodage **ROT13**.

8. **Décodage final**  
Après décodage ROT13, j’ai obtenu le chemin réel :  /the/devs/are/so/funny/they/hid/an/easter/egg/within/the/easter/egg


9. **Accès à l’URL finale**  
J’ai entré ce chemin dans l’URL, ce qui a permis de valider le challenge.

---

##  Vulnerabilities

1. **Poison Null Byte Injection**  
- Composant affecté : système de fichiers (/ftp)  
- Sévérité : **High**

2. **Information Disclosure (Encoded Data Exposure)**  
- Composant affecté : fichiers accessibles publiquement  
- Sévérité : **Medium**

3. **Improper Input Validation**  
- Composant affecté : validation des chemins  
- Sévérité : **High**

---

##  Risks

1. Accès non autorisé à des fichiers sensibles  
2. Exposition de données internes (même encodées)  
3. Possibilité d’exploitation plus avancée du serveur  

---

##  Actions

1. **Mitigation strategies**  
- Bloquer les caractères spéciaux comme les null bytes (`%00`)  
- Valider strictement les chemins de fichiers  

2. **Remediation fixes**  
- Implémenter une normalisation des entrées (canonicalization)  
- Empêcher l’accès direct aux fichiers sensibles via URL  

3. **Best practices**  
- Ne jamais exposer de données sensibles même encodées (Base64 ≠ sécurité)  
- Mettre en place des contrôles d’accès stricts côté serveur  
- Suivre les recommandations OWASP sur la validation des entrées  