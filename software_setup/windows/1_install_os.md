# Windows OS Installation

Last used on Windows 10 release 19041

## USEFUL HOTKEYS

- `F2` = Boot Settings
- `F12` = One time menu (Select what to boot from, diagnostics tests etc.
- `F8` = Safe mode.
Safe mode was removed to make it boot faster.
If unsuccessful boot 3 times then can select safe boot by going:
  1. In windows search for `Recovery options`
  2. Under `Advanced start up` select `Restart now`
  3. Then select `Use a device` then select the flash stick

## BEFORE YOU START

1. Make sure have Windows key on hand
   - To get it via a script, refer to `scripts/Get Windows Key.ps1`.
   Right click on the script and select `Run with Power Shell`
2. Recommend installing Linux/Ubuntu first, it has better partition creation
   tools. Refer to [Ubuntu OS Installation](../ubuntu/1_install_os.md)

## INSTALLATION PREP

1. Download a Window ISO image
2. Download `Windows USB/DVD Download Tool`
3. Use the tool to write it to disk.
4. Restart, press `F2` to enter BIOS settings
5. Disable `Secure boot`
6. **Enable** boot from USB boot under `USB settings`
7. Save and exit
8. Either:
  - Press `F12` to enter boot menu selection, and select USB disk
  - Alternatively in windows search for `Recovery options` and under
    `Advanced start up` select `Restart now` then 1use a device` then
    select the USB device.

## INSTALLATION

1. Choose language, keyboard layout, and region in vain, only to be asked 3
   times later on.
2. Disable all the new "features" ... next .. next windows style.

**!!! If M2800 freezes/crashes refer to [drivers](./2_drivers_setup.md) !!!**

