# Greenshot Setup

1. Close Greenshot (when it closes it overwrites the `.ini` file)
2. Open `C:\Users\Michael\scoop\apps\greenshot\1.2.10.6\greenshot.ini`
3. Replace

  ```ini
  ExcludePlugins=
  ```

  with

  ```ini
  ExcludePlugins=Box Plugin,Confluence Plugin,Dropbox Plugin,Flickr Plugin,Imgur Plugin,Jira Plugin,OCR Plugin,Office Plugin,Photobucket Plugin,Picasa-Web Plugin
  ```

   Note `External command Plugin` required for open with `mspaint`
4. Start Greenshot

## Auto Start up

1. `Settings` &rarr; `General` Tab &rarr; Check `Launch Greenshot at startup`
2. Find the scoop current .exe and ensure it is NOT set to run as admin.

Note: Alternate method (have not tried), copy and paste exe into `WIN+R` &rarr; `shell:startup`

