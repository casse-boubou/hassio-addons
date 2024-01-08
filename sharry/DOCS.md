# Home Assistant Add-on: Sharry

## Install

D'habord ajoutez le repertoire à l'add-on store de HomeAssistant (`https://github.com/erdnaxela02/hassio-addons`):

[![Open your Home Assistant instance and show the add add-on repository dialog
with a specific repository URL pre-filled.][add-repo-shield]][add-repo]

Ensuite recherchez Sharry dans le store et cliquez sur installer:

[![Open your Home Assistant instance and show the dashboard of a Supervisor add-on.][add-addon-shield]][add-addon]

## Access & Login

[Sharry][sharry] est configuré pour s'authentifier auprès de Home Assistant par
défaut. Cela signifie que tout utilisateur HA peut ouvrir l'interface
utilisateur et se connecter avec ses informations d'identification HA.
Chaque utilisateur HA aura son propre compte dans Sharry et ses propres partages.

L'add-on est configuré pour que toutes les autres méthodes de connexion et
d'enregistrement de nouveaux utilisateurs par défaut soient désactivées.
Si vous souhaitez autoriser les utilisateurs à avoir des comptes uniquement
avec Sharry, vous pouvez activer l'enregistrement d'utilisateurs et d'autres
méthodes de connexion à l'aide de l'option `conf_overrides` illustrée ci-dessous.
Vous devrez configurer l'une des autres méthodes de connexion
sous `sharry.restserver.backend.auth` et définir
`sharry.restserver.backend.ignup.mode` sur `open` ou `invite`.
Pour plus d'information vous pouvez consulter [Sharry coniguration][sharry-docs-configure].

## Database Setup

[Sharry][sharry] nécessite une base de données Postgres ou MariaDB pour
stocker ses données. Par défaut, il stockera ses données dans
l'[addon MariaDB][addon-mariadb]. Cet add-on doit être installé et en cours
d'exécution avant le démarrage. Vous n'avez besoin d'aucune configuration
supplémentaire pour cela, tant que l'add-on MariaDB est en cours d'execution,
Sharry pourra l'utiliser.

[![Open your Home Assistant instance and show the dashboard of a Supervisor add-on.][add-addon-shield]][add-addon-mariadb]

Si vous le préférez, vous pouvez utiliser une base de données distante en
remplissant toutes les options `remote_db_*` ci-dessous. Vous devrez créer
la base de données et l'opérateur pour Sharry à l'avance et Sharry aura
besoin d'un accès complet en lecture/écriture sur la base de données
spécifiée afin de pouvoir configurer le schéma et gérer les données.

Veuillez noter qu'il n'y a pas de chemin de mise à niveau facile entreces deux options.

## ⚠ Backing up Sharry

Étant donné que Sharry ne stocke pas ses propres données, les snapshots de ce
module complémentaire n'incluront que sa configuration. Vous devrez sauvegarder
séparément les données afin de pouvoir les restaurer.

Si vous utilisez le module complémentaire MariaDB, assurez-vous d'inclure
également ce module complémentaire dans votre snapshots.

Si vous utilisez une base de données différente, vous devrez configurer
votre propre processus de sauvegarde.

Et si vous utiliser un stockage des données locale, vous devrez pensé à
sauvegarder le dossier local

## Configuration

Example add-on configuration:

```yaml
domain: homeassistant.local
use_ssl: false
default_language: us
share_max_size_gb: 1.5
share_max_valid_days: 365
server_secret: CHANGE_ME
log_level: info
conf_overrides:
  - property: sharry.restserver.webapp.welcome-message
    value: Happy sharing!
```

**Note**: _Ceci n'est qu'un exemple, ne le copier-coller pas ! Crée le votre!_

### Option: `conf_overrides` (required)

La configuration de Sharry est spécifiée dans [HOCON][hocon].
Cela signifie que les valeurs d'une configuration peuvent être remplacées à
l'aide des propriétés Java comme décrit [ici][hocon-docs-props].
Cette option vous permet de fournir une option de remplacements de
configuration pour personnaliser les configutaions avancées de Sharry
qui n'ont pas été exposées en tant qu'options ci-dessus. Vous pouvez voir
l'ensemble complet des options disponibles ici :

