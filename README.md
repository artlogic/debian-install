debian-install
==============

Install directions and scripts for a basic Debian 8 workstation install.

First Steps
-----------

1. Install debian using defaults. Choose LVM and full disk encryption. Use an install CD to avoid having to screw around with renaming the crypt device: http://unix.stackexchange.com/a/81020
2. When tasksel starts, choose only the standard utilities and the ssh server
3. Once the system boots, configure the wireless network, as detailed here: https://wiki.debian.org/WiFi/HowToUse#Command_Line - or maybe not - maybe just hardwire for initial config? If we do configure, we'll have to fix things so the network manager actually works.
4. Make sure to set the proper hosts and remote_user in the install.yaml
5. Run the following: ansible-playbook install.yaml --ask-pass --ask-become-pass

Things that are broken
----------------------

* Capslock light doesn't work... looks like this is a longstanding bug on virtual consoles (and not a big deal): http://unix.stackexchange.com/questions/136817/caps-lock-led-not-working-on-linux-console

Things to test
--------------

* sleep/hibernate on lid close (this might work - test)

Things left to install
----------------------

* emacs - create a backport? install from source? or https://www.debian.org/doc/manuals/debian-handbook/sect.apt-get.en.html#sect.apt-mix-distros
* apparmor - this may be interesting: https://help.ubuntu.com/14.04/serverguide/apparmor.html and https://wiki.debian.org/AppArmor/HowToUse
* pidgin: pidgin, pidgin-awayonlock, pidgin-libnotify, pidgin-otr, pidgin-twitter
* f.lux: https://justgetflux.com/linux.html
* volume controls (alsa?)
* Install the stuff to do fan/temp ctrl (and show it in i3status - maybe)

Things left to configure
------------------------

* Swap caps and ctrl (using /etc/default/keyboard)
* modify i3bar/i3status to notify me of pending upgrades
* tp_smapi stuff (battery, HDAPS - see: http://www.thinkwiki.org/wiki/Drivers and http://www.thinkwiki.org/wiki/Tp_smapi)
* copy/paste from an xterm - this could be a mess (maybe use a different term?)
* readline keyboard bindings in firefox: http://kb.mozillazine.org/Emacs_Keybindings_%28Firefox%29#GNU.2FLinux
* review: https://www.debian.org/doc/manuals/securing-debian-howto/index.en.html
* configure the network manager to start automatically (globally)

Things I use now, but I'm going to wait until I need them
---------------------------------------------------------

* Balsamiq Mockups (for Xorg - requires Adobe Air)
* Calibre
* Dropbox
* Skype
* Gimp
* Chromium
* LibreOffice

### Things I use, but not by name

* Something like xScope
* Something to Play Music (iTunes library sharing compatible)
* Email? Some sort of a browser frame? A client? Mutt? Emacs?
* Something like Preview (for viewing PDFs mostly - maybe images)
* Do I need some kind of file explorer? Is the shell enough?
* Some sort of Torrent client

### Tricky things

* 1Password

Things Handled by Local Copies
------------------------------

* python - pyenv
* ruby - rvm/rbenv
* emacs packages - package.el
* node - nvm
