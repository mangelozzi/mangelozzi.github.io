# WORK

## APPS - Insync

1. Install `Insync` for Google Drive
2. Download from: <https://www.insynchq.com/downloads/linux>
3. Open in folder, right click and select `Open with other application` -> `Software install`
4. Open `Chrome` and sign into work account, and keep that tab open, then start `Insync`

## CRYPTOMATOR

1. Add the `~/Insync/<EMAIL_ADDRESS>/Google Drive/NanoCube/NanoCube_Secure` vault
1. Add personnel vault if you have, e.g.: `~/Insync/<EMAIL_ADDRESS>/Google Drive/NanoCube/NanoCube_Michael_Secure` vault
2. Unlock the `NanoCube_Secure` vault.

## SUDOERS

- Copy then move, i.e. 2 steps, or else get permission error
```
cp ~/.local/share/Cryptomator/mnt/NanoCube_Secure/terminal/terminal_sudoers ~/terminal_sudoers
sudo mv ~/terminal_sudoers etc/sudoers.d/terminal_sudoers
sudo chown root:root /etc/sudoers.d/terminal_sudoers
sudo chmod 440 /etc/sudoers.d/terminal_sudoers
```

### GET VPS PRIVATE KEYS

- The public keys have the `.pub` extension.

```
cd ~/.local/share/Cryptomator/mnt/NanoCube_Secure/ssh_vps
fd -t f --exclude '*.*' 'vps-.*' | xargs cp -t ~/.ssh
cd ~/.ssh
sudo chown -R $USER:$USER ~/.ssh
sudo chmod -R 700 ~/.ssh
```
