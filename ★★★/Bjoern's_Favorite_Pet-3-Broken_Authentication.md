# Challenge : Bjoern's Favorite Pet

## Methodology

1. **Reconnaissance (OSINT)**  
   J’ai exploré l’application à la recherche d’informations concernant Bjoern, notamment via les produits, avis et profils utilisateurs.

2. **Recherche d’indices**  
   J’ai utilisé la barre de recherche de l’application pour trouver des éléments liés à "Bjoern".

3. **Analyse des résultats**  
   En consultant les résultats, j’ai trouvé un produit ou un avis associé à Bjoern contenant une information sur son animal préféré.

4. **Validation**  
   L’information récupérée a permis de valider le challenge.

---

## Vulnerabilities

1. **Information Disclosure**  
   - Composant affecté : données produits / avis utilisateurs  
   - Sévérité : **Low**

2. **Excessive Data Exposure**  
   - Composant affecté : API / affichage des données  
   - Sévérité : **Low**

3. **Improper Access Control**  
   - Composant affecté : gestion des informations utilisateurs  
   - Sévérité : **Low**

---

## Risks

1. Divulgation d’informations personnelles des utilisateurs  
2. Exploitation des données pour du social engineering  
3. Atteinte à la vie privée  

---

## Actions

1. **Mitigation strategies**  
   - Limiter les informations exposées publiquement  
   - Filtrer les données sensibles affichées  

2. **Remediation fixes**  
   - Supprimer ou masquer les informations personnelles inutiles  
   - Restreindre l’accès aux données sensibles  

3. **Best practices**  
   - Appliquer le principe du moindre privilège  
   - Ne jamais exposer de données sensibles côté client  
   - Suivre les recommandations OWASP sur la protection des données  