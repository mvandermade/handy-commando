## Before starting
- Get 2 pc's
- 1 PC to use for manual searching (and keeping this open)
- 1 PC to install FreeBSD onto. This PC will be formatted (you lose all data) in the installation.

## Burning image to USB (Windows 10)

- I use the NetBSD imager (rawrite) to image an USB flash drive: https://www.netbsd.org/~martin/rawrite32/download.html
- Download the zipped image and leave it zipped (rawrite automatically does this)
- https://download.freebsd.org/ftp/releases/amd64/amd64/ISO-IMAGES/12.1/FreeBSD-12.1-RELEASE-amd64-memstick.img.xz
- Insert USB device.
- Open Rawrite32.exe in the downloaded zip.
- Open the .xz file.
- Make sure to match the SHA256 or SHA512 you see in the GUI of the NetBSD imager with that one on the website: https://download.freebsd.org/ftp/releases/amd64/amd64/ISO-IMAGES/12.1/CHECKSUM.SHA512-FreeBSD-12.1-RELEASE-amd64
- Select your USB disk.
- Click write to disk/
- Click yes to erase all data and install freebsd installer on the usb drive.
- If you get an error try formatting the drive to "ExFAT".
- The process is finished when you see : 948.9 MByte successfully written to disk.
- Eject the USB drive.

# Boot the target PC from USB
- You know this is always a bit of a game, could take you 1 minute or 15 minutes depending on how quick you can remember all the hidden shortkeys.
- In my case F9 is change boot order, F10 or ESC can get you into the BIOS/EFI to configure
- "If" FreeBSD doesn't like EFI booting from the installer, so I switch mine to "Legacy" in "Boot order" -> Legacy support ON
"Else" I used another usb drive, and now I can boot from EFI. So booting using "Legacyboot=off" depends on the usb drive in my case.


## Get started with the Installation
- FreeBSD shows a red ball (daemon) logo and will take you to the installer if you press ENTER or wait 10 seconds.
- The installer is simply a dark blue screen with the options "Install", "Shell", "live CD"
- Once you choose an option you can't go back, so you only can go forward.
- You can press "Cancel", it may take you back to the first screen otherwise:
### When you make a mistake.
- You can at any time soft power off the PC by pressing it's power button.
- You will see the shutdown commands through the backdrop.
- It's the best way to correct a mistake during installation.

# Installation itself:
- I did it like this (v12.1):
- "Welcome" choose "Install", ENTER.
- "Keymap selection" -> Continue with default keymap, ENTER.
- "Set hostname", I typed: "laptopp", ENTER.
- "Distribution select", no change, ENTER.
- "Partitioning". Auto (UFS), ENTER.
- "Partitioning". Choose sda0, ENTER.
- "Partition". Choose Entire Disk, ENTER.
- "Confirmation". Yes, ENTER.
- "Partition Scheme". GPT, ENTER.
- "Partition Editor". Finish, ENTER.
- "Confirmation". "Commit", ENTER.
- Now the installation starts. You can relax for a bit while the PC organizes all files.
- When you get a black screen (text based shell) it's time for Setting up

## Installation, Setting up
- Choose root password. Root is for installing files and such so keep it private.
- Blue screen "Network configuration", ENTER.
If you have a WiFi card:
- "Regdomain/Country. Yes, ENTER.
- "ETSI". OK, ENTER. https://forums.freebsd.org/threads/what-is-the-correct-regdomain-code.60469/
- "Country". Use arrow keys to select your country, ENTER.
- "Network selection". Use arrow keys and ENTER.
- "Wifi setup". Enter passphrase, ENTER.
- ipv4. YES, ENTER.
- Configure DHCP, ENTER.
- ipv6. YES, ENTER.
- SLAAC. YES, ENTER. https://howdoesinternetwork.com/2013/slaac
- "Sending router sollicitation..." Wait.
- "Network configuration", ENTER.
- "Select local or UTC (Greenwich Mean Time) clock" -> NO enter
- "Time Zone Selection" Use arrow keys and ENTER to choose your TimeZone.
- "Time & Date". If it looks OK, hit ENTER at "Skip" (you can always change it later).
- "System configuration". Choose what you like using SPACEBAR. You can change these things using `vi /etc/rc.conf`. The more options you select, the slower startup time since these commands are executed in sequence.
- "System hardening". Choose options using SPACE, confirm on OK, ENTER.
- "Add User Accounts". ->YES, ENTER.
- Go through the different options a user can choose.
- "Final configuration". ->Exit, ENTER.
- "Manual Configuration". ->NO, ENTER.
- "Complete". ->Reboot ENTER.
- System boots into a shell.
- Fonts are small on my machine, (so get your reading glasses ready) 
- To enlarge fonts people recommend: https://www.freebsd.org/cgi/man.cgi?query=vidcontrol&sektion=1&manpath=freebsd-release-ports (i didn't figure it out yet...)

# Install Xorg
https://www.freebsd.org/doc/handbook/x-install.html
- Login as root
- pkg install xorg

# Install X Display Manager
https://www.freebsd.org/doc/handbook/x-xdm.html
- Login as root
- pkg install x11/xdm

# Install Gnome3
- Login as root.
- type: pkg install gnome3
- Question package manager not installed. Type y, ENTER. 500 packages for Gnome3. press y, ENTER.
- Take a good pause, takes around 15-30 minutes to download and install.

## Configuring Gnome3:
https://www.freebsd.org/doc/handbook/x11-wm.html

mount /proc at boot:
Add this line to /etc/fstab
The identation should be equal to the existing entries.
```
proc           /proc       procfs  rw  0   0
```

Install graphics card driver (otherwise you get an error when typing startx) https://forums.freebsd.org/threads/new-to-freebsd-startx-fails-with-cannot-run-in-framebuffer-mode-help.68882/
```
pkg install graphics/drm-kmod
```

I added the following to rc.conf to make Gnome boot.

```
# Enable mouse
moused_enable="YES"
# Graphics
kld_list="/boot/modules/i915kms.ko"
# GNOME dependencies
dbus_enable="YES"
hald_enable="YES"
# Boot GNOME using gdm
gdm_enable="YES"
# Boot GNOME services
gnome_enable="YES"
```

# Change brightness (works freeBSD wide)
- ```kldload acpi_video``` https://forums.freebsd.org/threads/how-to-change-brightness-with-fn-key.51987/
- To persist boot:
- as root: ```sysrc kld_list+=acpi_video``` which will append the command to /etc/rc.conf
- Reboot
- Use the hotkeys on your keyboard to change brightness. Note it's verrry small increments, so hold the keys a long time!

## Touchpad
- enable moused in your /etc/rc.conf ```moused_enable="YES"```
- add to /boot/loader.conf ```hw.psm.synaptics_support="1"```
- Bit strange behaviour when tapping with two fingers, but I kind of living with it now.

# Quirks
- No software manager installed
- Cannot change two finger tap = right click

# Compliment
- Gnome does detect the touchpad and it works nice