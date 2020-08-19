# Windows Terminal

Refer to `windows_terminal/settings.json` for the settings file.

Is stored at `%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`

Symlink it to the checkout with (Required admin CMD):
```
mklink "%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json" "C:\code\software_setup\apps\windows_terminal\settings.json"
```
