# Challenge : API Only XSS

## Methodology

1. **Accès aux outils développeur**
   J’ai ouvert les outils de développement du navigateur (F12).

2. **Récupération du token**
   Je me suis rendu dans l’onglet **Storage / Application** afin de récupérer le token JWT de l’utilisateur admin.

3. **Analyse du token**
   Le token contient des informations sensibles comme :

   * email
   * rôle (admin)
   * informations utilisateur

4. **Utilisation du token**
   J’ai utilisé ce token pour effectuer des requêtes authentifiées en tant qu’administrateur.

5. **Injection XSS via API**
   J’ai injecté un payload XSS dans un champ accessible via l’API (ex: feedback, review).

6. **Exécution du script**
   Le script malveillant s’exécute côté client, permettant potentiellement de voler des données comme les cookies ou tokens.

---

## Vulnerabilities

1. **Cross-Site Scripting (XSS)**

   * Composant affecté : API / frontend
   * Sévérité : **High**

2. **Sensitive Data Exposure (JWT Token)**

   * Composant affecté : stockage local (browser storage)
   * Sévérité : **High**

3. **Improper Access Control**

   * Composant affecté : système d’authentification API
   * Sévérité : **Medium**

---

## Risks

1. Vol de session (token JWT / cookies)
2. Accès non autorisé aux comptes administrateurs
3. Exécution de code malveillant dans le navigateur des utilisateurs

---

## Actions

1. **Mitigation strategies**

   * Échapper / filtrer toutes les entrées utilisateur
   * Implémenter une protection contre les XSS (CSP, encoding)

2. **Remediation fixes**

   * Ne pas stocker les tokens sensibles dans le localStorage
   * Utiliser des cookies sécurisés (HttpOnly, Secure)

3. **Best practices**

   * Valider toutes les entrées côté serveur
   * Implémenter une Content Security Policy (CSP)
   * Suivre les recommandations OWASP sur les XSS et la gestion des tokens
