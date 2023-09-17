# SETUP

## DROPBOX

- Install Dropbox so can install Cryptomator
- Download `.deb` file here: <https://www.dropbox.com/install>
- Right click on file and say open with software center, or `sudo dpkg -i file.deb`
- Can set Dropbox to selective sync the vault first if in a rush, then sync the other files later.

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
```
cp ~/.local/share/Cryptomator/mnt/Mighty_Secure/Michael/linux_setup/ssh/github_dev ~/.ssh/github_dev
cp ~/.local/share/Cryptomator/mnt/Mighty_Secure/Michael/linux_setup/ssh/config ~/.ssh/config
sudo chown -R $USER:$USER ~/.ssh
sudo chmod -R 700 ~/.ssh
eval $(ssh-agent)
ssh-add ~/.ssh/github_dev
```

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

## CONFIG - RUN INSTALLER SCRIPTS

- Info here: [First setup config files](https://github.com/michael-angelozzi/.config)
- `bash ~/.config/install/_all.sh`

## LOWER INCORRECT PASSWORD DELAY

- Change the delay from 3s to 0.5seconds:

1. `sudoedit /etc/pam.d/login`
2. Find the line:
    ```
    auth       optional   pam_faildelay.so  delay=3000000
    ```
3. Decrease the delay (value is in micro seconds):
    ```
    auth       optional   pam_faildelay.so  delay=500000
    ```
