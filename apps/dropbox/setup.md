# Dropbox Setup

## Windows

### Disable Dropbox Hogging Explorer's Navigational quicklist

[Original guide link (On previous page is another method)](https://www.dropboxforum.com/t5/Dropbox-installs-integrations/How-does-one-remove-the-Dropbox-link-from-the-Navigation-Pane-om/td-p/93970/page/7):

1. `regedit`
2. Navigate to:
    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\NonEnum`
3. Right click -> `New DWORD Value`  
    Name:  `{E31EA727-12ED-4702-820C-4B6445F28E1B}`  
    Value: `1`
