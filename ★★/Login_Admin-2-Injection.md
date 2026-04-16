# Challenge : Login Admin

## Methodology

1. **Interception des requêtes**
   J’ai lancé Burp Suite et activé l’interception (Intercept ON).

2. **Tentative de connexion**
   J’ai essayé de me connecter avec :

   * Email : `admin`
   * Mot de passe : `admin`

3. **Capture de la requête**
   J’ai cliqué sur **Log in** afin d’intercepter la requête HTTP.

4. **Analyse de la requête**
   Dans Burp Suite, j’ai identifié la requête `POST` contenant les informations de connexion et suis allé dans l’onglet **RAW**.

5. **Injection SQL**
   J’ai modifié le champ email en ajoutant le payload suivant :

   ```
   ' OR 1=1 --
   ```

6. **Envoi de la requête modifiée**
   J’ai cliqué sur **Forward** pour envoyer la requête modifiée, puis désactivé l’interception (Intercept OFF).

7. **Résultat**
   L’authentification a été bypassée, me permettant d’accéder au compte administrateur.

---

## Vulnerabilities

1. **SQL Injection (Authentication Bypass)**

   * Composant affecté : système d’authentification
   * Sévérité : **Critical**

2. **Improper Input Validation**

   * Composant affecté : formulaire de login
   * Sévérité : **High**

3. **Broken Authentication**

   * Composant affecté : mécanisme de connexion
   * Sévérité : **High**

---

## Risks

1. Accès non autorisé au compte administrateur
2. Compromission complète de l’application
3. Accès à toutes les données sensibles

---

## Actions

1. **Mitigation strategies**

   * Utiliser des requêtes préparées (prepared statements)
   * Valider et filtrer toutes les entrées utilisateur

2. **Remediation fixes**

   * Corriger les requêtes SQL vulnérables
   * Implémenter un ORM sécurisé

3. **Best practices**

   * Ne jamais concaténer directement les entrées utilisateur dans les requêtes SQL
   * Mettre en place des protections contre les injections SQL
   * Suivre les recommandations OWASP sur les injections
