# Windows Terminal

Refer to `windows_terminal/settings.json` for the settings file.

Is stored at `%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`

Symlink it to the checkout with (Required admin CMD):
```
mklink "%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json" "\\wsl$\Ubuntu-20.04\home\michael\mangelozzi.github.io\software_setup\apps\windows_terminal\settings.json"
```

## FONT

- Install [RobotoMono Nerd Font](../fonts/Roboto%20Mono%20Medium%20Nerd%20Font%20Plus%20Power%20Symbols.ttf)
- The whole font family is available in a zip from [Fonts dir](../fonts/)
