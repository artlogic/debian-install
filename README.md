debian-install
==============

Install directions and scripts for a basic Debian 7 workstation install.

First Steps
-----------

1. Install debian using defaults. Choose LVM and full disk encryption.
2. When tasksel starts, choose only the standard utilities and the ssh server.
3. Once the system boots, find and install the missing recommended packages, marking them as automatically installed, using first `aptitude search '~RBrecommends:~i'`, and then `aptitude install [package]` and `aptitude markauto [package]`.
4. Next up, ansible!

Some Things I Use/Need
----------------------

* Emacs
* screen/tmux
* git
* nodejs
* Maybe zsh (time to switch?)

### Xorg

* Balsamiq Mockups (for Xorg - requires Adobe Air)
* Calibre
* Dropbox
* Pidgin
* Skype
* Firefox (iceweasel)
* Flux
* Gimp
* Chromium
* LibreOffice

Things Handled by Local Copies
------------------------------

* python - pyenv
* ruby - rvm/rubyenv
* emacs packages - package.el

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
