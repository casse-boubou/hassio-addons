# Frosch Home Assistant Add-ons

[![License][license-shield]](LICENSE)

Une collection d'add-on pour HomeAssistant faite par Frosch et développer pour Raspberry Pi 4.

## Installation

Clicuez sur le lien suivant et suivez les instructions:

[![Open your Home Assistant instance and show the add add-on repository dialog
with a specific repository URL pre-filled.][add-repo-shield]][add-repo]

Ou sinon vous pouvez copier cet URL et l'ajouter manuellement dans le
add-on store de votre HA:

```txt
https://github.com/erdnaxela02/hassio-addons
```

## Add-ons disponible

### &#10003; [Sharry][addon-sharry]

![Latest Version][sharry-version-shield]
![Supports armhf Architecture][sharry-armhf-shield]
![Supports armv7 Architecture][sharry-armv7-shield]
![Supports aarch64 Architecture][sharry-aarch64-shield]
![Supports amd64 Architecture][sharry-amd64-shield]
![Supports i386 Architecture][sharry-i386-shield]

Sharry pour Home Assistant

[![Open your Home Assistant instance and show the dashboard of a Supervisor add-on.][add-addon-shield]][add-addon-sharry]

[:books: Sharry add-on documentation][addon-doc-sharry]

### &#10003; [Sharry-dependency-less][addon-sharry-dependency-less]

![Latest Version][sharry-dependency-less-version-shield]
![Supports armhf Architecture][sharry-dependency-less-armhf-shield]
![Supports armv7 Architecture][sharry-dependency-less-armv7-shield]
![Supports aarch64 Architecture][sharry-dependency-less-aarch64-shield]
![Supports amd64 Architecture][sharry-dependency-less-amd64-shield]
![Supports i386 Architecture][sharry-dependency-less-i386-shield]

Sharry pour Home Assistant sans dependances a Mariadb

[![Open your Home Assistant instance and show the dashboard of a Supervisor add-on.][add-addon-shield]][add-addon-sharry-dependency-less]

[:books: Sharry-dependency-less add-on documentation][addon-doc-sharry-dependency-less]

## Support

Je ne suis pas dévellopeur, n'ai aucune formation de code, je suis simplement autodidact.
Si vous avez une question concernant HA et ses add-ons vous pouvez consulter:

- [Le Forum communautaire francophone][HACF] de HomeAssistant
- [Le Forum communautaire anglophone][forum] de HomeAssistant.
- [Le serveur Discord][discord-ha] de HomeAssistant.

## License

MIT License

Copyright (c) 2022 erdnaxela02

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

[addon-sharry]: https://github.com/erdnaxela02/addon-sharry/tree/v1.0.0
[addon-doc-sharry]: https://github.com/erdnaxela02/addon-sharry/blob/v1.0.0/README.md
[sharry-version-shield]: https://img.shields.io/badge/version-v1.0.0-blue.svg
[add-addon-sharry]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=c751e21a_sharry
[sharry-aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[sharry-amd64-shield]: https://img.shields.io/badge/amd64-no-red.svg
[sharry-armhf-shield]: https://img.shields.io/badge/armhf-no-red.svg
[sharry-armv7-shield]: https://img.shields.io/badge/armv7-no-red.svg
[sharry-i386-shield]: https://img.shields.io/badge/i386-no-red.svg

[addon-sharry-dependency-less]: https://github.com/erdnaxela02/addon-sharry-dependency-less/tree/v0.1.0
[addon-doc-sharry-dependency-less]: https://github.com/erdnaxela02/addon-sharry-dependency-less/blob/v0.1.0/README.md
[sharry-dependency-less-version-shield]: https://img.shields.io/badge/version-v0.1.0-blue.svg
[add-addon-sharry-dependency-less]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=c751e21a_sharry-dependency-less
[sharry-dependency-less-aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[sharry-dependency-less-amd64-shield]: https://img.shields.io/badge/amd64-no-red.svg
[sharry-dependency-less-armhf-shield]: https://img.shields.io/badge/armhf-no-red.svg
[sharry-dependency-less-armv7-shield]: https://img.shields.io/badge/armv7-no-red.svg
[sharry-dependency-less-i386-shield]: https://img.shields.io/badge/i386-no-red.svg

[add-addon-shield]: https://my.home-assistant.io/badges/supervisor_addon.svg
[add-repo-shield]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg
[add-repo]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A//github.com/erdnaxela02/hassio-addons
[license-shield]: https://img.shields.io/github/license/erdnaxela02/hassio-addons.svg
[discord-ha]: https://discord.gg/c5DvZ4e
[forum]: https://community.home-assistant.io/
[HACF]: https://forum.hacf.fr/
 