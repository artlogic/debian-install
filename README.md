debian-install
==============

Install directions and scripts for a basic Debian 7 workstation install.

First Steps
-----------

1. Install debian using defaults. Choose LVM and full disk encryption.
2. When tasksel starts, choose only the standard utilities and the ssh server.
3. Once the system boots, find and install the missing recommended packages, marking them as automatically installed, using first `aptitude search '~RBrecommends:~i'`, and then `aptitude install [package]` and `aptitude markauto [package]`.
4. Next up, ansible!
