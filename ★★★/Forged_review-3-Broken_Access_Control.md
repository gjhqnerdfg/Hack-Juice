# Challenge : Forged Review

## Methodology

1. **Authentification**  
   Je me suis connecté à l’application avec un compte utilisateur valide.

2. **Accès à un produit**  
   Je me suis rendu sur la page d’un produit afin de pouvoir laisser un avis.

3. **Remplissage du formulaire**  
   J’ai complété le formulaire de review avec des informations valides.

4. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON).

5. **Soumission du formulaire**  
   J’ai cliqué sur **Submit** pour capturer la requête HTTP.

6. **Modification des données**  
   Dans Burp Suite, j’ai modifié le paramètre utilisateur (user / userId) afin d’utiliser l’identité d’un autre utilisateur existant.

7. **Envoi de la requête**  
   J’ai utilisé **Forward** pour envoyer la requête modifiée au serveur, puis désactivé l’interception (Intercept OFF).

---

## Vulnerabilities

1. **Insecure Direct Object Reference (IDOR)**  
   - Composant affecté : système de gestion des reviews  
   - Sévérité : **High**

2. **Broken Authentication / Impersonation**  
   - Composant affecté : API des avis produits  
   - Sévérité : **High**

3. **Lack of Server-Side Validation**  
   - Composant affecté : backend  
   - Sévérité : **Medium**

---

## Risks

1. Usurpation d’identité d’utilisateurs  
2. Manipulation des avis produits  
3. Perte de crédibilité et de confiance des utilisateurs  

---

## Actions

1. **Mitigation strategies**  
   - Vérifier l’identité utilisateur côté serveur  
   - Associer automatiquement les actions à l’utilisateur authentifié  

2. **Remediation fixes**  
   - Supprimer les champs utilisateur modifiables côté client  
   - Implémenter un contrôle d’accès strict sur les actions  

3. **Best practices**  
   - Ne jamais faire confiance aux données envoyées par le client  
   - Utiliser des tokens sécurisés (JWT / session)  
   - Suivre les recommandations OWASP sur les IDOR et l’authentification  