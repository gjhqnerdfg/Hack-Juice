# Challenge : Support Connection

## Methodology
1. **Exploration de l'interface**
   J'ai navigué dans l'application afin d'identifier les sections liées au support et à l'authentification.

2. **Analyse des sources via DevTools**
   Dans l'onglet **Sources** des DevTools, j'ai effectué une recherche (`Ctrl+F`) avec le mot-clé `support`. J'ai découvert une expression régulière exposée dans le code source : /(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@!!%*?&])[A-Za-z\d@!!%*?&]{12,30}/

3. **Déduction du mot de passe**
   En analysant la logique de la regex (majuscule, minuscule, chiffre, caractère spécial, 12-30 caractères) et le contexte de l'application, j'ai déduit le mot de passe :
   `Support2022!`

4. **Accès à la base de données**
   J'ai ouvert le fichier `incident-support.kdbx` (base de données KeePass) avec le mot de passe déduit, ce qui a permis d'extraire les identifiants stockés.

5. **Récupération des credentials**
   Les identifiants récupérés ont permis de valider le challenge.

---

## Vulnerabilities

1. **Exposure of Sensitive Logic in Client-Side Code**
   - Composant affecté : code source JavaScript (DevTools > Sources)
   - Sévérité : **High**

2. **Weak / Predictable Password**
   - Composant affecté : compte support
   - Sévérité : **High**

3. **Sensitive File Exposure**
   - Composant affecté : fichier `incident-support.kdbx`
   - Sévérité : **Critical**

4. **Information Disclosure**
   - Composant affecté : expressions régulières et logique de validation exposées côté client
   - Sévérité : **Medium**

---

## Risks

1. Exposition de la logique de validation des mots de passe dans le code client
2. Possibilité de déduire ou brute-forcer un mot de passe à partir des règles exposées
3. Accès non autorisé à des identifiants critiques via la base de données KeePass
4. Compromission complète du compte support et des systèmes associés

---

## Actions

1. **Mitigation strategies**
   - Ne jamais exposer de logique de validation sensible côté client
   - Déplacer les contrôles de sécurité côté serveur
   - Utiliser des mots de passe générés aléatoirement et non prévisibles

2. **Remediation fixes**
   - Supprimer ou obfusquer les expressions régulières sensibles du code source
   - Changer immédiatement les identifiants compromis
   - Chiffrer et sécuriser l'accès aux fichiers `.kdbx`
   - Mettre en place une authentification multi-facteurs (MFA) sur le compte support

3. **Best practices**
   - Appliquer le principe du moindre privilège sur les comptes support
   - Ne jamais stocker de logique de sécurité dans le code JavaScript côté client
   - Suivre les recommandations OWASP A02:2021 (Cryptographic Failures) et A05:2021 (Security Misconfiguration)
   - Auditer régulièrement les fichiers sensibles accessibles dans l'application