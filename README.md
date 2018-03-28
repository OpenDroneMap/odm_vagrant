odm_vagrant
===========

**Please refer to https://docs.opendronemap.org for instructions on how to install ODM. Vagrant is no longer supported**

Vagrant machine for using OpenDroneMap, meant primarily for Windows users who want to leverage ODM.

How to Install and Test
========================

1. Install VirtualBox ( http://virtualbox.org )
2. Install Vagrant ( http://vagrantup.com )
3. Install Github for Windows or Mac OS ( https://desktop.github.com/ )
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
In Windows, you will have the vodm_data directory you just created, in the GNU/Linux environment used below, that directory will be called vagrant_data, they are the same directory<br><br>
You have now installed, launched and logged in to an Ubuntu GNU/Linux OS on your Windows machine. The following commands are all standard Ubuntu GNU/Linux commands.

9. If you don't have your own data, clone some sample imagery from our repository https://github.com/OpenDroneMap/odm_data.git. This could take a while, so it might be better so pick and choose. 

  ```
  sudo apt-get -y install git
  cd /vagrant_data/
  git clone https://github.com/OpenDroneMap/odm_data_bellus.git
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
  bash configure.sh
  mkdir build && cd build && cmake .. && make && cd ..
  ```
Wait patiently, on a typical desktop machine ODM App installation will take about 20 minutes.

12. (optional) With your favorite editor, add the following to your `~/.bashrc` file:

  ```
  export PYTHONPATH=$PYTHONPATH:/odm_app/OpenDroneMap/SuperBuild/install/lib/python2.7/dist-packages:/odm_app/OpenDroneMap/SuperBuild/src/opensfm
  export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/odm_app/OpenDroneMap/SuperBuild/install/lib
  ```
You'll need to logout and back in again if you do this.

13. Run the OpenDroneMap App on an odm_data test dataset (or your own).

  ```
  ./run.sh --project-path /vagrant_data/odm_data_bellus/
  ```
Wait patiently again, this will take some time.<br>
Outputs will be in:<br>
/vagrant_data/odm_data_bellus/<br>
In your Windows host, these will be at c:\users\yourusername\Documents\odm\vodm_data\odm_data_bellus

14. If you are done processing imagery datasets, you can logout and shutdown the virutal machine.

```
sudo shutdown now
```
To enter the ODM environment again, repeat steps 7, 8 (but don't make the vodm_data directory a second time) Step 13 is all you need to do to run the software on another imagery dataset.

---

Install MeshLab 1.3.3 or later on your Windows host. Then...

From Meshlab 1.3.3:

	* Import dense point cloud:
		* e.g. c:\users\yourusername\Documents\odm\vodm_data\odm_data_bellus\pmvs\recon0\models\option-0000.ply
		* (there may be multiple reconX folders)
	* Mesh: 
		* c:\users\yourusername\Documents\odm\vodm_data\odm_data_bellus\odm_meshing\odm_mesh.ply
	* Textured Mesh:
		* c:\users\yourusername\Documents\odm\vodm_data\odm_data_bellus\odm_texturing\odm_textured_model.obj
	* Orthophoto:
		* c:\users\yourusername\Documents\odm\vodm_data\odm_data_bellus\odm_orthophoto\odm_orthophoto.tif

Celebrate. Now try your own dataset. If you don't have one, saunter over to http://www.publiclab.org/ for DIY balloon advice, or get yourself a nifty quad copter with a commodity camera (preferably not a GoPro for now until we have a routine to calibrate those). Aim for 70-80% overlap between your photos.