<https://eikek.github.io/sharry/doc/configure#default-config>

**Note**: _La modification de ces options peut éventuellement entraîner
des problèmes avec votre instance. À UTILISER À VOS RISQUES ET PÉRILS!_

Celles-ci sont sensibles à la casse et tous les éléments définis par une
configuration spécifique seront prioritaires. Ceux qui ne peuvent pas être
remplacés sont signalés par un commentaire
dans la [configuration par défaut][default-config] que cet add-on utilise.

#### Sub-option: `conf_overrides.property` (required)

La propriété de configuration à définir. Doit être le chemin complet à
partir de la racine. Des instructions sur la manipulation des tableaux
peuvent être trouvées [ici][hocon-docs-arrays].

#### Sub-option: `conf_overrides.value` (required)

La valeur de la propriété à définir.

### Option: `DefaultStore` (required)

Le mode de stockage des données partagées.

Database: les données seront stocker dans une base de données Mariadb ou Postgres

Filesystem: les données seront stocker localement dans un fichier system
Localiser dans le dossier "share" de HA

### Option: `remote_db_host` (optional)

Si vous utilisez une base de données externe, le hostname/l'adresse
de la base de données MariaDB/Postgres.

### Option: `remote_db_type` (optional)

S'applique uniquement si une base de données distante est utilisée,
le type de base de données (`mariadb` ou `postgres`).

### Option: `remote_db_port` (optional)

S'applique uniquement si une base de données distante est utilisée,
le port sur lequel le serveur de base de données écoute.

### Option: `remote_db_database` (optional)

S'applique uniquement si une base de données distante est utilisée,
le nom de la base de données.

### Option: `remote_db_username` (optional)

S'applique uniquement si une base de données distante est utilisée,
le nom d'utilisateur qui possède les autorisations sur cette base de données.

### Option: `remote_db_password` (optional)

S'applique uniquement si une base de données distante est utilisée,
le mot de passe de l'utilisateur ci-dessus.

### Option: `local_db` (optional)

Renseignez le nom du repertoire où les données seront localement stocker.
Par défaut `Sharry`

### Option: `copy_db` (optional)

A définir si vous souhaiter activer la copie des données partagées
d'une base de données mariadb/postgres vers un stockage locale
ou inversement.
La copie est effectuée au démarrage de l'add-on.

### Option: `copy_db_source` (optional)

Selectionnez ici la source de la copie des données

### Option: `copy_db_target` (optional)

Selectionnez ici la destination de la copie des données

### Option: `domain` (required)

Le nom de domaine à partir duquel les utilisateurs accèderont à Sharry.
Sharry reçoit une URL de base qu'elle utilise pour générer des URL et
configurer des cookies. Cela sera créé à partir de cette option,
de l'option `use_ssl` et du port que vous avez indiqué pour `9090`.
Si le port n'est pas répertorié, l'add-on suppose que les utilisateurs
n'incluent pas de port dans l'URL lorsqu'ils accèdent à Sharry.

### Option: `ssl` (optional)

Active/Désactive SSL (HTTPS). Définissez-le sur `true` pour l'activer,
sinon `false`.

**Note**: _Les paramètres SSL s'appliquent uniquement à l'accès direct
et n'ont aucun effet sur le service Ingress._

### Option: `certfile` (optional)

Le fichier de certificat à utiliser pour SSL.

**Note**: _Le fichier DOIT être stocké dans `/ssl/`,
qui est la valeur par défaut_

### Option: `keyfile` (optional)

Le fichier de clé privée à utiliser pour SSL.

**Note**: _Le fichier DOIT être stocké dans `/ssl/`,
qui est la valeur par défaut_

### Option: `access.add_port` (optional)

Les ports que les utilisateurs devront fournir lors de l'accès à Sharry.
Si omis, suppose que les utilisateurs ne fourniront pas de port dans
l'URL lors de l'accès à Sharry.

### Option: `default_language` (optional)

Un code pays [ISO 3166-1][iso-3166-1]. La valeur par défaut est `us` si
omis ou si le code fourni n'est pas valide ou si sa langue
n'est pas disponible pour Sharry.

