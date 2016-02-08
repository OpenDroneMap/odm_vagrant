odm_vagrant
===========

Vagrant machine for using OpenDroneMap, meant primarily for Windows users who want to leverage ODM.

How to Install and Test
========================

1. Install VirtualBox ( http://virtualbox.org )
2. Install Vagrant ( http://vagrantup.com )
3. Install Github for Windows or Mac OS ( http://windows.github.com or http://mac.github.com )
4. Clone the odm_vagrant repository ( https://github.com/OpenDroneMap/odm_vagrant ) to your local machine.
5. Make a main install directory for the OpenDroneMap installation c:\users\yourusername\Documents\odm\
6. Copy your cloned 'odm_vagrant' directory to c:\users\yourusername\Documents\odm\
7. Launch GitHub Command Line (Start Menu->GitHub Inc->Git Shell)
8. Navigate to the odm_vagrant directory and install the guest operating system ( commands in the boxes below should be typed into the command line ):

  ```
  cd c:\users\yourusername\Documents\odm\odm_vagrant\
  mkdir ..\vodm_data
  vagrant up
  vagrant ssh
  ```
In Windows you will have the vodm_data directory you just created, in the GNU/Linux environment used below, that directory will be called vagrant_data, they are the same directory<br><br>
You have now installed, launched and logged in to an Ubuntu GNU/Linux OS on your Windows machine. The following commands are all standard Ubuntu GNU/Linux commands.

9. Clone the sample imagery repository https://github.com/OpenDroneMap/odm_data.git

  ```
  sudo apt-get -y install git
  cd /vagrant_data/
  git clone --recursive https://github.com/OpenDroneMap/odm_data.git
  ```

10. Clone the OpenDroneMap application repository  https://github.com/OpenDroneMap/OpenDroneMap.git

  ```
  sudo mkdir /odm_app
  sudo chown vagrant:vagrant /odm_app/
  cd /odm_app/
  git clone https://github.com/OpenDroneMap/OpenDroneMap.git
  ```

11. Install the OpenDroneMap software:

  ```
  cd /odm_app/OpenDroneMap/
  ./install.sh
  ```
Wait patiently, on a typical desktop machine ODM App installation will take about 20 minutes.

12. Run the OpenDroneMap App on the an odm_data test dataset.

  ```
  cd /vagrant_data/odm_data/pacifica/
  /odm_app/OpenDroneMap/run.py
  ```
Wait patiently again, this will take about the same amount of time as the install proceedure.<br>
Outputs will be in:<br>
/vagrant_data/odm_data/pacifica/reconstruction-with-image-size-1200<br>
and<br>
/vagrant_data/odm_data/pacifica/reconstruction-with-image-size-1200-results<br>
In your Windows host, these will be at c:\users\yourusername\Documents\odm\vodm_data\odm_data\pacifica\

13. If you are done processing imagery datasets, you can logout and shutdown the virutal machine.

  ```
  sudo shutdown now
  ```
To enter the ODM environment again, repeat steps 7, 8 (but don't make the vodm_data directory a second time) Step 12 is all you need to do to run the software on another imagery dataset.

---

Install MeshLab 1.3.3 or later on your Windows host. Then...

From Meshlab 1.3.3:

	* Open Project file, navigate to:
		* c:\users\yourusername\Documents\odm\vodm_data\odm_data\pacifica\reconstruction-with-image-size-1200\bundle\bundle.out
	* It will prompt for the image list file
		* c:\users\yourusername\Documents\odm\vodm_data\odm_data\pacifica\reconstruction-with-image-size-1200\list.txt
	* Control-L and delete "0 model"
	* Import dense point cloud:
		* e.g. c:\users\yourusername\Documents\odm\vodm_data\odm_data\pacifica\reconstruction-with-image-size-1200-results\option-0000.ply
		* (there may be multiple ply files)
	* Make a mesh:
		* Filters:Remeshing, Simplification and Reconstruction:Surface Reconstruction Poisson
	* Texture the mesh
		* Parameterization + texturing from registered rasters

Celebrate. Now try your own dataset. If you don't have one, saunter over to http://www.publiclab.org/ for DIY balloon advice, or get yourself a nifty quad copter with a commodity camera (preferably not a GoPro for now until we have a routine to calibrate those). Aim for 70-80% overlap between your photos.
