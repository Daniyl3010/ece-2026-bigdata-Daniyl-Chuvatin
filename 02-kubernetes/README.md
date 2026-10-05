
## Lab 2 - ConfigMap & Secret

Réalisé dans le namespace Onyxia (pas de namespace dédié), avec `resources` ajoutées sur chaque pod (quota Onyxia).

- ConfigMap : configuration non sensible (chemins, paramètres). Créée depuis un fichier, des littéraux ou un YAML.
- Secret : données sensibles. Seulement encodées en base64 (pas chiffrées) : `base64 -d` suffit à les lire.
- Injection possible en variables d'environnement (`env`, `envFrom`) ou en fichiers via un volume (`volumeMounts`).
- Les clés utilisées sont les exemples officiels d'AWS, pas de vrais identifiants.
