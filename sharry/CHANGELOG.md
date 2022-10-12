# What’s changed

- Convertion du mode d'édition de tous les fichiers de CRLF à LF
- 'DefaultStore' défini maintenant automatiquement la database par défaut (plus besoin de la sélectionner manuellement en plus de DefaultStore)
- Améliorations des messages d'erreurs
- Amélioration du mode 'copy_db' qui vérifie maintenant si les base de données source et target ne sont pas identique
- Amélioration du mode 'copy_db' qui active automatiquement la base de donnée (mariadb ou locale) de destination qui n'est pas définie par DefaultStore

## Suppressions

- Suppression des options 'use_maria_db' et 'use_local_db' puisque la database est maintenant automatiquement définie par DefaultStore
