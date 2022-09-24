# Installing Drivers

## Teledatics Linux Repository

Teledatics has created a repository that currently supports the Debian and Raspbian operating systems. This repository can be used to automatically install the TD-XPAH Linux drivers.

### Add Repository

Run the following commands to add our GPG key and repository to your system

	wget -O - https://teledatics.com/teledatics.gpg.key | apt-key add -
	echo "deb https://teledatics.com/repos/apt/debian bullseye misc" > /etc/apt/sources.list.d/teledatics-repo.list
	apt update
	
### Installing Drivers

To install the drivers run the following commands

	apt install spi-ft232h-dkms nrc-dkms

This will install and compile the drivers automatically for your system. The drivers will be installed to directory

	/lib/modules/<kernel-version>/updates/dkms

### Loading Drivers

The nrc7292 driver is currently loaded manually. We have included helper scripts that will automatically set the correct parameters when the driver loads. 

To load the nrc7292 driver run the command

	modprobe nrc
		
The spi-ft232h driver loads automatically whenever your TD-XPAH is connected to the system. You do not need to load the spi-ft232h driver manually.

### Unloading Drivers

To unload the nrc7292 driver run the command:

	rmmod nrc
	
Make sure you unload the driver manually *before* you unplug the TD-XPAH from your Linux system.	

