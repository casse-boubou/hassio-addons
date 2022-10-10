# What’s changed

## Suppressions de fonctions

- Suppression du fichier apparmor.txt pour supprimer la restriction des droits
de l'utilisateur java qui empechait d'utiliser une database locale
- Suppression de la création de l'utilisateur java qui était restraint
et empechait d'utiliser une database locale
- Suppression de la commande s6-setuidgid qui executait le programme avec les
droits de l'utilisateur java qui empechait d'utiliser une database locale

## Ajout de fonctions

- Ajout de l'accès en lecture/ecriture du dossier "Share" pour l'add-on
- Ajout de la possibilitée d'enregistrer la database en locale plutot que
dans la database Maria db
- Ajout de la possibilitée de copier une database de maria db à locale et vice versa
- Ajout de plusieurs fonctions supplémentaires dans la configuration de l'add-on
  - utiliser une database Maria db ou locale par défaut
  - utiliser une database Maria db
  - utiliser une database locale
  - choisir un repertoir de stockage de la database locale
  - copier la database
  - source de la copie de la database
  - destination de la copie de la database