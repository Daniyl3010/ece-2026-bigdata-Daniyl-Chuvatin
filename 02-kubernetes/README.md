
## Lab 2 - ConfigMap & Secret

Réalisé dans le namespace Onyxia (pas de namespace dédié), avec `resources` ajoutées sur chaque pod (quota Onyxia).

- ConfigMap : configuration non sensible (chemins, paramètres). Créée depuis un fichier, des littéraux ou un YAML.
- Secret : données sensibles. Seulement encodées en base64 (pas chiffrées) : `base64 -d` suffit à les lire.
- Injection possible en variables d'environnement (`env`, `envFrom`) ou en fichiers via un volume (`volumeMounts`).
- Les clés utilisées sont les exemples officiels d'AWS, pas de vrais identifiants.

## Lab 3 - Job & CronJob

Réalisé dans le namespace Onyxia, avec `resources` ajoutées (quota Onyxia). Les commandes `-w` ont été remplacées
par `kubectl wait` / `sleep` pour garder un log lisible.

- Job : exécute une tâche jusqu'à sa fin. `backoffLimit` fixe le nombre de nouvelles tentatives en cas d'échec,
  `activeDeadlineSeconds` la durée maximale.
- `parallelism` / `completions` : plusieurs pods exécutent la tâche en parallèle (4 pods simultanés observés).
- CronJob : crée un Job selon une expression cron (`*/2 * * * *` = toutes les 2 minutes).
  `concurrencyPolicy: Forbid` empêche deux exécutions simultanées, `suspend` met en pause la planification.
