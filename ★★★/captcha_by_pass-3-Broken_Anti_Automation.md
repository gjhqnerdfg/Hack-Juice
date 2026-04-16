# Challenge : CAPTCHA Bypass

## Methodology

1. **Authentification**  
   Je me suis connecté à l’application avec un compte utilisateur valide.

2. **Accès à la fonctionnalité**  
   Je me suis rendu sur la section **Customer Feedback**.

3. **Remplissage du formulaire**  
   J’ai complété le formulaire avec des informations valides.

4. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON).

5. **Soumission du formulaire**  
   J’ai cliqué sur **Submit** afin de capturer la requête HTTP.

6. **Modification des données**  
   Dans Burp Suite, j’ai modifié le paramètre `rating` en lui donnant une valeur invalide (ex: `20`), ce qui ne devrait normalement pas être accepté.

7. **Envoi de la requête**  
   J’ai utilisé **Forward** pour envoyer la requête modifiée au serveur, puis désactivé l’interception (Intercept OFF).

---

## Vulnerabilities

1. **CAPTCHA Bypass**  
   - Composant affecté : système de validation du formulaire  
   - Sévérité : **High**

2. **Lack of Server-Side Validation**  
   - Composant affecté : backend (API de feedback)  
   - Sévérité : **High**

3. **Client-Side Validation Only**  
   - Composant affecté : formulaire frontend  
   - Sévérité : **Medium**

---

## Risks

1. Soumission automatisée de formulaires (spam / bots)  
2. Altération des données (ex: notes incohérentes)  
3. Dégradation de la qualité et de la fiabilité du service  

---

## Actions

1. **Mitigation strategies**  
   - Implémenter une validation côté serveur stricte  
   - Vérifier les valeurs autorisées pour chaque champ  

2. **Remediation fixes**  
   - Refuser toute valeur hors limites (ex: rating > 5)  
   - Vérifier le CAPTCHA côté serveur et non uniquement côté client  

3. **Best practices**  
   - Ne jamais faire confiance aux données côté client  
   - Implémenter des protections anti-bot robustes (reCAPTCHA côté serveur)  
   - Suivre les recommandations OWASP sur la validation des entrées  