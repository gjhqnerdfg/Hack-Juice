# Challenge : Forged Feedback

## Methodology

1. **Authentification**  
   Je me suis connecté à l’application avec un compte utilisateur valide.

2. **Accès à la fonctionnalité**  
   Je me suis rendu sur la section **Customer Feedback** afin d’envoyer un avis.

3. **Remplissage du formulaire**  
   J’ai complété le formulaire de feedback avec des données valides.

4. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON).

5. **Envoi de la requête**  
   J’ai cliqué sur **Submit** sur le site pour capturer la requête HTTP.

6. **Modification des données**  
   Dans Burp Suite, j’ai modifié le paramètre `userId` afin d’usurper l’identité d’un autre utilisateur.

7. **Transmission de la requête**  
   J’ai utilisé **Forward** pour envoyer la requête modifiée au serveur, puis désactivé l’interception (Intercept OFF).

---

## Vulnerabilities

1. **Insecure Direct Object Reference (IDOR)**  
   - Composant affecté : système de gestion des utilisateurs  
   - Sévérité : **High**

2. **Broken Authentication**  
   - Composant affecté : API de feedback  
   - Sévérité : **High**

3. **Lack of Server-Side Validation**  
   - Composant affecté : backend (traitement des requêtes)  
   - Sévérité : **Medium**

---

## Risks

1. Usurpation d’identité d’autres utilisateurs  
2. Manipulation des avis clients  
3. Perte de confiance des utilisateurs envers la plateforme  

---

## Actions

1. **Mitigation strategies**  
   - Vérifier l’identité de l’utilisateur côté serveur  
   - Ne jamais faire confiance aux données envoyées par le client  

2. **Remediation fixes**  
   - Supprimer le champ `userId` côté client  
   - Associer automatiquement les actions à l’utilisateur authentifié  

3. **Best practices**  
   - Implémenter un système d’authentification sécurisé (sessions / JWT)  
   - Valider toutes les requêtes côté serveur  
   - Suivre les recommandations OWASP sur les IDOR  