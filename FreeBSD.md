## Burning image to USB

I use the NetBSD imager to image an USB flash drive with:
https://download.freebsd.org/ftp/releases/amd64/amd64/ISO-IMAGES/12.1/FreeBSD-12.1-RELEASE-amd64-memstick.img.xz
Make sure to match the SHA256 or SHA512 you see in the GUI of the NetBSD imager with that one on the website:
https://download.freebsd.org/ftp/releases/amd64/amd64/ISO-IMAGES/12.1/CHECKSUM.SHA512-FreeBSD-12.1-RELEASE-amd64

# Boot the target PC from USB
- You know this is always a bit of a game, could take you 1 minute or 15 minutes depending on how quick you can remember all the hidden shortkeys.
- In my case F9 is change boot order, F10 or ESC can get you into the BIOS/EFI to configure
- FreeBSD doesn't like EFI booting from the installer, so I switch mine to "Legacy" in "Boot order" -> Legacy support ON
- Then you need to type some confirmation code saying you changed it.
- FreeBSD shows a red ball logo and will take you to the installer.
- During installation you can press ESC to go back (??) but if you press ESC in the first screen you break the installer (quirk).
- I'm not super sure what the ENTER key does all the time, but I simply went for all default on this one (so just keep pressing enter)
- At the point of WiFi change of region is important here (because of the g/N-channels 12 and 13). https://forums.freebsd.org/threads/what-is-the-correct-regdomain-code.60469/
- I picked ETSI here to see all the WiFi channels
- The WiFi process is quite a no brainer except for the last screen with DNS, but I just clicked ENTER there
- The question about setting the clock to UTC, I had no idea, so press no here.
- Now select a timezone (UTC isn't a timezone, but it is equivalent to UTC+0 timezone I guess.)
- System configuration, (my thought it it writes to /etc/rc.conf where you can undo it)
- Press SPACE for the following:
  - ntpupdate
  - ntpd (because in my experience clock drift is quite a thing)
  - moused (let's see what it does)
  - powerd
- Press ENTER to commit System configuration
- System Hardening, my pc isn't a server so choose what you think is best.
  - Enable password prompt
- Enroll your user account (warning ! if you press enter you can't go back anymore with ESC
- In the last screen you have a nice GUI to install some extra stuff. If you don't here you need to go into the shell manually.
- I fetched the handbook here. 
- Disable Legacy mode from BIOS/EFI didn't work in my case, I also had to disable Secure boot option.
- System boots into a shell.
- The mouse works, but I didn't see anything useful to do with it :)
- Fonts are super small on my machine, no idea how to change it (so get your reading glasses ready)

# Change display brightness
- As root
- ```pkg install xbrightness```
- Doesn't work?

# Edit documents
- as root
- ```pkg install nano```. This allows you to lean onto the keyboard without messing things up (ComputerPhile youtube quote).



# Install webbrowser.
- ```su``` doesn't work for my user. So login as "root" with tha password you made just a few minutes ago.
- pkg install firefox
- Wait till 130 packages are loaded to the machine.
- A lot of console output. I cant scroll the console, So I hope it's fine

# Resolve error "no DISPLAY environment variable specified: 
- ```pkg install x11/kde5```
- If you have 5GB disk space at your disposal go ahead type y to install it.
- I kind of like the drawing app kritta by KDE. You can also try another one:
- https://www.freebsd.org/doc/handbook/x11-wm.html

# Setup KDE after installation
- Add a window manager that also bootstraps the GUI: ```pkg install x11/sddm```
- Following the man page:
- Add this line to /etc/fstab ```proc           /proc       procfs  rw  0   0```
- Add these lines in /etc/rc.conf
```
# x11/kde5
dbus_enable="YES"
hald_enable="YES"
# Window manager x11/sddm
sddm_enable="YES"
```
