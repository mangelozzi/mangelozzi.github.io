# Nerd-Fonts Patcher

## INTRO

- Often these block chars are absent from fonts, and windows terminal has a
  useless fall back font.
- These are the unicode blocks of interest: [Unicode blocks](https://www.compart.com/en/unicode/block/U+2580)

## How to

[README on how to setup and use font-patcher](https://github.com/ryanoasis/nerd-fonts#option-8-patch-your-own-font)

1. Checkout the `betaboon` version of nerd-fonts, which just contains what's
   required for patching the fonts. The original `ryanoasis` version is over
   2GB due to all the included fonts.
   - <https://github.com/betaboon/nerd-fonts-patcher>
   - <https://github.com/ryanoasis/nerd-fonts>

2. Follow the instructions on how to install `fontforge`. I installed it in
   linux cause it already had python. Install `fontforge` from the apt repo.
3. Open the `font-patcher` script (has no `.py` extension) in the root dir:
    ```
        nerd-fonts-patcher/font-patcher
    ```
4. Set the horizontal and vertical alignment to not auto center by changing
   the default `align` and `valign` to an empty string for the `CUSTOM_ATTR`
   group.
    ```
   CUSTOM_ATTR = {
       'default': {'align': '', 'valign': '', 'stretch': '', 'params': ''},
    ```
5. Place the custom font to patch which contains the unicode block chars into
   the `src/glyphs/` dir. e.g.:
   Source Code Pro for Powerline.otf
   - [Source Code Pro (Google Fonts)](https://fonts.google.com/specimen/Source+Code+Pro)
   - [Source Code Pro (Powerline Fonts)](https://github.com/powerline/fonts/tree/master/SourceCodePro)
   ```
    nerd-fonts-patcher/src/glyphs/SourceCodePro-Regular.ttf
    nerd-fonts-patcher/src/glyphs/Source Code Pro for Powerline.otf
   ```
6. Then run:
    ```
    sudo fontforge -script font-patcher --powersymbols --powerline --powerlineextra --custom SourceCodePro.otf RobotoMono-Medium.ttf
    ```
7. Can check the generated font (appears in `nerd-fonts-patcher` root dir) by dropping it into `https://fontdrop.info/`.
8. Check glyphs `0x258C` and `0x2590` are not aligned centrally.











