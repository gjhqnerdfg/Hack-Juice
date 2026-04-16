# Challenge : Score Board

## Methodology

1. **Reconnaissance (OSINT)**  
   J’ai exploré l’interface de l’application en recherchant des éléments cachés ou non accessibles directement depuis le menu principal.

2. **Enumeration des routes**  
   J’ai inspecté le code source de la page avec les outils de développement du navigateur (DevTools) afin d’identifier des chemins ou endpoints non documentés.

3. **Analyse du frontend**  
   En parcourant les fichiers JavaScript chargés côté client, j’ai identifié une route interne liée au scoreboard (`/score-board`).

4. **Accès direct à la ressource**  
   J’ai accédé manuellement à l’URL `/score-board` dans le navigateur pour afficher une page normalement cachée.

---

## Vulnerabilities

1. **Unrestricted Access to Sensitive Endpoint**  
   - Composant affecté : routing / interface utilisateur  
   - Sévérité : **Low**

2. **Security Through Obscurity**  
   - Composant affecté : frontend (JavaScript)  
   - Sévérité : **Low**

3. **Improper Access Control (Broken Access Control)**  
   - Composant affecté : système de navigation  
   - Sévérité : **Medium**

---

## Risks

1. Divulgation d’informations internes (liste des challenges)  
2. Aide involontaire à un attaquant pour progresser dans l’exploitation  
3. Réduction de la difficulté globale de la sécurité de l’application  

---

## Actions

1. **Mitigation strategies**  
   - Implémenter un contrôle d’accès sur les routes sensibles  
   - Vérifier les permissions côté serveur et pas uniquement côté client  

2. **Remediation fixes**  
   - Restreindre l’accès à `/score-board` aux utilisateurs autorisés  
   - Supprimer les références aux routes sensibles dans le code frontend  

3. **Best practices**  
   - Ne jamais cacher une fonctionnalité uniquement via le frontend  
   - Implémenter un contrôle d’accès robuste (RBAC / authentication checks)  
   - Suivre les recommandations OWASP sur le contrôle d’accès  