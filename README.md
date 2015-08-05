debian-install
==============

Install directions and scripts for a basic Debian 8 workstation install.

First Steps
-----------

1. Install debian using defaults. Choose LVM and full disk encryption. Use an install CD to avoid having to screw around with renaming the crypt device: http://unix.stackexchange.com/a/81020
2. When tasksel starts, choose only the standard utilities and the ssh server
3. Once the system boots, configure the wireless network, as detailed here: https://wiki.debian.org/WiFi/HowToUse#Command_Line
4. Make sure to set the proper hosts and user in the install.yaml
5. Run the following: ansible-playbook install.yaml --ask-pass --ask-become-pass

Things that are broken
----------------------

* Capslock light doesn't work... looks like this is a longstanding bug on virtual consoles: http://unix.stackexchange.com/questions/136817/caps-lock-led-not-working-on-linux-console

Some Things I Use/Need
----------------------

* Emacs
* screen/tmux
* git
* Maybe zsh (time to switch?)
* ectkeeper
* apticron
* swap caps & ctrl (easy to do using /etc/default/keyboard)
* fan and temperature control (and HD spindown for now... tho I will be upgrading to an SSD)
* sleep/hibernate on lid close (this might work - test)
* using the mouse from the terminal? maybe?
* battery meter

### What if I try and run everything from the command line?

tmux would need the following meters (a status bar, like byobu):

* battery
* time
* mail/message notifications (How would this work with IMs?)

Apps I'd like/need to have:

* Dropbox works from the command line, sort of...
* IM / Twitter
* Mail client - lots of command line options
* a web browser
* something to easily connect ot new wireless networks

things I wouldn't be able to do:

* mockups, graphics editing, design
* ebooks
* skype
* flux (sadly... tho this might be easily remedied)
* modern web browsers
* document editing (office-ish docs - and spreadsheets - got to be a replacement for those!)

open questions:

* would I listen to music from the command line?
* skype is basically dead - other options?
* 1password - isn't there a gnu password manager?

### Xorg

* Balsamiq Mockups (for Xorg - requires Adobe Air)
* Calibre
* Dropbox
* Pidgin (with twitter plugin, or twitter client)
* Skype
* Firefox (iceweasel)
* Flux
* Gimp
* Chromium
* LibreOffice

Things Handled by Local Copies
------------------------------

* python - pyenv
* ruby - rvm/rbenv
* emacs packages - package.el
* node - nvm

Things I Need, but not by Name
------------------------------

* Terminal Emulator (for Xorg)
* Something like xScope
* Something to Play Music (iTunes library sharing compatible)
* Email? Some sort of a browser frame?
* Something like Preview
* Some sort of Torrent client
* Tiling Window Manager
* Display Manager
* Search Based Launcher
* Dock/Launcher
* Battery Meter
* Audio Controls
* Network Controls
* Multiple Desktops
* Notifications

Tricky Things
-------------

* 1Password
