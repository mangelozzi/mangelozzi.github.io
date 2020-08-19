# APPS

## Config (dot files)

- [First setup config files](https://github.com/michael-angelozzi/.config)

## Bash

- [Setup bash RC file](https://github.com/michael-angelozzi/.config/tree/master/bash)

Refer to:

## Documented stand alone apps:

- [Anki](../apps/anki.md)
- [Chrome](../apps/chrome.md)
- [Node.js](../apps/nodejs.md)
- [Python](../apps/python.md)

## 1. Update Package Repo

```bash
sudo apt update
```

## 2. Ripgrep

For searching within files

```bash
curl -LO https://github.com/BurntSushi/ripgrep/releases/download/11.0.2/ripgrep_11.0.2_amd64.deb
sudo dpkg -i ripgrep_11.0.2_amd64.deb
```

## 3. Fd

For searching file names

```bash
sudo apt install fd-find
```

Unfortunately the name `fd` is already taken, if one makes an alias (`alias fd=fdfind`), then
nvim can't see it (as its only available in bash). Just make a copy of the binary with:
  `sudo cp /bin/fdfind /bin/fd`

## 4. FZF

```bash
sudo apt-get install fzf
```

