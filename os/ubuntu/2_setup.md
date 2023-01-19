# SETUP

## DROPBOX

- Install Dropbox so can install Cryptomator
- Download `.deb` file here: <https://www.dropbox.com/install>
- Right click on file and say open with software center, or `sudo dpkg -i file.deb`

## CRYPTOMATOR FILES

- Install Cryptomator:
    ```
    sudo add-apt-repository ppa:sebastian-stenzel/cryptomator
    sudo apt update
    sudo apt install -y cryptomator
    ```
- Add the `Shared` -> `Secure` -> `Mighty_Secure` vault.

## SSH

1. Copy files from from:
    - SRC: Cryptomator -> `Mighty_Secure` -> `Michael` -> `linux_setup` -> `ssh`
    - OUT: `~/.ssh/`
2. `sudo chown -R $USER:$USER ~/.ssh`
3. `sudo chmod -R 700 ~/.ssh`
4. `eval $(ssh-agent)`
5. `ssh-add ~/.ssh/github_dev`


## BASE APPS

- Require `GIT` and `CURL`

```
sudo apt install -y git curl
```

## INSTALL DOT FILES

From `https://github.com/mangelozzi/dotfiles`:

```
curl https://raw.githubusercontent.com/mangelozzi/dotfiles/master/.config/install/_install_config.sh | bash
```

## Config - Run installer scripts

- Info here: [First setup config files](https://github.com/michael-angelozzi/.config)
- `bash ~/.config/install/_all.sh`
