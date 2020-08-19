# WSL2

- Follow this guide:
- <https://docs.microsoft.com/en-us/windows/wsl/install-win10>

## DNS (Cannot resolve host)

Neovim will fail to install packages, so will apt-get update. To fix do the following:

1. Create a file: `/etc/wsl.conf`.
2. Put the following lines in the file

```
[network]
generateResolvConf = false
```
3. In a `cmd` window, run `wsl --shutdown`
4. Restart WSL2

5. `ls -l /etc/resolv.conf` and check its not a symlink.
6. If it is a symlink, then delete the file, and copy the source.
7. Change `172.24.0.1` to another nameserver, e.g.:
   - Current router: `192.168.0.1`
   - Google: `8.8.8.8`

## .BASHRC NOT EXECUTED

To tell windows to start wsl/bash with an interactive shell (i.e. load ~.bashrc)
one can do `bash.exe -i` (now you have colours and should feel more homey).

To have `wsl` or `bash` automatically start an  interactive prompt, create
`~/.profile` and paste inside of it:
```bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi
```

