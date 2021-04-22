# WSL2

## ADD A SECOND DITRO

Based on [this SuperUser post](https://superuser.com/questions/1515246/how-to-add-second-wsl2-ubuntu-distro-fresh-install):

1. Download: <https://cloud-images.ubuntu.com/releases/focal/release/ubuntu-20.04-server-cloudimg-amd64-wsl.rootfs.tar.gz>
3. Add the new distro with:
    ```
    wsl.exe --import <DISTRO_HANDLE> <INSTALL_DIR> <DL_TAR_GZ_PATH>
    ```
    e.g. say we call this distro `ubuntu_b`:
    ```
    wsl.exe --import ubuntu_b "D:\wsl\ubuntu_b" "D:\wsl\ubuntu-20.04-server-cloudimg-amd64-wsl.rootfs.tar.gz"
    ```
4. Start the image with: `wsl.exe -d ubuntu_b`

### Change default user of NONE DEFAULT Distro

- For default distro can use `ubuntu config --default-user username`
- Refer to [github issue](https://github.com/microsoft/WSL/issues/3974).
- Add to `/etc/wsl.conf`:

### Change root password of 2nd Distribution

- When creating the 2nd distribution it does not ask you for root password.
- Open a new shell (be logged in as root).
- `passwd` and enter in the new password.

```
[user]
default=username
```

## DELETE A DISTRO

- `wsl --unregister <DISTRO_HANDLE>`
- e,g, `wsl --unregister ubuntu_b`

## WSL2 SERVE UP CONTENT TO EXTERNAL NETWORK

- By default WSL2 communicates only with windows processes on the same computer.
- To be able to view Django from another host, e.g. phone, one must setup WSL2
  to forward traffic from windows to WSL2 on the required port.
- Note the WSL2 IP address changes from time to time.
- Can refer to [this help script](https://gist.github.com/xmeng1/aae4b223e9ccc089911ee764928f5486)
- Some blogs indicate that one can port forward to 127.0.0.1, but this does not
  work when I tested, it have to be the WSL IP address, e.g. `172.31.191.138`

