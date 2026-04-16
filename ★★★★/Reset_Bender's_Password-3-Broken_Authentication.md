# Challenge : Reset Bender's Password

## Methodology

1. **Accès au formulaire de réinitialisation**  
   Je me suis rendu sur la page de réinitialisation du mot de passe.

2. **Recherche de l’email de Bender**  
   J’ai identifié l’email de Bender (`bender@juice-sh.op`) pour initier le processus.

3. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON) pour capturer la requête HTTP envoyée lors de la demande de reset.

4. **Modification de la requête**  
   J’ai manipulé les paramètres de la requête afin de réinitialiser le mot de passe de Bender à une valeur connue.

5. **Envoi de la requête modifiée**  
   J’ai utilisé **Forward** pour transmettre la requête modifiée au serveur et observer le résultat.

6. **Connexion avec le nouveau mot de passe**  
   Après la réinitialisation, j’ai pu me connecter au compte de Bender avec le mot de passe choisi.

---

## Vulnerabilities

1. **Insecure Direct Object Reference (IDOR)**  
   - Composant affecté : API de réinitialisation de mot de passe  
   - Sévérité : **High**

2. **Broken Authentication / Password Reset Flaw**  
   - Composant affecté : mécanisme de reset de mot de passe  
   - Sévérité : **Critical**

3. **Lack of Server-Side Validation**  
   - Composant affecté : backend  
   - Sévérité : **High**

---

## Risks

1. Prise de contrôle des comptes utilisateurs  
2. Divulgation ou altération des données sensibles  
3. Perte de confiance des utilisateurs envers la plateforme  

---

## Actions

1. **Mitigation strategies**  
   - Vérifier l’identité de l’utilisateur avant d’autoriser un reset  
   - Générer des tokens uniques et sécurisés pour chaque demande  

2. **Remediation fixes**  
   - Implémenter un système de reset sécurisé avec expiration du token  
   - Ne jamais permettre la réinitialisation de mot de passe via des paramètres manipulables  

3. **Best practices**  
   - Suivre les recommandations OWASP sur les processus de réinitialisation de mot de passe  
   - Logger toutes les requêtes de reset et détecter les anomalies  
   - Valider tous les paramètres côté serveur  