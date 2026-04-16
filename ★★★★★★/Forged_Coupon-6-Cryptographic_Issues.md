# Challenge : Forged Coupon

## Methodology

1. **Exploration initiale**  
   J’ai commencé par explorer les fichiers accessibles dans `/ftp/` et j’ai trouvé :  /ftp/coupons_2013.md.bak%2500.md
   contenant des informations sur d’anciens coupons.

2. **Test des coupons existants**  
J’ai essayé plusieurs coupons trouvés dans ce fichier, mais ils ne permettaient pas d’atteindre une réduction de 80%.

3. **Recherche de nouveaux indices**  
En observant l’interface, j’ai trouvé une source externe proposant des coupons valides, notamment :  k#pDmhz3:t
qui donnait une réduction de 40%.

4. **Analyse du format du coupon**  
J’ai cherché à identifier le type d’encodage utilisé pour ce coupon à l’aide d’outils comme **dcode.fr**.

5. **Identification de l’encodage**  
L’analyse a révélé que le coupon était encodé en **Z85**.

6. **Décodage du coupon**  
Après décodage, j’ai obtenu :  APR26-40


7. **Modification du contenu**  
J’ai modifié la valeur de réduction :  APR26-80

9. **Utilisation du coupon forgé**  
J’ai entré ce coupon dans l’application, ce qui a permis d’obtenir une réduction de 80% et valider le challenge.

---

## Vulnerabilities

1. **Business Logic Flaw (Coupon Manipulation)**  
- Composant affecté : système de coupons  
- Sévérité : **Critical**

2. **Weak Encoding Mechanism (Z85 without integrity check)**  
- Composant affecté : génération des coupons  
- Sévérité : **High**

3. **Lack of Server-Side Validation**  
- Composant affecté : validation des coupons  
- Sévérité : **High**

---

## Risks

1. Fraude financière via génération de coupons arbitraires  
2. Perte importante de revenus pour l’entreprise  
3. Exploitation automatisée du système de réduction  

---

## 🛠️ Actions

1. **Mitigation strategies**  
- Vérifier les coupons côté serveur avec une signature sécurisée  
- Ne jamais faire confiance aux données encodées côté client  

2. **Remediation fixes**  
- Utiliser des coupons signés (HMAC, JWT)  
- Stocker les coupons côté serveur au lieu de les encoder côté client  

3. **Best practices**  
- Ne jamais utiliser un simple encodage comme mécanisme de sécurité  
- Implémenter des contrôles d’intégrité (signature, hash)  
- Suivre les recommandations OWASP sur la logique métier  

8. **Ré-encodage du coupon**  
J’ai ensuite ré-encodé cette nouvelle valeur en Z85, ce qui a donné :  k#pDmhz3)x


9. **Utilisation du coupon forgé**  
J’ai entré ce coupon dans l’application, ce qui a permis d’obtenir une réduction de 80% et valider le challenge.

---

## Vulnerabilities

1. **Business Logic Flaw (Coupon Manipulation)**  
- Composant affecté : système de coupons  
- Sévérité : **Critical**

2. **Weak Encoding Mechanism (Z85 without integrity check)**  
- Composant affecté : génération des coupons  
- Sévérité : **High**

3. **Lack of Server-Side Validation**  
- Composant affecté : validation des coupons  
- Sévérité : **High**

---

## Risks

1. Fraude financière via génération de coupons arbitraires  
2. Perte importante de revenus pour l’entreprise  
3. Exploitation automatisée du système de réduction  

---

## Actions

1. **Mitigation strategies**  
- Vérifier les coupons côté serveur avec une signature sécurisée  
- Ne jamais faire confiance aux données encodées côté client  

2. **Remediation fixes**  
- Utiliser des coupons signés (HMAC, JWT)  
- Stocker les coupons côté serveur au lieu de les encoder côté client  

3. **Best practices**  
- Ne jamais utiliser un simple encodage comme mécanisme de sécurité  
- Implémenter des contrôles d’intégrité (signature, hash)  
- Suivre les recommandations OWASP sur la logique métier  