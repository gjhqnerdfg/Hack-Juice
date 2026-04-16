# Challenge : Access Log

## Methodology

1. **Accès à la fonctionnalité**  
   Je me suis rendu sur la section de l’application qui enregistre les logs d’accès, ou sur une page où les logs sont visibles.

2. **Observation des requêtes**  
   J’ai utilisé les outils de développement du navigateur et/ou **Burp Suite** pour surveiller les requêtes HTTP envoyées lors de la navigation.

3. **Injection de données**  
   J’ai ajouté des entrées spéciales dans les champs accessibles (ex: formulaire de recherche, login, URL) pour voir si elles apparaissaient dans les logs.

4. **Analyse des logs**  
   J’ai consulté les logs enregistrés et identifié la présence de mes entrées injectées, ce qui montre qu’aucune validation ou filtrage n’était effectué.

5. **Exploitation**  
   Les informations récupérées dans les logs peuvent être utilisées pour détecter des vulnérabilités ou obtenir des informations sur le système et les utilisateurs.

---

## Vulnerabilities

1. **Information Disclosure**  
   - Composant affecté : système de logging / backend  
   - Sévérité : **Medium**

2. **Lack of Input Validation**  
   - Composant affecté : formulaires / journaux d’accès  
   - Sévérité : **Medium**

3. **Security Misconfiguration**  
   - Composant affecté : gestion des logs  
   - Sévérité : **Medium**

---

## Risks

1. Fuite d’informations sensibles sur les utilisateurs ou le système  
2. Possibilité d’exploiter les logs pour des attaques futures (ex: XSS dans les logs)  
3. Risque de divulgation d’informations critiques à des personnes non autorisées  

---

## Actions

1. **Mitigation strategies**  
   - Valider et encoder toutes les entrées utilisateurs avant de les enregistrer dans les logs  
   - Restreindre l’accès aux logs aux utilisateurs autorisés seulement  

2. **Remediation fixes**  
   - Filtrer les caractères spéciaux et scripts dans les logs  
   - Implémenter un contrôle d’accès strict sur les pages de logs  

3. **Best practices**  
   - Ne jamais exposer les logs côté client  
   - Suivre les recommandations OWASP sur la gestion sécurisée des journaux  
   - Mettre en place un monitoring des anomalies dans les logs  