### Option: `share_max_size_gb` (optional)

La taille maximale d'un partage en Go. La valeur par défaut est `1.5`.

### Option: `share_max_valid_days` (optional)

Nombre maximum de jours pendant lesquels un partage peut être valide.
La valeur par défaut est `365`.

### Option: `server_secret` (required)

_Secret_ utilisé pour signer les jetons d'authentification générés pour les
clients. Préfixez-le avec `hex:` pour utiliser une valeur
hexadécimale ou `b64:` pour utiliser une valeur encodée en base64.

### Option: `reset_database` (optional)

Définir sur `true` pour supprimer et recréer la base de données au démarrage.
Comme les données sont conservées dans l'addon MariaDB, elles ne sont pas
supprimées lors d'une désinstallation.

**Note**: _Cette option s'applique **uniquement** si vous utilisez le module
complémentaire MariaDB, il n'essaiera pas de supprimer une base de
données MySQL distante. De plus, une fois la base de données réinitialisée,
cette option de configuration sera automatiquement désactivée pour l'addon._

## Changelog & Releases

Vous pouvez consulter le changelog [GitHub ici][releases].

## Support

Je ne suis pas dévellopeur, n'ai aucune formation de code, je suis simplement autodidact.
Si vous avez une question concernant HA et ses add-ons vous pouvez consulter:

- [Le Forum communautaire francophone][hacf] de HomeAssistant
- [Le Forum communautaire anglophone][forum] de HomeAssistant.
- [Le serveur Discord][discord-ha] de HomeAssistant.

## Authors & contributors

Ce projet est un fork du projet original de [Mike Degatano][mdegat01].

Pour une liste complète des auteurs et contributeurs merci de consulter
la [page des contributeurs][contributors].

## License

MIT License

Copyright (c) 2022-2024 [Frosh][Frosh]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> **_Parts of the project are copied and inspired by a project originally Copyright
> (c) 2021-2023 [Mike Degatano][mdegat01], distributed under [MIT License.][sharrylicense]:_**
>
> > Permission is hereby granted, free of charge, to any person obtaining a copy
> > of this software and associated documentation files (the "Software"), to deal
> > in the Software without restriction, including without limitation the rights
> > to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> > copies of the Software, and to permit persons to whom the Software is
> > furnished to do so, subject to the following conditions:\_
> >
> > _The above copyright notice and this permission notice shall be included in all
> > copies or substantial portions of the Software._
> >
> > _THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> > IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> > FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> > AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> > LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> > OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> > SOFTWARE._

[add-addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=c751e21a_sharry
[add-addon-shield]: https://my.home-assistant.io/badges/supervisor_addon.svg
[add-repo]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Ferdnaxela02%2Fhassio-addons
[add-repo-shield]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg
[add-addon-mariadb]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_mariadb
[addon-mariadb]: https://github.com/home-assistant/addons/tree/master/mariadb
[default-config]: https://github.com/erdnaxela02/addon-sharry/blob/main/sharry/rootfs/etc/sharry/sharry.conf
[discord-ha]: https://discord.gg/c5DvZ4e
[forum]: https://community.home-assistant.io
[hacf]: https://forum.hacf.fr/
[hocon]: https://github.com/lightbend/config/blob/master/HOCON.md#hocon-human-optimized-config-object-notation
[hocon-docs-arrays]: https://github.com/lightbend/config/blob/master/README.md#set-array-values-outside-configuration-files
[hocon-docs-props]: https://github.com/lightbend/config/blob/master/HOCON.md#java-properties-mapping
[iso-3166-1]: https://en.wikipedia.org/wiki/ISO_3166-1
[Frosh]: https://github.com/erdnaxela02
[mdegat01]: https://github.com/mdegat01
[sharrylicense]: https://github.com/mdegat01/addon-sharry/blob/main/LICENSE
[contributors]: https://github.com/mdegat01/addon-sharry/graphs/contributors
[releases]: https://github.com/erdnaxela02/addon-sharry/releases
[sharry]: https://eikek.github.io/sharry/
[sharry-docs-configure]: https://eikek.github.io/sharry/doc/configure
