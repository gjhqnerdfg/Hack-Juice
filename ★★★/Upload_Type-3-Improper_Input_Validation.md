# Challenge : Upload Type

## Methodology

1. **Accès à la fonctionnalité de téléchargement**  
   Je me suis rendu sur la section permettant d’uploader des fichiers (ex: profile picture, product upload).

2. **Préparation du fichier**  
   J’ai créé un fichier avec une extension non autorisée (ex: `.js`, `.html`, ou `.php`) pour tester les restrictions côté serveur.

3. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON) pour capturer la requête HTTP envoyée lors de l’upload.

4. **Modification des paramètres**  
   J’ai modifié le champ `filename` ou `Content-Type` pour forcer le serveur à accepter le fichier non autorisé.

5. **Envoi de la requête modifiée**  
   J’ai utilisé **Forward** pour envoyer la requête modifiée au serveur.

6. **Observation du résultat**  
   Le serveur a accepté le fichier malgré son type non autorisé, ce qui a permis de bypasser les restrictions d’upload.

---

## Vulnerabilities

1. **Unrestricted File Upload**  
   - Composant affecté : système d’upload de fichiers  
   - Sévérité : **High**

2. **Lack of File Type Validation**  
   - Composant affecté : backend  
   - Sévérité : **High**

3. **Broken Access Control / Security Misconfiguration**  
   - Composant affecté : stockage des fichiers  
   - Sévérité : **Medium**

---

## Risks

1. Possibilité d’exécuter du code malveillant sur le serveur (RCE)  
2. Déploiement de fichiers dangereux (ex: scripts, shell)  
3. Compromission du serveur ou fuite de données  

---

## Actions

1. **Mitigation strategies**  
   - Valider strictement les extensions autorisées côté serveur  
   - Vérifier le type MIME et le contenu réel du fichier  

2. **Remediation fixes**  
   - Bloquer les types de fichiers dangereux  
   - Stocker les fichiers uploadés dans un dossier non accessible publiquement  
   - Scanner les fichiers pour les virus et scripts  

3. **Best practices**  
   - Ne jamais faire confiance aux informations fournies par le client (nom de fichier, type MIME)  
   - Suivre les recommandations OWASP sur l’upload sécurisé de fichiers  
   - Appliquer le principe du moindre privilège pour le stockage des fichiers  