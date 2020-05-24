# Installing OS.

Using a working machine...
Windows 10:
- Download: http://www.netbsd.org/~martin/rawrite32/
- Grab the USB img.gz (http://netbsd.org/). I used NetBSD-9.0-amd64-uefi-install.img.gz
- Open up the checksum page.
- Insert and format USB thumb drive (2GB+).
- Start Rawrite32.
- Verify the checksum as displayed by rawrite32.
- Go ahead and write it to the usb thumb drive.

Next remove the drive and plugin it into the target PC.
- Make sure you have a phone or other PC in reach, you will need it.
- Remove all the partitions from your PC. (This can also be done with the NetBSD installer).
- Make you system boot from the USB drive
- Although the image said uefi it didn't boot into UEFI. So I needed to switch my BIOS/EFI settings to "Legacy"
- Follow the instructions, if in doubt check here: http://netbsd.org/docs/guide/en/chap-inst.html
- WiFi settings during installation was something I wasn't able to do. It's not necessary anyways since I used the full usb img.gz.
- It's simplest to set the root password and create a non-root user in the setup GUI. Because this is the last chance to do it with a nice GUI.
- Reboot
- Login as non-root user
- You are done. Continue if you need internet access through WiFi.

# Setup WiFi
- ```ifconfig``` and not the network adapter name. In my case iwm0
- type ```su``` and login as root.
- I added the following snippet using: ```vi /etc/wpa_supplicant.conf```
```conf
network={
ssid="MYNETWORK"
key_mgmt=WPA-PSK
psk="MYKEY"
}
country=de
```
- save the document using ESC + !wq
- as root ```vi /etc/rc.conf```
- Add the following snippet:
```conf
wpa_supplicant=YES
wpa_supplicant_flags="-B -D bsd -i iwm0 -c /etc/wpa_supplicant.conf"
dhcpcd=YES
dhcpcd_flags="-qM iwm0 -b"
hostname=mywificlientname
```
- reboot
- login as non-root
- ping github.com

# Activate xdm window manager
- In order to get a GUI going, NetBSD got some basic X window management:
- ```su```
- ```vi /etc/rc.conf```
- Add snippet:
```conf
xdm=YES
```
- reboot
- login into the graphical shell.
- Switch to the thrusty old terminal with lower dpi res using CTRL+ALT+F1,F2,F3,F4. In my case XDM sits at CTRL+ALT+F5.

# Install <web browser, something else>
- Bewary of the fact that NetBSD does not contain any SSL certificates.
- Using pkg_add you can therefore (initially) only install through HTTP
- https://www.netbsd.org/docs/guide/en/chap-boot.html#chap-boot-pkgsrc
- Find out what PORT (arch) and Release you want to use (9.0). Check here with a web browser: http://cdn.netbsd.org/pub/pkgsrc/packages/NetBSD/amd64/
- Note: current and stable mean different things in NetBSD world. https://www.netbsd.org/releases/release-map.html
- In my case I type in the sh shell: (_current is needed for things like firefox).
- ```PKG_PATH="http://cdn.NetBSD.org/pub/pkgsrc/packages/NetBSD/amd64/9.0_current/All```
- This is now a current shell variable for sh to use.
- Export it so pkg_add can see it: ```export PKG_PATH```
- Hooray this was the hardest part. Https is something I didn't got working, so I stick to http.
- (If you reboot this variable is gone and you have to type it in a shell, a .sh file won't work).

- Hop over to ```su```, your shell variables (PKG_PATH) will persist.
- Type ```pkg_add firefox``` to install the latest nightly of firefox.

# Open a GUI app.
- Open xdm (or use CTRL+ALT+F5 in my case) to hop to the window manager
- Click to open "xterm"
- Then type:
  - firefox
  - xClock
  - (... any other X.org compatible GUI)

# Keeping the system updated
- Perhaps through pkg_add ? Or simply reinstall NetBSD when a new release hits.

# Change brightness
- Perhaps use xBrightness. Sysctl didn't work for my machine.

# Check battery level, will my system die ?
- No need, if the battery is low it will shutdown automatically.

# Shutdown
- Press the power button of you machine once and shortly.


## And the why is this useful ?
I don't really can answer you this.
If you have a working box that is fine, then don't mess around with duo booting.
On the other hand if you have a PC lying around you don't use too much, NetBSD might be useful for you since it does not need much to go onto the internet. 
I kind of hate the procedure that you PC is more busy updating itself than with your actual casual using it.
The less that is customizable, the better for systems that aren't used much in my opinion. So I'm finding out if it is worth it !

I do recommend a quite fast processor, since it isn't as well optimized as for example ChromeOS. YouTube will stutter video frames, but audio seems fine.
Also didn't notice any big issues with the pointer becoming slow, it actually feels more responsive than any other OS.
Don't expect a smooth user experience though! You will get stuck in editors like Vi with a backspace that doesn't work (tip: use ESC + x).
So get ready to read some manuals, because Youtube support for BSD is sparse.
The reason I did undertake it was to checkout what BSD is all about and learn the historics behind computing in general. 
Afterall BSD derivatives can be found in a lot of places !

# Quirks you might encounter too:
- People think your pc is crashing because of all the green letters at boottime.
- xdm isn't self explainatory, things like full screen do not exist.
- if xdm crashes remember the shortcut CTRL+ALT+F1
- Don't use an external display with xdm. Terminals are fine (they simply clone).
- The backspace and delete key do not always work (in ```vi``` for example).
- Touchpad rightclick area hard to use
- Two finger scrolling not working (instead there is 1 finger scrolling).
- No WDDM-like hotkey support (for brightness, volume)
- Laptop lid closing doesn't have any effect
- Fingerprint reader not working
- Really hard to configure things you don't know without the installer GUI.
- No SSL support for the NetBSD website.
- XDM fonts scale different from the other TTY's.
- xterm under xdm doesn't support the arrowUp key.
