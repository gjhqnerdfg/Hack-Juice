# Challenge : Poison Null Byte

## Methodology

1. **Compréhension de l’objectif**  
   Le but était de bypass des contrôles de sécurité afin d’accéder à un fichier normalement non accessible.

2. **Analyse des chemins de fichiers**  
   J’ai identifié qu’il était possible d’accéder à certains fichiers via des endpoints comme `/ftp/`.

3. **Test des restrictions**  
   J’ai tenté d’accéder directement à des fichiers sensibles (ex: `.pyc`), mais l’accès était bloqué ou filtré.

4. **Utilisation d’un Null Byte**  
   J’ai utilisé un **Poison Null Byte** (`%00`) encodé en URL (`%2500`) pour contourner les vérifications de sécurité.

5. **Construction du payload**  
   J’ai utilisé un chemin comme :  /ftp/encrypt.pyc%2500.md

   Ce qui permet de tromper le serveur :
- le backend interprète `.pyc`
- le filtre pense traiter un fichier `.md`

6. **Accès au fichier**  
Le serveur a accepté la requête et m’a permis d’accéder à un fichier normalement restreint.

---

##  Vulnerabilities

1. **Poison Null Byte Injection**  
- Composant affecté : système de gestion de fichiers / backend  
- Sévérité : **High**

2. **Improper Input Validation**  
- Composant affecté : traitement des chemins de fichiers  
- Sévérité : **High**

3. **Security Misconfiguration (File Access Control)**  
- Composant affecté : serveur de fichiers (/ftp)  
- Sévérité : **Medium**

---

## Risks

1. Accès non autorisé à des fichiers sensibles  
2. Fuite d’informations critiques (code source, configs)  
3. Possibilité d’exploitation avancée du serveur  

---

## Actions

1. **Mitigation strategies**  
- Valider strictement les chemins de fichiers côté serveur  
- Bloquer les caractères spéciaux comme les null bytes  

2. **Remediation fixes**  
- Normaliser les entrées avant traitement (canonicalization)  
- Refuser toute requête contenant des encodages suspects (`%00`, `%2500`)  

3. **Best practices**  
- Ne jamais se baser uniquement sur l’extension pour sécuriser un fichier  
- Implémenter des contrôles d’accès robustes côté serveur  
- Suivre les recommandations OWASP sur la validation des entrées et accès fichiers  