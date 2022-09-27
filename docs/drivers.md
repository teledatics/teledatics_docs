# Installing Drivers

## Teledatics Linux Repository

Teledatics has created a repository that currently supports the Debian and Raspbian operating systems. This repository can be used to automatically install the TD-XPAH Linux drivers.

### Add Repository

Run the following commands to add our GPG key and repository to your system

	sudo wget https://teledatics.com/teledatics.gpg.key -O - | sudo apt-key add -
	sudo echo "deb https://teledatics.com/repos/apt/debian bullseye misc" | sudo tee /etc/apt/sources.list.d/teledatics-repo.list
	sudo apt update
	
### Installing Drivers

To install the drivers run the following commands

	sudo apt install spi-ft232h-dkms nrc-dkms

This will install and compile the drivers automatically for your system. This may take some time on smaller systems.

The drivers will be installed to directory

	/lib/modules/<kernel-version>/updates/dkms

### Loading Drivers
		
The spi-ft232h and nrc drivers load automatically whenever your TD-XPAH is connected to the system. You do not need to load the spi-ft232h or nrc drivers manually.

### Unloading Drivers

To unload the drivers run the command:

	sudo modprobe -r spi-ft232h
	
This will unload both the spi-ft232h and the nrc driver.

Make sure you unload the driver *before* you unplug the TD-XPAH from your Linux system.	


