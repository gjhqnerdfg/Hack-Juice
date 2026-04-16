# Challenge : Manipulate Basket

## Methodology

1. **Ajout d’un produit au panier**  
   J’ai ajouté un produit au panier depuis la boutique.

2. **Accès au panier**  
   Je me suis rendu sur la page du panier pour visualiser les produits sélectionnés.

3. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON).

4. **Modification des paramètres**  
   J’ai modifié les données envoyées au serveur (ex: `quantity`, `productId` ou autres paramètres du panier) afin de manipuler le contenu du panier.

5. **Envoi de la requête modifiée**  
   J’ai utilisé **Forward** pour envoyer la requête modifiée au serveur.

6. **Observation du résultat**  
   Le serveur a accepté les modifications, permettant de changer le contenu ou les valeurs du panier de manière non autorisée.

---

## Vulnerabilities

1. **Parameter Tampering**  
   - Composant affecté : système de gestion du panier  
   - Sévérité : **High**

2. **Lack of Server-Side Validation**  
   - Composant affecté : backend (API panier)  
   - Sévérité : **High**

3. **Broken Access Control**  
   - Composant affecté : logique métier du panier  
   - Sévérité : **Medium**

---

## Risks

1. Modification frauduleuse des prix ou quantités  
2. Perte financière pour l’entreprise  
3. Exploitation du système de commande  

---

## Actions

1. **Mitigation strategies**  
   - Valider toutes les données côté serveur  
   - Vérifier la cohérence des valeurs (quantité, prix, produit)  

2. **Remediation fixes**  
   - Ne jamais faire confiance aux données du client  
   - Calculer les prix uniquement côté serveur  

3. **Best practices**  
   - Implémenter des contrôles d’intégrité sur les requêtes  
   - Utiliser des identifiants sécurisés pour les produits  
   - Suivre les recommandations OWASP sur le contrôle d’accès et la validation des entrées.