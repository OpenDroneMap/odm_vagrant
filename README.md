odm_vagrant
===========

Vagrant machine for using OpenDroneMap, meant primarily for Windows users who want to leverage ODM.

How to use
==========

1. Install VirtualBox ( http://virtualbox.org )
2. Install Vagrant ( http://vagrantup.com )
3. (For Windows and Mac) Install Github ( http://windows.github.com or http://mac.github.com )
4. Make a directory c:\users\yourusername\Documents\odm\vagrant_data
5. Copy 'odm_vagrant' to c:\users\yourusername\Documents\odm\
6. Launch GitHub Command Line
 * Navigate to vagrant directory.:

 ```
 cd c:\users\yourusername\Documents\OpenDroneMap\
 ```
 * Type the following in the command line

  ```
  vagrant up
  vagrant ssh
  ```

7. Clone zip of https://github.com/OpenDroneMap/OpenDroneMap.git and https://github.com/OpenDroneMap/odm_data.git

  ```
  cd /vagrant_data/
  sudo apt-get install git
  git clone https://github.com/OpenDroneMap/OpenDroneMap.git
  git clone https://github.com/OpenDroneMap/odm_data.git
  ```

8. Install:

  ```
  cd /vagrant_data/OpenDroneMap
  ./install.sh
  ```

Wait patiently...
Now let us run OpenDroneMap on our test dataset.

```
cd /vagrant_data/odm_data
/vagrant_data/OpenDroneMap/./run.pl
```

Wait patiently again...

Outputs will be in /vagrant_data/odm_data/reconstruction-with-image-size-1200 and /vagrant_data/odm_data/reconstruction-with-image-size-1200-results .

In your Windows host, these will be at c:\users\yourusername\Documents\odm\vagrant_data\odm_data\reconstruction-with-image-size-1200

---

Install MeshLab 1.3.3 or later on your Windows host. Then...

From Meshlab 1.3.3:

	* Open Project file, navigate to:
		* c:\users\yourusername\Documents\odm\vagrant_data\odm_data\reconstruction-with-image-size-1200\reconstruction-with-image-size-1200\bundle\bundle.out
	* It will prompt for the image list file
		* c:\users\yourusername\Documents\odm\vagrant_data\odm_data\reconstruction-with-image-size-1200\reconstruction-with-image-size-1200\list.txt
	* Control-L and delete "0 model"
	* Import dense point cloud:
		* e.g. c:\users\yourusername\Documents\odm\vagrant_data\odm_data\reconstruction-with-image-size-1200\reconstruction-with-image-size-1200-results\option-0000.ply
		* (there may be multiple ply files)
	* Make a mesh:
		* Filters:Remeshing, Simplification and Reconstruction:Surface Reconstruction Poisson
	* Texture the mesh
		* Parameterization + texturing from registered rasters

Celebrate.
