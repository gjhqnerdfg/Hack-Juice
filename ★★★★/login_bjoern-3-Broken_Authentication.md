# Challenge : Login Bjoern

## Methodology

1. **Analyse de l’indice**  
   J’ai identifié que le challenge nécessitait une transformation particulière de l’email de Bjoern.

2. **Utilisation de la console JavaScript**  
   J’ai utilisé la console du navigateur pour exécuter du code JavaScript.

3. **Transformation de l’email**  
   J’ai utilisé la commande suivante pour inverser l’email puis l’encoder en Base64 :  window.btoa("bjoern.kimminich@gmail.com".split("").reverse().join(""))

4. **Récupération du résultat**  
Le résultat obtenu correspond à la valeur attendue pour contourner le système d’authentification.

5. **Authentification**  
J’ai utilisé cette valeur pour me connecter en tant que Bjoern.

---

## Vulnerabilities

1. **Weak Encoding Mechanism (Base64 Misuse)**  
- Composant affecté : système d’authentification  
- Sévérité : **Medium**

2. **Improper Authentication Logic**  
- Composant affecté : login  
- Sévérité : **High**

3. **Information Disclosure (Predictable Transformation)**  
- Composant affecté : logique de transformation des identifiants  
- Sévérité : **Medium**

---

## Risks

1. Contournement de l’authentification  
2. Accès non autorisé aux comptes utilisateurs  
3. Exploitation facile si la logique est découverte  

---

## Actions

1. **Mitigation strategies**  
- Ne jamais utiliser Base64 comme mécanisme de sécurité  
- Implémenter une authentification robuste avec mots de passe sécurisés  

2. **Remediation fixes**  
- Supprimer toute logique d’authentification basée sur des transformations prévisibles  
- Utiliser un système de hash sécurisé (bcrypt, argon2)  

3. **Best practices**  
- Ne jamais stocker ou transmettre des données sensibles sans chiffrement  
- Implémenter une authentification standardisée et sécurisée  
- Suivre les recommandations OWASP sur l’authentification  