# Challenge : Privacy Policy

## Methodology

1. **Exploration de l’interface**
   J’ai navigué dans l’application afin d’identifier les différentes sections accessibles.

2. **Recherche du lien**
   J’ai repéré un lien vers la **Privacy Policy** généralement présent en bas de page (footer).

3. **Accès à la page**
   J’ai cliqué sur ce lien pour accéder à la page de politique de confidentialité.

4. **Validation du challenge**
   L’accès à cette page a permis de valider le challenge.

---

## Vulnerabilities

1. **Information Disclosure**

   * Composant affecté : contenu de la page Privacy Policy
   * Sévérité : **Low**

2. **Security Misconfiguration**

   * Composant affecté : structure de l’application
   * Sévérité : **Low**

3. **Unrestricted Access to Information**

   * Composant affecté : pages publiques
   * Sévérité : **Low**

---

## Risks

1. Divulgation d’informations sur les pratiques internes
2. Possibilité pour un attaquant de mieux comprendre le système
3. Exposition d’informations potentiellement sensibles

---

## Actions

1. **Mitigation strategies**

   * Limiter les informations sensibles dans les pages publiques
   * Vérifier le contenu publié

2. **Remediation fixes**

   * Supprimer ou anonymiser les données sensibles
   * Réviser régulièrement les pages publiques

3. **Best practices**

   * Appliquer le principe du moindre privilège
   * Ne publier que les informations nécessaires
   * Suivre les recommandations OWASP sur la gestion des données publiques
