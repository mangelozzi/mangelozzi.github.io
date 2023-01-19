# Chrome Setup

Prefer `Markdown Viewer` over `Markdown Previw Plus` since it render code block
highlighting correctly.


## EXTENSION - MARKDOWN VIEWER

[Full documentation available here](https://github.com/simov/markdown-viewer)

[Get the extension here](https://chrome.google.com/webstore/detail/markdown-viewer/ckkdlimhmcjmikdlpkmbgfkaikojcbjk/related)

1. Click top 3 vertical dots
2. Click on `More tools`
3. `Extensions`
4. Under `Markdown Viewer` select `Details`
5. Enable `Allow access to file URLs`


## EXTENSION - ADVANCED REST CLIENT

To be able to make REST calls with Chrome:

1. Install `Advanced REST client` extension
2. Install `ARC cookie exchange` extension
3. Go to apps -> `ARC`
4. Enter In the URL, and if the API request authentication already set in the
   browser, then just to the right of `SEND`, click `⋮`, and select
   `Use XHR`.
5. Can add headers if required.
6. Click `SEND`.

## EXTENSIONS - UBLOCK

1. Right click on the icon to the right of the address bar and select `Options`.
2. `Filters lists` tab
3. Scroll down to `Annoyances`
4. Check `AdGuard Annoyances` and `AdGuard Social Media`
5. At the top click `Update now`.

## PROFILE DATA

Profile data is stored at: `%USERPROFILE%\AppData\Local\Google\Chrome\User Data\`.
If you go to say `Profile 1/` and look at `Google Profile Picture.png` to determine
which profile is which.

Can start a given profile with `chrome --profile-directory="Profile 2" path/to/file.html`

## FIXES

- `chrome://flags/#overlay-scrollbars` and disable overlay scrollbars
