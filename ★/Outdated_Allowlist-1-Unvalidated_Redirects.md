# Challenge : Outdated Allowlist

## Methodology

1. **Analyse du frontend**
   J’ai ouvert les outils de développement du navigateur (Inspecter / F12).

2. **Exploration du code JavaScript**
   Je me suis rendu dans l’onglet **Debugger** puis dans le fichier `main.js`.

3. **Recherche d’indices**
   J’ai utilisé la fonction de recherche pour trouver le mot-clé **"blockchain"** dans le code.

4. **Identification du lien**
   J’ai trouvé une URL présente dans une allowlist (liste blanche) du code.

5. **Accès au lien**
   J’ai copié et ouvert le lien suivant :

   ```
   https://www.blockchain.com/explorer/addresses/btc/1AbKfgvw9psQ41NbLi8kufDQTezwG8DRZm
   ```

6. **Validation du challenge**
   L’accès à ce lien a permis de valider le challenge.

---

## Vulnerabilities

1. **Outdated Allowlist**

   * Composant affecté : frontend (main.js)
   * Sévérité : **Low**

2. **Information Disclosure**

   * Composant affecté : code JavaScript client
   * Sévérité : **Low**

3. **Security Misconfiguration**

   * Composant affecté : gestion des URLs autorisées
   * Sévérité : **Low**

---

## Risks

1. Divulgation d’informations internes via le code source
2. Accès à des ressources non prévues
3. Possibilité d’exploitation si d’autres liens sensibles sont exposés

---

## Actions

1. **Mitigation strategies**

   * Éviter d’exposer des URLs sensibles dans le code frontend
   * Mettre à jour régulièrement les allowlists

2. **Remediation fixes**

   * Supprimer les liens inutiles ou obsolètes
   * Gérer les allowlists côté serveur uniquement

3. **Best practices**

   * Ne jamais stocker d’informations sensibles dans le code client
   * Appliquer le principe du moindre privilège
   * Suivre les recommandations OWASP sur la gestion des configurations
