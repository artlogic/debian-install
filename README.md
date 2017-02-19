debian-install
==============

Install directions and scripts for a basic Debian 8 workstation install.

Goals
-----

1. Keep GNOME, and other resource hungry complex things out of the mix.
2. Unix philosophy FTW.
3. Only install what's needed.

First Steps
-----------

1. Install debian using defaults. Choose LVM and full disk encryption. Make sure user and root passwords are identical.
2. When tasksel starts, choose only the standard utilities and the ssh server
3. Once the system boots, configure the wireless network, as detailed here: https://wiki.debian.org/WiFi/HowToUse#Command_Line - or maybe not - maybe just hardwire for initial config? If we do configure, we'll have to fix things so the network manager actually works... actually, just do everything hardwired, but then comment out eth0 in /etc/network/interfaces after the install is complete.
4. Rename the crypt device (it'll be sdb, should be sda): http://unix.stackexchange.com/a/81020 - this seems to have been fixed.
5. Make sure to set the proper hosts in the preinstall.yaml and install.yaml, and ansible_user in the host definition.
6. Run the following:
  1. ansible-playbook preinstall.yaml --ask-pass --ask-become-pass
  2. ansible-playbook install.yaml --ask-pass --ask-become-pass

Things that are broken
----------------------

* Capslock light doesn't work... looks like this is a longstanding bug on virtual consoles (and not a big deal): http://unix.stackexchange.com/questions/136817/caps-lock-led-not-working-on-linux-console - since I plan to be in X, not an issue

Things left to install
----------------------

* Non-blocking (future):
  * maybe switch to source code pro: https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=736681

Things left to configure
------------------------

### System

* Non-blocking (future):
  * get devmon (udisks2, udevil) running as a service, and notifications of mounts would be nice (pull from backports?)
    * https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=799745
    * devmon should probably have it's own user (group plugdev) to start the service
  * tp_smapi stuff (battery, HDAPS - see: http://www.thinkwiki.org/wiki/Drivers and http://www.thinkwiki.org/wiki/Tp_smapi - it could be TLP takes care of this)
  * review: https://www.debian.org/doc/manuals/securing-debian-howto/index.en.html
  * apparmor - this may be interesting: https://help.ubuntu.com/14.04/serverguide/apparmor.html and https://wiki.debian.org/AppArmor/HowToUse - currently very few apps have profiles
  * Look into GRUB 2 and LUKS support
  * Talk w/ Rob about backporting emacs 25
  * Multi-head support seems sketchy, or at least very manual... xrandr works, but could be more automatic - research is needed.
  * lightdm is taking care of the desktop background - but doesn't seem to work well with disparate resolutions and multi-head. It could be we need feh or nitrogen.
  * look into using the fingerprint reader - just for fun maybe?

### User

User config will be either a separate playbook or a separate repo entirely (review because some of these may be global)

* configure the network manager to start automatically (this might already be happening?): https://faq.i3wm.org/question/2155/how-can-i-use-autostart-desktop-files-in-i3.1.html
* modify i3bar/i3status to notify me of pending upgrades (dotfiles)
* terminal config (colors, copy/paste, etc...) https://wiki.archlinux.org/index.php/Rxvt-unicode
* How can I lock the screen manually? After a delay? (xautolock for automatic - looks like i3lock has a manual setting)
* configure the volume up/down/mute buttons on the keyboard to work - display the volume in the status bar
* should we display the backlight status... or momentarily display it, like mac os? Maybe a status notification?
* make sure the screen locks on suspend/hibernate
* ssh agent?

### Optional

* It may be a good idea to mark automatically installed dependencies that I'd prefer to not be nuked as intentionally installed (e.g. git)

Things I use now, but I'm going to wait until I need them
---------------------------------------------------------

* Balsamiq Mockups (for Xorg - requires Adobe Air)
* Calibre
* Dropbox (replace with syncthing/owncloud?)
* Skype (shouldn't any VoIP client work?)
* Gimp
* Chromium
* LibreOffice
* Slack (is there a Linux client? or just use the website)
* pidgin-awayonlock (is there a version that works *without* gnome-screensaver?)

### Things I use, but not by name

* Something like xScope
* Something to Play Music (iTunes library sharing compatible)
* Email? Some sort of a browser frame? A client? Mutt? Emacs?
* Something like Preview (for viewing PDFs mostly - maybe images - keep `less` in mind)
* Do I need some kind of file explorer? Is the shell enough?
* Some sort of Torrent client
* Something like little snitch
* Something like caffeine
* Something like Postman (REST client)
* A better twitter client - pidgin is kind of junky for that - or just use the website?
* fan/temp ctrl (and show it in i3status - maybe) (lm-sensors, thinkfan, hddtemp, xsensors, fancontrol, thermald) (thinkpad_acpi does a lot of this already... do we need any of this?)
* review: http://feeding.cloud.geek.nz/posts/creating-a-modern-tiling-desktop-environment-using-i3/
* review: http://suckless.org/ http://suckless.org/rocks http://suckless.org/sucks/
* review: https://wiki.archlinux.org/index.php/List_of_applications
* review: https://faq.i3wm.org/question/4517/desktop-programs-to-use-with-i3/
* review: https://news.ycombinator.com/item?id=10134009
* review: https://news.ycombinator.com/item?id=10565605
* Review: https://news.ycombinator.com/item?id=10644690
* Review: http://joaquinlp.me/blog/your-guide-to-a-damn-light-arch-linux-with-i3-and-text-apps/

### Tricky things

* 1Password
  * https://news.ycombinator.com/item?id=10411146
  * http://www.passwordstore.org/
  * http://keepass.info/

Ansible Annoyances
------------------

* it would be nice to write a little etckeeper module (or use this: https://github.com/expansible/etckeeper )
