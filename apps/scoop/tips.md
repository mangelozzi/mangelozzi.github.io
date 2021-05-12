# Scoop Tips

## REMEMBER

```
scoop search foo
```

## INTEGRATION

- After installation, go to `C:\Users\Michael\scoop\apps` and right click on
  the `current` exe's and select `Pin to Start`
- If require the app on the path, add it manually to the path

## Notes

- Before adding additional buckets, git must be installed.
- To search for an app, use `scoop search foo`

## MAIN BUCKET (Installed by default)

[Listing of available apps](https://github.com/ScoopInstaller/Main/tree/master/bucket)

Notes:

- `scoop install cmder-full` includes git as well, but then only have git when
  inside cmder
- `scoop install git` doesn't have right click `Git Bash here` because its the
  portable version, so just download it manually.
- Ignore the `Couldn't find manifest for 'vscredist' from 'extras' bucket`

```bat
scoop install aria2 (Multi connection downloads for scoop)
scoop install 7zip ripgrep fd fzf
scoop install cmder
scoop install nodejs (Web dev and Neovim-Coc requires this)
scoop install neovim (Probably wanna install nightly from version bucket below)
```

## NON PORTABLE BUCKET

[Listing of available apps](https://github.com/TheRandomLabs/scoop-nonportable/tree/master/bucket)

Add bucket `scoop bucket add nonportable`

```bat
scoop install pgadmin4-np
scoop install putty-np
scoop install foobar2000   # Also portable version available
```


## VERSION BUCKET

Add bucket `scoop bucket add versions`

```bat
scoop install neovim-nightly
```

## EXTRAS BUCKET

[Listing of available apps](https://github.com/lukesampson/scoop-extras/tree/master/bucket)

Add bucket `scoop bucket add extras`

```bat
scoop install anki
scoop install cryptomator
scoop install darktable           (add to start menu)
scoop install filezilla
scoop install winscp
scoop install gimp                (add to start menu)
scoop install greenshot           (refer to greenshot setup below)
scoop install inkscape            (add to start menu)
scoop install libreoffice-stable
scoop install mp3tag
scoop install putty
scoop install screentogif         (useful for showing bugs)
scoop install speedcrunch         (add to start menu)
scoop install sumatrapdf          (not good cause runs in portable mode and cant be used a default pdf viewer)
scoop install vlc
scoop install winmerge
```

Other notable apps

```bat
scoop install fontforge
scoop install kicad
scoop install freecad
scoop install audacity
scoop install pdfsam
scoop install notepadplusplus
scoop install youtube-dl
```

## NERD FONTS BUCKET

[Listing of available apps](https://github.com/matthewjberger/scoop-nerd-fonts/tree/master/bucket)

Add bucket `scoop bucket add nerd-fonts`
Installing font requires admin privileges, hence the `sudo` (even on windows)

```bat
sudo scoop install RobotoMono-NF
sudo scoop install inconsolatago-nf  (inconsolata-nf messes up fi in file with a telphone symbol)
```

