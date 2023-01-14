# APPS

## BASE APPS

- Require `GIT` and `CURL`

```
sudo apt install -y git curl
```

## GET GIT SSH

1. Copy from:
    - SRC: Cryptomator -> `Mighty_Secure` -> Michael -> SSH -> Github -> `github_dev` (remove the password hint suffix)
    - OUT: `~/.ssh/github_dev`
2. `sudo chown 700 ~/.ssh/github_dev`
3. `eval $(ssh-agent)`
4. `ssh-add ~/.ssh/github_dev`

## INSTALL DOT FILES

- From `https://github.com/mangelozzi/dotfiles`:

```
curl https://raw.githubusercontent.com/mangelozzi/dotfiles/master/.config/install/_install_config.sh | bash
```

## Config (dot files)

- [First setup config files](https://github.com/michael-angelozzi/.config)

## Bash

- [Setup bash RC file](https://github.com/michael-angelozzi/.config/tree/master/bash)

## Update Package Repo

```bash
sudo apt update
```

## Speedcrunch

```bash
sudo apt install -y speedcrunch
```

## QDirStat

```bash
`sudo apt install -y qdirstat`
```

## These are install by config scripts:

## Ripgrep

For searching within files

```bash
curl -LO https://github.com/BurntSushi/ripgrep/releases/download/11.0.2/ripgrep_11.0.2_amd64.deb
sudo dpkg -i ripgrep_11.0.2_amd64.deb
```

## Fd

For searching file names

```bash
sudo apt install fd-find
```

Unfortunately the name `fd` is already taken, if one makes an alias (`alias fd=fdfind`), then
nvim can't see it (as its only available in bash). Just make a copy of the binary with:
  `sudo cp /bin/fdfind /bin/fd`

## FZF

```bash
sudo apt install fzf
```

## Tree

```bash
sudo apt install tree
```
