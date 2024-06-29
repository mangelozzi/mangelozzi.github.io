1. Download MFC635 Driver:
    - <https://www.canon-europe.com/support/consumer/products/printers/i-sensys/mf-series/i-sensys-mf645cx.html?type=drivers&language=en&os=linux%20(64-bit)>
2. Extract it
3. `xhost +SI:localuser:root` or else get error about cannot open display 0.
    - I also did not use I3, but logged into Ubuntu with the default window manager without wayland support.
4. sudo ./setup.sh
5. sudo apt install scanner
