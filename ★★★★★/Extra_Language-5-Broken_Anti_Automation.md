# Challenge : Extra Language

## Methodology
1. **Exploration de l'interface**
   J'ai navigué dans l'application afin d'identifier les options de changement de langue.

2. **Interception des paquets réseau**
   En changeant de langue depuis l'interface, j'ai observé dans les DevTools (onglet **Network**) les requêtes effectuées pour récupérer les fichiers de traduction. J'ai identifié le format et l'endpoint utilisé pour charger les paquets de langue (fichiers JSON).

3. **Découverte de la langue cachée**
   En analysant les requêtes et la structure des fichiers de langue, j'ai identifié un code de langue non référencé dans l'interface : tlh_AA

4. **Récupération du paquet JSON**
   J'ai directement requêté l'endpoint de langue avec le code `tlh_AA` afin de récupérer le fichier de traduction associé.

5. **Validation du challenge**
   L'accès au paquet JSON de la langue Klingon a permis de valider le challenge.

---

## Vulnerabilities

1. **Hidden Endpoint Exposure**
   - Composant affecté : API de chargement des fichiers de langue
   - Sévérité : **Medium**

2. **Insecure Direct Object Reference (IDOR)**
   - Composant affecté : endpoint de récupération des paquets de langue
   - Sévérité : **Medium**

3. **Information Disclosure**
   - Composant affecté : ressources non référencées accessibles publiquement
   - Sévérité : **Low**

---

## Risks

1. Accès à des ressources cachées non destinées aux utilisateurs finaux
2. Possibilité d'énumérer d'autres endpoints ou ressources non documentées
3. Exposition de contenu ou de données non prévues pour la production

---

## Actions

1. **Mitigation strategies**
   - Restreindre l'accès aux ressources non publiées via des contrôles d'accès côté serveur
   - Ne pas laisser de ressources de test ou cachées accessibles en production

2. **Remediation fixes**
   - Supprimer ou désactiver les paquets de langue non utilisés en production
   - Mettre en place une liste blanche des codes de langue acceptés
   - Retourner une erreur 404 pour tout code de langue non autorisé

3. **Best practices**
   - Auditer régulièrement les endpoints accessibles publiquement
   - Appliquer le principe du moindre privilège sur les ressources statiques
   - Suivre les recommandations OWASP A01:2021 (Broken Access Control)