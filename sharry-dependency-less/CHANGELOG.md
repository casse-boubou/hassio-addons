# What’s changed

- Sharry et MariaDB ont maintenant des dossier séparer dans rootfs. Ainsi Sharry attend maintenant que MariaDB soit complètement initialisé avant de se lancer au lieu d'avoir le même fichier RUN pour les deux programmes qui les exécutes l'un après l'autre.