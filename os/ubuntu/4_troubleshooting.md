# Troublehshooting

## NO PERMISSION TO ACCESS USB DRIVE

1. `sudo nvim /usr/share/polkit-1/actions/org.freedesktop.UDisks2.policy`
2. Find the block `<action id="org.freedesktop.udisks2.filesystem-mount">`
3. Change from:

    defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>

4. Change to (2x yes):

   <defaults>
      <allow_any>yes</allow_any>
      <allow_inactive>yes</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>

- <https://en.linuxportal.info/tutorials/troubleshooting/how-to-clear-the-not-authorized-to-perform-operation-error-message-when-automatically-attaching-USB-flash-drives-and-other-external-USB-storage-devices>

## Change Default OS in Multi Boot systems

- <https://www.techmesto.com/set-windows-as-default-in-linux-dual-boot/>
1. Turn on your PC and take a look at the GRUB screen. Note the position Windows loader is at (0-INDEXED COUNTING!) and then proceed with booting up with your Linux install.
2. `sudo nvim /etc/default/grub`
3. Set `GRUB_DEFAULT=2` to the required number, e.g. if it is say the third position (0-indexed)
4. `sudo update-grub`


## Graphics Card

sudo apt-get install nvidia-driver-515

## Disable power saving sound card

- Sound card hums when power saving mode on (quite for about 10seconds)

<del>
- This is only temporary:
    ```bash
    sudo su -
    echo 0 > /sys/module/snd_hda_intel/parameters/power_save
    ```
</del>

- Permanent fix:

1. `sudo nvim /etc/modprobe.d/alsa-base.conf`
2. Append this line to the end of the file, save and reboot
    ```
    options snd-hda-intel power_save=0 power_save_controller=N
    ```
