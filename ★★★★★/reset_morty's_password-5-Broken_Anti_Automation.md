# Challenge : Reset Morty's Password

## Methodology

1. **Recherche d’informations (OSINT)**  
   J’ai trouvé l’adresse email de Morty en consultant une review présente dans l’application.

2. **Accès à la fonctionnalité de reset**  
   Je me suis rendu sur la page **Forgot Password** et j’ai saisi l’email de Morty.

3. **Récupération de la question de sécurité**  
   J’ai obtenu la question suivante : What is your favorite pet?

4. **Recherche de la réponse**  
J’ai effectué des recherches sur Morty et trouvé une réponse possible : **Snuffles**, qui s’est révélée incorrecte.

5. **Génération de variantes (brute force intelligent)**  
J’ai développé un script Python pour générer plusieurs variantes du mot **Snuffles** en utilisant la méthode **leet speak** (remplacement de lettres par des chiffres/symboles).

6. **Préparation de l’attaque avec Burp Suite**  
J’ai utilisé **Burp Suite** et envoyé la requête dans le module **Repeater / Intruder**.

7. **Configuration de l’attaque**  
- Mode : **Sniper**  
- Ajout d’une variable sur la réponse à la question de sécurité  
- Import de la liste générée dans l’onglet **Payloads**

8. **Exécution de l’attaque**  
J’ai lancé l’attaque en testant toutes les variantes générées.

9. **Gestion du rate limiting**  
J’ai remarqué un timeout après environ 100 requêtes, j’ai donc divisé ma liste en plusieurs parties et relancé plusieurs attaques.

10. **Exploitation réussie**  
Une des variantes générées 5N0wb41L a permis de répondre correctement à la question et de réinitialiser le mot de passe.

---

## Vulnerabilities

1. **Weak Security Question / Predictable Answer**  
- Composant affecté : système de récupération de mot de passe  
- Sévérité : **High**

2. **Brute Force Vulnerability (No Proper Rate Limiting)**  
- Composant affecté : endpoint de reset  
- Sévérité : **High**

3. **Information Disclosure (OSINT)**  
- Composant affecté : reviews / données publiques  
- Sévérité : **Medium**

---

## Risks

1. Compromission de comptes via des questions de sécurité faibles  
2. Attaques automatisées permettant de deviner les réponses  
3. Accès non autorisé aux données utilisateurs  

---

## Actions

1. **Mitigation strategies**  
- Supprimer les questions de sécurité ou utiliser des méthodes plus sécurisées  
- Implémenter un rate limiting strict et des protections anti-brute force  

2. **Remediation fixes**  
- Utiliser des tokens uniques pour le reset de mot de passe  
- Bloquer temporairement les comptes après plusieurs tentatives échouées  

3. **Best practices**  
- Éviter les questions de sécurité basées sur des informations publiques  
- Implémenter une authentification multifactorielle (MFA)  
- Suivre les recommandations OWASP sur la gestion des identités et authentification  