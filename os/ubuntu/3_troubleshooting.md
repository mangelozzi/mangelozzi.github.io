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
