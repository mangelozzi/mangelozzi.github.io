# Windows Settings

## Scroll Bars

Search from start menu for `Automatically hide scroll bars in Windows` and disable
that retarded idea.

## win+I Settings

- Go through each menu and hunt down and disable all the new annoying "features".
- `Night light` schedule ON at 18:30 and OFF at 6:30

## Uninstall unwanted apps

1. `Control Panel\Programs\Programs and Features`
2. `Win+I` settings ->`Apps`->`Apps and Features`

## Hardware and Sound settings

In explorer nav to `Control Panel\Hardware and Sound`

### AutoPlay

- `Change default settings for media or devicves` -> Disable `Use AutoPlay
  for all media devices`

### Sound

- `Change system sounds` -> Change sound `Sound Scheme` to `None`
- If the Sound volume goes down when you press up after it changes a song, do
  the following:
  1. Find the currently playing sound device, right click &rarr; `Properties`
  2. Select the `Advanced` tab
  3. Find the `Exclusive Mode` heading
  4. Uncheck `Allow applications to take exclusive control of this device`.

#### Volume goes Loud when playing new video

1. `Device Manager` &rarr; `Sound, video and game controllers`
2. `Realtek High Definition Audio Device` right click `Update driver`
3. Choose `Browse my computer for driver software`, and select 
   `Let me pick from a list of device drivers on my computer`.
4. Will have the choices:
   - `Realtek High Definition Audio Device`
   - `High Definition Audio Device` &larr; SELECT THIS ONE!!!
5. Ignore the warning click `OK`.

### Plugged in never go to sleep

- `Control Panel\Hardware and Sound\Power Options\Edit Plan Settings`

### Power Options

- `Change what the power buttons do` -> Disable sleep and closing the lid
- `Change when the computer sleeps` -> Disable plugged in sleep

## Disable Font aliasing (true type font)

## Remove unwanted task bar icons

1. Right click task bar and select `Taskbar settings`
2. Heading: `Notifications Area`
3. Click:   `Turn system icons on or off`

## Remove AMD Radeon from Context Menu

1. regedit
2. Nav to `Computer\HKEY_CLASSES_ROOT\Directory\Background\shellex\ContextMenuHandlers\ACE`
3. Prepend value with some dashes to disable it, e.g. `--{5E2121EE-0300-11D4-8D3B-444553540000}`

## Disable Lock screen

[Original guide link](https://www.cnet.com/how-to/how-to-disable-the-windows-10-lock-screen/)

1. regedit
2. Nav to `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows`
3. Right click `Windows` add key `Personalization`
4. Add New `DWORD (32-bit) Value` named `NoLockScreen` with value `1`

