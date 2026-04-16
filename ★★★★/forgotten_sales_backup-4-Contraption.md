#  Challenge : Forgotten Sales Backup

##  Methodology

1. **Compréhension de l’objectif**  
   Le but était d’accéder à un fichier de sauvegarde oublié contenant des informations sensibles.

2. **Exploration des chemins (/ftp)**  
   J’ai exploré le répertoire `/ftp/` afin d’identifier des fichiers accessibles publiquement.

3. **Recherche de fichiers sensibles**  
   J’ai testé différents noms de fichiers courants, notamment des fichiers de backup comme `.bak`.

4. **Accès direct au fichier**  
   J’ai utilisé l’URL suivante :  /ftp/package.json.bak

   ce qui m’a permis d’accéder à une sauvegarde du fichier `package.json`.

5. **Analyse du contenu**  
Le fichier contenait des informations internes sur l’application (configuration, dépendances, etc.), validant ainsi le challenge.

---

## Vulnerabilities

1. **Sensitive Data Exposure**  
- Composant affecté : fichiers de configuration / backup  
- Sévérité : **High**

2. **Security Misconfiguration**  
- Composant affecté : serveur de fichiers (/ftp)  
- Sévérité : **High**

3. **Improper Access Control**  
- Composant affecté : gestion des accès fichiers  
- Sévérité : **Medium**

---

## Risks

1. Fuite d’informations sensibles (configuration, dépendances)  
2. Aide à un attaquant pour préparer des attaques ciblées  
3. Exposition de données internes critiques  

---

## Actions

1. **Mitigation strategies**  
- Restreindre l’accès aux fichiers sensibles  
- Ne jamais exposer de fichiers de backup en production  

2. **Remediation fixes**  
- Supprimer les fichiers `.bak` du serveur public  
- Configurer correctement les permissions d’accès  

3. **Best practices**  
- Ne jamais stocker de fichiers sensibles dans des répertoires publics  
- Mettre en place des audits réguliers des fichiers exposés  
- Suivre les recommandations OWASP sur la gestion des fichiers sensibles  