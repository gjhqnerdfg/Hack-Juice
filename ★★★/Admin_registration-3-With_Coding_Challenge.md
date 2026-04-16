# Challenge : Admin Registration

## Methodology

1. **Interception des requêtes**
   J’ai lancé Burp Suite et activé l’interception (Intercept ON).

2. **Création d’un compte**
   J’ai créé un compte utilisateur via l’interface d’inscription, ce qui a généré une requête HTTP vers `/api/Users/`.

3. **Analyse de la requête**
   Dans Burp Suite, je suis allé dans **Proxy → HTTP history** et j’ai repéré la requête `POST /api/Users/`.

4. **Envoi vers Repeater**
   J’ai envoyé cette requête dans Repeater (Ctrl + R) pour pouvoir la modifier.

5. **Modification des paramètres**
   Dans le corps JSON de la requête, j’ai :

   * modifié l’adresse email
   * ajouté le champ `"role": "admin",` juste après `"passwordRepeat"`

6. **Envoi de la requête modifiée**
   J’ai cliqué sur **Send** dans Repeater pour envoyer la requête au serveur.

7. **Résultat**
   Le compte a été créé avec les privilèges administrateur, validant le challenge.

---

## Vulnerabilities

1. **Privilege Escalation (Mass Assignment)**

   * Composant affecté : API `/api/Users/`
   * Sévérité : **Critical**

2. **Lack of Server-Side Validation**

   * Composant affecté : backend (création de compte)
   * Sévérité : **High**

3. **Broken Access Control**

   * Composant affecté : gestion des rôles utilisateurs
   * Sévérité : **Critical**

---

## Risks

1. Création de comptes administrateurs non autorisés
2. Compromission complète de l’application
3. Accès à toutes les données et fonctionnalités sensibles

---

## Actions

1. **Mitigation strategies**

   * Restreindre les champs modifiables côté serveur
   * Vérifier les rôles utilisateur côté backend uniquement

2. **Remediation fixes**

   * Ignorer tout champ `role` envoyé par le client
   * Attribuer les rôles uniquement côté serveur

3. **Best practices**

   * Implémenter une protection contre les attaques de type Mass Assignment
   * Mettre en place un contrôle d’accès strict (RBAC)
   * Suivre les recommandations OWASP sur le contrôle d’accès
