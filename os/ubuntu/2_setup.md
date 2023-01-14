# SETUP

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

## Config - Run installer scripts

- `bash ~/.config/install/_all.sh`
