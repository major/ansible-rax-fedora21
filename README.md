### Test Fedora 21 on the Rackspace Cloud

***DEPRECATED:*** *This repository really isn't needed any longer since Rackspace has a Fedora 21 image ready to go today.*

This small ansible playbook will take a Fedora 20 instance on Rackspace Cloud and upgrade it to Fedora 21 (currently in Alpha at the time of this writing).  It takes 7-9 minutes to run and provides you with a minimal installation of Fedora 21 for testing, or if you're brave, production use.

##### Getting started
Ensure that you [have ansible installed](http://docs.ansible.com/intro_installation.html) on your system.  (That's outside the scope of these instructions.)

1. Build a Cloud Server (a small 1GB server works fine).
2. Replace `example.com` in hosts.yml with your Cloud Server's IP address.
3. Run the playbook: `ansible-playbook -i hosts.yml playbook.yml`

##### Behind the scenes
The playbook automates these tasks for you:

1. Install prerequisites in Fedora 20 and update all packages
2. Switch bootloaders from extlinux to grub2
3. Download Fedora 21 upgrade packages and then install them (long step)
4. Reboots and relabels SELinux contexts during reboot (long step)
5. Waits for server to come back and verifies that Fedora 21 is installed

**PLEASE DON'T USE THIS ON A PRODUCTION SYSTEM YOU CARE ABOUT!**

Fedora 21 is still in development and this ansible playbook is also pretty basic.  Only use this playbook on servers that you plan to use for testing Fedora 21.
