# Windows Terminal Setup

Refer to `settings.json` for the settings file.

Is stored at `%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`


## Symlink Settings file

1. Ensure all instance of windows terminal are closed (or else will auto create settings file when its deleted)
2. Start cmd.exe in admin mode.
3.
    ```
    del "%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json";
    mklink "%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json" "\\wsl$\Ubuntu-20.04\home\michael\mangelozzi.github.io\apps\windows_terminal\settings.json"
    ```

## FONT

- Install [RobotoMono Nerd Font](../fonts/Roboto%20Mono%20Medium%20Nerd%20Font%20Plus%20Power%20Symbols.ttf)
- The whole font family is available in a zip from [Fonts dir](../fonts/)
