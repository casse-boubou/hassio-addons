# Home Assistant Add-on: P2pool

## About

Cet Addon vous permettra l'execution d'un pool décentralisé [p2pool][p2pool] sur
votre HomeAssistant sur RaspBerry Pi 4.

Pour toutes options de configuration et possibilitées d'applications, merci de vous
renseigner sur la page du projet [p2pool][p2pool].

## Installation

D'habord ajoutez le repertoire à l'add-on store de HomeAssistant (`https://github.com/erdnaxela02/hassio-addons`):

[![Open your Home Assistant instance and show the add add-on repository dialog
with a specific repository URL pre-filled.][add-repo-shield]][add-repo]

Ensuite recherchez P2pool dans le store et cliquez sur installer:

[![Open your Home Assistant instance and show the dashboard of a Supervisor add-on.][add-addon-shield]][add-addon]

## Configuration

Example add-on configuration:

```yaml
p2pool_conf_overrides:
  - property: no-cache
    value: ""
  - property: no-randomx
    value: ""
monero_wallet: YOUR_WALLET_ADDRESS
p2pool_mini_sidechain: true
p2pool_loglevel: "1"
```

**Note**: _Ceci n'est qu'un exemple, ne le copier-coller pas ! Crée le votre!_

**Note**: _Il est recommandeé d'utiliser les option `no-cache` et `no-randomx` sur
Raspberry afin d'economiser des resources mémoire._

### Option: `p2pool_conf_overrides`

Cette option vous permet de fournir une option de configuration pour personnaliser
les configutaions avancées de P2pool qui n'ont pas été exposées en tant qu'options
ci-dessous.

Vous pouvez voir l'ensemble complet des options disponibles ici :

<https://github.com/SChernykh/p2pool/blob/master/docs/COMMAND_LINE.MD>

**Syntax**:

```conf_syntax
- property: option-name
  value: "value"
OR
- property: valueless-option-name
  value: ""     **for options that don't expect value**
```

**Note**: _Toutes les options n'ont pas été testées. La modification de ces options
peut éventuellement entraîner des problèmes avec votre instance.
À UTILISER À VOS RISQUES ET PÉRILS!_

### Option: `monero_wallet`

Adresse de votre portefeuille Monero.

Avant de commencer à miner, créez un nouveau portefeuille et ne l'utilisez pas pour
autre chose que le minage pour des raisons de confidentialité - toutes les adresses
de portefeuille sont publiques sur P2Pool !

Seule les primary wallet address sont prisent en charge - pas de subaddresses ni
integrated addresses.

### Option: `p2pool_mini_sidechain`

Ajoutez le paramètre --mini à votre commande P2Pool pour vous connecter à la sidechain
p2pool-mini.
Notez que cela changera également le port p2p par défaut de 37889 à 37888.

### Option: `p2pool_loglevel`

Verbosité du journal, nombre entier compris entre 0 et 6.
P2Pool a une journalisation détaillée par défaut, vous pouvez la réduire en utilisant
la commande "loglevel N" où N est compris entre 0 et 6. Le niveau de journalisation
par défaut est 3.

## Changelog & Releases

Vous pouvez consulter le changelog [GitHub ici][releases].

## Support

Je ne suis pas dévellopeur, n'ai aucune formation de code, je suis simplement autodidact.
Si vous avez une question concernant HA et ses add-ons vous pouvez consulter:

- [Le Forum communautaire francophone][hacf] de HomeAssistant
- [Le Forum communautaire anglophone][forum] de HomeAssistant.
- [Le serveur Discord][discord-ha] de HomeAssistant.

## License

MIT License

Copyright (c) 2022 [Frosch][frosch]

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

> **_Parts of the project are originally Copyright (c) 2022, [SChernykh][p2poolauthor],
> distributed under [GNU General Public License v3.0][p2poollicense]:_**
>
> > _- This program is free software: you can redistribute it and/or modify it under
> > the terms of the GNU General Public License as published by the Free Software
> > Foundation, either version 3 of the License, or (at your option) any later version._
> >
> > _- This program is distributed in the hope that it will be useful,
> > but WITHOUT ANY WARRANTY; without even the implied warranty of
> > MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
> > GNU General Public License for more details._
> >
> > _- You should have received a copy of the GNU General Public License
> > along with this program. If not, see <https://www.gnu.org/licenses>._

[add-addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=c751e21a_p2pool
[add-addon-shield]: https://my.home-assistant.io/badges/supervisor_addon.svg
[add-repo]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Ferdnaxela02%2Fhassio-addons
[add-repo-shield]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg
[discord-ha]: https://discord.gg/c5DvZ4e
[forum]: https://community.home-assistant.io
[hacf]: https://forum.hacf.fr/
[frosch]: https://github.com/erdnaxela02
[releases]: https://github.com/erdnaxela02/addon-p2pool/releases
[p2pool]: https://github.com/SChernykh/p2pool
[p2poolauthor]: https://github.com/SChernykh
[p2poollicense]: https://github.com/SChernykh/p2pool/blob/master/LICENSE
