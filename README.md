# NinjaRemote on Linux

I am using Fedora Linux so the commands here will be run on Fedora 36.

## Installing Prerequisites

1. Install Wine  
```sh
sudo dnf install wine* -y
```
***You may need to enable rpm fusion depending on your distribution***

2. Change browser useragent to show that you are running Windows. There are many tutorials on how to do this. I used this extension in Chrome: [User-Agent-Switcher](https://chrome.google.com/webstore/detail/user-agent-switcher/kchfmpdcejfkipopnolndinkeoipnoia?hl=en)  
You will need to find the custom string for Chrome on windows and add it to the list.  
This is important because since we aren't on Windows, the Ninja Remote icon doesn't appear
<br>
3. Sign into Ninja and download the ncplayer msi.  
<br>
4. Install Ncplayer:

```bash
wine /home/<username>/ncinstaller-x64.msi
```

5. Create a file:  

```bash
nano ~/.local/share/applications/ncplayer.desktop
```

with the contents :

```ini
[Desktop Entry]
Exec=wine /home/<username>/.wine/drive_c/users/<username>/AppData/Roaming/NinjaRemote/ncplayer.exe -u %u
Type=Application
Terminal=false
MimeType=x-scheme-handler/ninjarmm;
```

6. Install the desktop entry so that Chrome can recognize the protocol.

```bash
xdg-desktop-menu install ~/.local/share/applications/ncplayer.desktop --novendor
```  

7. Install dxvk wine module

```bash
winetricks dxvk
```

<br>

7. Launch Ninja Remote from the Machine page in the web portal.  

The client will open, connect, then close, then re-establish the connection.
