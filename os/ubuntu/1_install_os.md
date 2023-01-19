# Ubuntu OS Installation

## USEFUL HOTKEYS

- `F2` = Boot Settings
- `F12` = One time menu (Select what to boot from, diagnostics tests etc.)

## BEFORE YOU START

1. Recommend installing Linux/Ubuntu before Windows, it has better partition
   creation tools.

## INSTALLATION PREP

1. Download a desktop Ubuntu ISO image

## MAKE USB BOOT TOOL

- Linux:
    ```
    sudo apt install usb-creator-gtk
    usb-creator-gtk
    ```
- Windows: Use `Rufus` to add it onto a boot flash stick.

## BOOT FROM USB

1. Restart, press `F2` to enter BIOS settings
2. Disable `Secure boot`
3. **Enable** boot from USB boot under `USB settings`
4. Save and exit
5. Press `F12` to enter boot menu selection, and select USB disk

## PARTITIONS

1. Select `Something else`
1. Can delete all partitions, if required.
2. Create a `GPT` type UEFI partition (`100MB` min, `550MB` if dual boot system).
3. Swap space 2x RAM size (if plan to use hibernation)
