# Challenge : Product Tampering (Advanced)

## Methodology

1. **Interception du trafic**
   J’ai lancé Burp Suite et activé l’interception (Intercept ON).

2. **Recherche d’une requête cible**
   J’ai identifié une requête GET vers :

   ```
   /rest/product/1/reviews
   ```

3. **Modification de la requête**
   J’ai envoyé cette requête dans Repeater puis modifié la première ligne pour créer une requête API :

   ```
   PUT /api/products/9 HTTP/2
   ```

4. **Analyse de la réponse**
   Après envoi, j’ai récupéré la réponse contenant les informations du produit, notamment un champ `description`.

5. **Identification du point d’injection**
   Dans le champ `description`, j’ai remarqué la présence de HTML (`href`), indiquant une possible injection.

6. **Injection du payload**
   J’ai remplacé la description par le contenu suivant :

   ```json
   {"description":"<a href=\"https://owasp.slack.com\" target=\"_blank\">More...</a>"}
   ```

7. **Envoi de la requête modifiée**
   J’ai envoyé la requête avec **Send** dans Burp Suite.

8. **Résultat**
   Le contenu HTML a été accepté et injecté dans l’application, validant le challenge.

---

## Vulnerabilities

1. **Stored XSS (Cross-Site Scripting)**

   * Composant affecté : description produit
   * Sévérité : **High**

2. **Improper Input Validation**

   * Composant affecté : API `/api/products/`
   * Sévérité : **High**

3. **Broken Access Control**

   * Composant affecté : modification des produits
   * Sévérité : **Critical**

---

## Risks

1. Injection de scripts malveillants visibles par tous les utilisateurs
2. Vol de sessions ou de données sensibles
3. Modification non autorisée du contenu de l’application

---

## Actions

1. **Mitigation strategies**

   * Échapper et filtrer tout contenu HTML injecté
   * Restreindre les permissions de modification des produits

2. **Remediation fixes**

   * Implémenter une validation stricte côté serveur
   * Bloquer les balises HTML non autorisées

3. **Best practices**

   * Utiliser un système de sanitation (ex: DOMPurify)
   * Implémenter un contrôle d’accès strict (RBAC)
   * Suivre les recommandations OWASP sur les XSS
