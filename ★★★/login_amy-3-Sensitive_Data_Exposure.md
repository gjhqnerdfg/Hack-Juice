# Challenge : Login Amy

## Methodology

1. **Recherche du mot de passe**  
   J’ai commencé par copier la phrase :  93.83 billion trillion trillion centuries
   qui est un indice donné dans le challenge.

2. **Consultation du site Haystack**  
Je me suis rendu sur le site :  https://www.grc.com/haystack.htm?id
pour analyser le mot de passe via la méthode de recherche de clés.

3. **Analyse des indices**  
Parmi les indices, un fait référence à **Futurama** : le petit ami de l’héroïne Amy s’appelle **Kif**.

4. **Construction du mot de passe**  
- On prend le prénom **Kif**  
- On combine avec l’autre indice fourni (`D0g.....................`)  
- On obtient finalement le mot de passe complet :  K1f.....................

5. **Authentification**  
Je me suis connecté sur l’application avec l’email Amy et ce mot de passe calculé.

---

## Vulnerabilities

1. **Weak Password Discovery / Predictable Password**  
- Composant affecté : système d’authentification  
- Sévérité : **Medium**

2. **Information Disclosure (via clues)**  
- Composant affecté : indices dans le challenge / site externe  
- Sévérité : **Low**

3. **Brute Force / Guessable Password**  
- Composant affecté : login Amy  
- Sévérité : **Medium**

---

## Risks

1. Compte utilisateur compromis si les indices sont accessibles publiquement  
2. Perte de confidentialité des informations personnelles  
3. Possibilité pour un attaquant d’utiliser la même méthode pour d’autres comptes  

---

## ActK1f.....................ions

1. **Mitigation strategies**  
- Interdire l’utilisation de mots de passe faibles ou basés sur des indices connus  
- Encourager les utilisateurs à créer des mots de passe forts et uniques  

2. **Remediation fixes**  
- Imposer des mots de passe complexes (longueur minimale + majuscules + chiffres + symboles)  
- Ne jamais divulguer d’indices permettant de reconstruire le mot de passe  

3. **Best practices**  
- Utiliser un gestionnaire de mots de passe sécurisé  
- Implémenter une vérification de la force du mot de passe côté serveur  
- Suivre les recommandations OWASP sur la gestion des mots de passe.