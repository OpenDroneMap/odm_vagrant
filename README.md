odm_vagrant
===========

Vagrant machine for using OpenDroneMap, meant primarily for Windows users who want to leverage ODM.

How to use
==========

1. Install VirtualBox ( http://virtualbox.org )
2. Install Vagrant ( http://vagrantup.com )
3. (For Windows and Mac) Install Github ( http://windows.github.com or http://mac.github.com )
4. Copy everything out of the 'user' directory to your user directory ( e.g. c:\users\robertherman\ )
  * This includes: 
      1. 'VirtualBox VMs'
      2. .vagrant.d
      3. .VirtualBox
5. Make a directory c:\users\yourusername\Documents\odm\vagrant_data
6. Copy OpenDroneMap to c:\users\yourusername\Documents\OpenDroneMap
7. Copy 'odm_vagrant' to c:\users\yourusername\Documents\odm\
8. Launch GitHub Command Line
 a. Navigate to vagrant directory.:
 ```
 cd c:\users\yourusername\Documents\OpenDroneMap\
 ```
 b. Type the following in the 
  ```
  vagrant up
  vagrant ssh
  ```

You're in!


