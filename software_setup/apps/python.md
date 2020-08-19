# Python

## INSTALLATION

### Ubuntu

Why not?

```bash
sudo apt install python3.8
```

Building from source [guide](https://linuxize.com/post/how-to-install-python-3-8-on-ubuntu-18-04/):

1. Use check install to control the installation so it can be uninstalled:
  - `sudo apt-get update && sudo apt-get install checkinstall`
Install requirements to build from source:
1. libffi-dev ...c_types for black
. `sudo apt-get install libffi-dev python3.8-dev`
Not sure about this list: `sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget`
1. Download most recent stable version from [python.org](https://www.python.org/download/other/)
2. Extract archive and cd into the dir
`./configure  --enable-optimizations`
`make`
Use check install so it can be uninstalled if required, call package python3.8
Call make install with `j -4` to use 4 cores.
`sudo checkinstall make install -j 4` (instead of sudo make install)

### Windows

Download installer from [here](https://www.python.org/downloads/windows/)

## PIP

### PIP (Ubuntu)

1. `sudo apt -y install python3-pip`
2. `apt-get install python3-venv` (Ubuntu, for venv/ (supposed to be OOTB))

### PIP (Windows)

Already bundled in with the windows installer

