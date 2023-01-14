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

## I3WM

- Installation from <https://i3wm.org/docs/repositories.html>:
- May have fix `sudo nvim /etc/apt/sources.list.d/sur5r-i3.list` by adding the architecture flag:
    deb http://debian.sur5r.net/i3/ ...
    to
    deb [arch=amd64] http://debian.sur5r.net/i3/ ...

```
cd ~/appimages
/usr/lib/apt/apt-helper download-file https://debian.sur5r.net/i3/pool/main/s/sur5r-keyring/sur5r-keyring_2022.02.17_all.deb keyring.deb SHA256:52053550c4ecb4e97c48900c61b2df4ec50728249d054190e8a0925addb12fc6
sudo apt install ./keyring.deb
echo "deb http://debian.sur5r.net/i3/ $(grep '^DISTRIB_CODENAME=' /etc/lsb-release | cut -f2 -d=) universe" | sudo tee /etc/apt/sources.list.d/sur5r-i3.list
sudo apt update
```

Make sure the version is right before installing it:
```
apt-cache show i3
```

Then install with:
```
sudo apt install -y i3
```
