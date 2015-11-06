debian-install
==============

Install directions and scripts for a basic Debian 8 workstation install.

First Steps
-----------

1. Install debian using defaults. Choose LVM and full disk encryption. Use an install CD to avoid having to screw around with renaming the crypt device: http://unix.stackexchange.com/a/81020 (make sure user and root passwords are identical)
2. When tasksel starts, choose only the standard utilities and the ssh server
3. Once the system boots, configure the wireless network, as detailed here: https://wiki.debian.org/WiFi/HowToUse#Command_Line - or maybe not - maybe just hardwire for initial config? If we do configure, we'll have to fix things so the network manager actually works.
4. Make sure to set the proper hosts in the install.yaml, and ansible_user in the host definition.
5. Run the following: ansible-playbook install.yaml --ask-pass --ask-become-pass

Things that are broken
----------------------

* Capslock light doesn't work... looks like this is a longstanding bug on virtual consoles (and not a big deal): http://unix.stackexchange.com/questions/136817/caps-lock-led-not-working-on-linux-console

Things left to install
----------------------

* emacs unstable is no longer installing... :(
  * Depends: libdbus-1-3 (>= 1.9.14) but 1.8.20-0+deb8u1 is installed.
  * Depends: libtinfo5 (>= 6) but 5.9+20140913-1+b1 is installed.
  * https://wiki.debian.org/BuildingFormalBackports
* review: http://feeding.cloud.geek.nz/posts/creating-a-modern-tiling-desktop-environment-using-i3/
* review: http://suckless.org/ http://suckless.org/rocks http://suckless.org/sucks/
* review: https://wiki.archlinux.org/index.php/List_of_applications
* review: https://faq.i3wm.org/question/4517/desktop-programs-to-use-with-i3/
* review: https://news.ycombinator.com/item?id=10134009
* apparmor - this may be interesting: https://help.ubuntu.com/14.04/serverguide/apparmor.html and https://wiki.debian.org/AppArmor/HowToUse
* xterm alternatives (stterm might be worth looking at...) - we need decent copy/paste and a search function

Things left to configure
------------------------

* make sure the script can be run many times
* modify i3bar/i3status to notify me of pending upgrades
* tp_smapi stuff (battery, HDAPS - see: http://www.thinkwiki.org/wiki/Drivers and http://www.thinkwiki.org/wiki/Tp_smapi)
* copy/paste from an xterm - this could be a mess (maybe use a different term?)
* readline keyboard bindings in firefox: http://kb.mozillazine.org/Emacs_Keybindings_%28Firefox%29#GNU.2FLinux
* review: https://www.debian.org/doc/manuals/securing-debian-howto/index.en.html
* configure the network manager to start automatically (globally)
* How can I lock the screen manually? After a delay? (xautolock for automatic - looks like i3lock has a manual setting)
* configure the volume up/down/mute buttons on the keyboard to work - display the volume in the status bar
* should we display the backlight status... or momentarily display it, like mac os? Maybe a status notification?
* automount usb insertions and CDs?

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
* Something like Preview (for viewing PDFs mostly - maybe images)
* Do I need some kind of file explorer? Is the shell enough?
* Some sort of Torrent client
* Something like little snitch
* Something like caffeine
* Something like Postman
* A better twitter client - pidgin is kind of junky for that - or just use the website?
* fan/temp ctrl (and show it in i3status - maybe) (lm-sensors, thinkfan, hddtemp, xsensors, fancontrol, thermald) (thinkpad_acpi does a lot of this already... do we need any of this?)

### Tricky things

* 1Password
  * https://news.ycombinator.com/item?id=10411146
  * http://www.passwordstore.org/

Things Handled by Local Copies
------------------------------

* python - pyenv
* ruby - rvm/rbenv
* emacs packages - package.el
* node - nvm

Ansible Annoyances
------------------

* it would be nice to write a little etckeeper module (or use this: https://github.com/expansible/etckeeper )
* it would be even nicer to fix the problem with the apt module
