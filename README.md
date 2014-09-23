odm_vagrant
===========

Vagrant machine for using OpenDroneMap, meant primarily for Windows users who want to leverage ODM.

How to use
==========

1. Install VirtualBox ( http://virtualbox.org )
2. Install Vagrant ( http://vagrantup.com )
3. (For Windows and Mac) Install Github ( http://windows.github.com or http://mac.github.com )
4. Make a directory c:\users\yourusername\Documents\odm\vagrant_data
5. Copy OpenDroneMap into c:\users\yourusername\Documents\odm\vagrant_data\
   * This will put OpenDroneMap into a directory shared by the host and virtual machine
6. Copy directory of photos (e.g. PacificaPhotos) you want to process to c:\users\yourusername\Documents\odm\vagrant_data\
7. Copy 'odm_vagrant' to c:\users\yourusername\Documents\odm\
8. Launch GitHub Command Line
 * Navigate to vagrant directory.:
 ```
 cd c:\users\yourusername\Documents\OpenDroneMap\
 ```
 * Type the following in the command line
  ```
  vagrant up
  vagrant ssh
  ```

You're in!

```
cd /vagrant_data/OpenDroneMap
./install.sh
```
Wait patiently...

```
cd /vagrant_data/PacificaPhotos
../OpenDroneMap/./run.pl
```
Wait patiently again...

Outputs will be in /vagrant_data/PacificaPhotos/reconstruction-with-image-size-1200 and /vagrant_data/PacificaPhotos/reconstruction-with-image-size-1200-results .

In your Windows host, these will be at c:\users\yourusername\Documents\odm\vagrant_data\PacificaPhotos\reconstruction-with-image-size-1200
