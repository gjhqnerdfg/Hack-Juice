# Challenge : Product Tampering

## Methodology

1. **Accès à la page produit**  
   Je me suis rendu sur la page d’un produit dans le shop.

2. **Ajout au panier**  
   J’ai ajouté le produit au panier pour préparer la manipulation.

3. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON) pour capturer la requête envoyée lors de l’ajout du produit au panier.

4. **Modification des paramètres**  
   J’ai modifié les champs liés au produit, tels que `price`, `productId` ou `quantity`, afin de manipuler le prix ou la référence du produit.

5. **Envoi de la requête modifiée**  
   J’ai utilisé **Forward** pour envoyer la requête modifiée au serveur.

6. **Observation du résultat**  
   Le serveur a accepté les modifications, permettant de changer le prix ou le produit de manière non autorisée.

---

## Vulnerabilities

1. **Parameter Tampering / Business Logic Flaw**  
   - Composant affecté : panier / backend produit  
   - Sévérité : **High**

2. **Lack of Server-Side Validation**  
   - Composant affecté : API de gestion des produits  
   - Sévérité : **High**

3. **Broken Access Control**  
   - Composant affecté : logique métier / panier  
   - Sévérité : **Medium**

---

## Risks

1. Manipulation frauduleuse du prix ou des produits  
2. Perte financière pour l’entreprise  
3. Exploitation répétée pouvant impacter le chiffre d’affaires et la réputation  

---

## Actions

1. **Mitigation strategies**  
   - Valider toutes les modifications de produits côté serveur  
   - Vérifier la cohérence des prix, quantités et références avant d’accepter une requête  

2. **Remediation fixes**  
   - Supprimer toute possibilité de modification des champs sensibles côté client  
   - Calculer les prix uniquement côté serveur  

3. **Best practices**  
   - Implémenter des contrôles d’intégrité et des logs pour les opérations critiques  
   - Suivre les recommandations OWASP sur la logique métier et la validation côté serveur  