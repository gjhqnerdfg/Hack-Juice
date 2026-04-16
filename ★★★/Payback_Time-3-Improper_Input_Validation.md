# Challenge : Payback Time

## Methodology

1. **Accès au produit ou à la fonctionnalité**  
   Je me suis rendu sur un produit dans le shop et sur l’option de paiement correspondante.

2. **Ajout au panier**  
   J’ai ajouté le produit au panier pour préparer le paiement.

3. **Interception de la requête**  
   J’ai lancé **Burp Suite** et activé l’interception (Intercept ON) pour capturer la requête de paiement.

4. **Modification des paramètres**  
   J’ai modifié les champs liés au prix ou à l’ordre (ex: `amount`, `discount`, `productId`) afin de réduire le montant à payer ou obtenir le produit gratuitement.

5. **Envoi de la requête modifiée**  
   J’ai utilisé **Forward** pour envoyer la requête manipulée au serveur et observer si le paiement était accepté.

6. **Validation du résultat**  
   Le serveur a accepté les modifications, permettant d’obtenir un produit sans payer correctement.

---

## Vulnerabilities

1. **Parameter Tampering / Business Logic Flaw**  
   - Composant affecté : système de paiement / panier  
   - Sévérité : **Critical**

2. **Lack of Server-Side Validation**  
   - Composant affecté : API de paiement  
   - Sévérité : **High**

3. **Broken Access Control**  
   - Composant affecté : backend de transaction  
   - Sévérité : **High**

---

## Risks

1. Fraude et perte financière pour l’entreprise  
2. Possibilité d’achat gratuit de produits  
3. Exploitation répétée pouvant affecter le chiffre d’affaires  

---

## Actions

1. **Mitigation strategies**  
   - Valider toutes les transactions côté serveur  
   - Vérifier l’intégrité des montants et produits avant de confirmer le paiement  

2. **Remediation fixes**  
   - Calculer les prix et remises uniquement côté serveur  
   - Interdire toute modification des paramètres côté client  

3. **Best practices**  
   - Implémenter des contrôles anti-fraude et logs de transactions  
   - Suivre les recommandations OWASP sur la logique métier et la validation des entrées  