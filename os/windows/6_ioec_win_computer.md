Setup up Debian with WSL1 !! Not WSL2 as WSL2 is slow as balls when accessing windows partition
WSL1 does not support Fuse needed for AppImages, so have to build Neovim from source to install it:

https://github.com/neovim/neovim/wiki/Building-Neovim#build-prerequisites
1. `sudo apt-get install ninja-build gettext cmake unzip curl`
2. `git clone https://github.com/neovim/neovim`
3. `cd neovim && make CMAKE_BUILD_TYPE=RelWithDebInfo`
4. ... don't cd build again... `cpack -G DEB && sudo dpkg -i nvim-linux64.deb`



Setup Windows terminal to use git bash:
<https://www.timschaeps.be/post/adding-git-bash-to-windows-terminal/>

User Microsoft Power Toys -> `Keyboard Manager` -> `Enabled Keyboard Manager` -> then click the `+`
- Remap Escape -> Capslock
- CapsLock -> WinL
- WinL -> Escape


- To get ping command working:
    - `setcap 'cap_net_raw+p' /bin/ping`
- To get network working:
    - `sudo nvim /etc/hosts`
    - And add these 2 lines:
        ```
        192.168.16.218  buildserver
        192.168.16.37   ioecsrvsqldev
        ```
