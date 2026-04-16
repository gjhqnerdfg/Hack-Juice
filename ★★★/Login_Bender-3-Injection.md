# Challenge : Login Bender

## Methodology

1. **Accès au formulaire de connexion**  
   Je me suis rendu sur la page de login de l’application.

2. **Test d’injection SQL**  
   J’ai tenté une injection SQL dans le champ email afin de contourner l’authentification.

3. **Payload utilisé**  
   J’ai saisi le payload suivant dans le champ email :  Bender@juice-sh.op'--

4. **Saisie d’un mot de passe aléatoire**  
J’ai entré un mot de passe quelconque, car l’injection SQL permet d’ignorer cette vérification.

5. **Validation du formulaire**  
Après soumission, l’authentification a été bypassée et j’ai été connecté en tant que Bender.

---

## Vulnerabilities

1. **SQL Injection (Authentication Bypass)**  
- Composant affecté : système d’authentification / base de données  
- Sévérité : **Critical**

2. **Improper Input Validation**  
- Composant affecté : formulaire de login  
- Sévérité : **High**

3. **Broken Authentication**  
- Composant affecté : mécanisme de connexion  
- Sévérité : **High**

---

## Risks

1. Accès non autorisé à des comptes utilisateurs  
2. Compromission de données sensibles  
3. Prise de contrôle complète de comptes  

---

## Actions

1. **Mitigation strategies**  
- Utiliser des requêtes préparées (prepared statements)  
- Filtrer et valider toutes les entrées utilisateur  

2. **Remediation fixes**  
- Corriger les requêtes SQL vulnérables  
- Implémenter un ORM sécurisé  

3. **Best practices**  
- Ne jamais concaténer directement les entrées utilisateur dans les requêtes SQL  
- Mettre en place une protection contre les injections  
- Suivre les recommandations OWASP sur les injections  