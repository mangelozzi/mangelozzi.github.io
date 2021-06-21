# Windows Drivers

For Dell M2800 Precision

## SYSTEM FREEZING ISSUE

### The Problem

After Installing windows, Graphics card causes freezing/crashes. After
anniversary Update there is a issue with ULPS (ultra low power state) and AMD
drivers newer than Crimson 16.7.2. It causes a system freeze. AMD removed the
PCI driver from its newest driver installations.

Note:    The real graphics card is `AMD FirePro W4170M`, but it shows up as `AMD Radeon HD 8790M`

### The Fix

Install AMD's PCI BUS driver. Refer to [this thread](https://community.amd.com/thread/220531#comment)

1. Boot to `Safe mode (without networking)`
If unsuccessful boot 3 times then can select safe boot by going:
  1. In windows search for `Recovery options`
  2. Under `Advanced start up` select `Restart now`
  3. Then select `Use a device` then select the flash stick
2. In safe mode go to device settings and
   disable `Display Adapters` -> `AMD Radeon ...`
3. Download AMD PCI Nov-2017 driver: `drivers/AMD-PCI-DRIVER.zip`
4. Extract the driver
5. Right click on `amdkmpfd.inf` and select `Install`.
    - (This is easier than finding the PCI bus and selecting update driver...)
6. Will ask you to reboot, select reboot.

### Install The Graphics Card Driver from Dell:

## INSTALL DRIVERS

1. Go to `NAS/Michael/Sofware - Windows/M2800 Drivers`
2. Install the following in this order:
  1. Graphics Card:
        - `Intel-HD-Graphics-4000-5000-500-P500-series-Driver_WWW9Y_WIN_20.19.15.5063_A10_01.EXE`
  2. Chip set Drivers 1:
        - `Chipset_Driver_3664N_WN_9.4.0.1027_A03.EXE`
  3. Intel Management Engine Components Installer:
        - `Chipset_Driver_4J8MX_WN32_11.7.0.1035_A00_07.EXE`
  4. Now can install the dell graphics card driver:
        - This driver is old but at least works with freeCAD.
        - Can't use Dell drivers with KiCAD PCB Editor.
            - [`M2800_Video_Driver_G5JNR_WN32_15.201.1101_A01.EXE`](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverId=G5JNR)
        - NOT the latest AMD Radeon driver:
            - The AMD drivers come up as the wrong graphics card (8790) and does not work with anything.
            - `radeon-software-adrenalin-2020-20.4.2-minimalsetup-200423_web.exe`
  6. Then Unzip the driver bundle:
     `M2800-Win10-A03-6HN8N.CAB`
  7. Go to device manager, and right click on each item, and manually select update and point
     to the extracted cab file contents.
  8. If Bluetooth not working well, can try:
        - `Intel-9x60-826x-7265-3165-7260-Bluetooth-Legacy-Driver_PDYP9_WIN_20.60.0_A22.EXE`

