<div align="center">

<img src="snap/gui/papr.png" alt="Papr logo" width="128" />

# Papr

**Read, organize and search your feeds from the desktop or command line.**

[![papr](https://snapcraft.io/papr/badge.svg)](https://snapcraft.io/papr)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64, arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Papr](https://github.com/l0ng-ai/papr), a local RSS reader with feeds, folders, full-text articles, tags, highlights, newsletters, audio and a command-line companion.

</div>

---

## Getting Started

<a href="https://snapcraft.io/papr"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install papr
papr
```

Launch the desktop once to create your database, then add a feed or import an OPML file. The CLI works without a desktop session after that:

```bash
papr.cli feeds
papr.cli --help
```

For more commands, see the [upstream CLI guide](https://github.com/l0ng-ai/papr/blob/main/docs/cli.md). Use `papr.cli` wherever that guide or the CLI's command suggestions say `papr`; the snap's `papr` command opens the desktop.

## Configure

Use the application's settings for feed refreshes, network proxies, sync and optional AI providers. There are no `snap set` options.

The desktop and CLI share `~/snap/papr/current/.local/share/com.thomas.papr/papr.db`. Settings stay under `~/snap/papr/current`, and cached files stay under `~/snap/papr/common/.cache`. Existing data from other Papr installations is separate; OPML imports subscriptions, not saved articles or reading history.

The CLI's `--db` option and `PAPR_DB` variable can select another accessible Papr database.

For OPML files or saved images on removable storage:

```bash
sudo snap connect papr:removable-media
```

## Limitations

- Automatic agent setup is unavailable. Configure your host agent to run `/snap/bin/papr.cli` manually.
- The application's launch-at-login control is hidden. To start Papr when you sign in, add `/snap/bin/papr` through your desktop's Startup Applications settings.
- File access is limited to the snap's own data, accessible home files and connected removable storage. Hidden host directories are not automatically accessible.
- Browser subscription links use `papr://` and may open another Papr window because upstream does not provide single-instance handling. The browser extension is installed separately.
- Desktop updates come through `snap refresh papr`. In-app checks direct you to the Snap Store.

## Build

```bash
git clone https://github.com/sidalit/papr-snap.git
cd papr-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/papr-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/l0ng-ai/papr/issues).

## License

Snap packaging: [MIT](LICENSE).
