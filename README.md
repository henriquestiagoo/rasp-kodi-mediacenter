# Raspberry Pi Kodi Mediacenter

Equipament
---------------------------
* Raspberry Pi
* Raspberry Pi Power Supply
* HDMI Cable
* Micro SD Card
* Raspberry Pi Case (Optional)
* Generic Remote Control (Optional)

LibreELEC/OpenELEC Install
---------------------------

* Download libreELEC/OpenELEC image according the rasp version: https://libreelec.tv/downloads/
* Unzip libreELEC/OpenELEC image
* Write the image on the sd card. [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/) is a good solution. 
* Place the card on the raspberry pi card slot

HDMI-CEC
---------------------------

To enable libreELEC/OpenELEC support (for remote control), go to:
    
    System > System definitions > Input > Peripherals > HDMI-CEC/CEC Adapter (enable)
 
 You can now use a generic remote control to navigate through Kodi menus.
    
Network configuration
---------------------------

To connect to a network, go to:
   
    System > Libre/OpenELEC > Networks
    
Enter the network credentials if required. If you want to configure a static ip address, choose `manual` the type of ip address method and add a valid ip network address. 

Repositories configuration
---------------------------

The repositories will give access to add-ons that aren't available on the official repositories. There's a step required to be able to install add-ons from unknown sources. Go to:

    System > System Definitions > Add-ons > and activate > Unknown sources
    
From now on, you can add whatever repository you want. When you found a repository you want to install, go to:

    System > Files manager > Add source > (enter url and choose a name to that repo) > Add files source
    
Now you have to go to:

    Add-ons > Install from a zip file (and select the source by the name you specified earlier)
    

Plexus (Acestream streams):
---------------------------

* Install Plexus add-on on raspberry pi
* Enable ssh
* Install [PuTTY](http://www.putty.org/) on your pc. You will need to access your rasp remotely through the pc. For that, you need to know what's the rasp ip address. If you haven't configured a static ip address or don't remember the rasp ip, go to `System > System info > (check ip address)` to check th rasp ip address.   

After installing puTTY (on local machine), remotely access to your pi placing the Pi ip address in Host Name and the number 22 in the port.
Username and passwords can be different depending the OS. Check below what credentials to use:

OSMC:
username: osmc
password: osmc

OpenELEC:
username: root
password: openelec

LibreELEC:
username: root
password: libreelec

Them you must enter the following commands:

    $ cd ~/.kodi/userdata/addon_data/program.plexus
    $ sudo rm -r acestream
    $ wget https://dl.bintray.com/pipplware/dists/unstable/armv7/misc/acestream_rpi_3.1.5.tar.gz
    $ tar xfv acestream_rpi_3.1.5.tar.gz
 
Note: When using OpenELEC or LibreELEC OS's, you have to remove the `sudo` on the second line. So the command is:
    
    rm -r acestream
    
Reboot the system and you should now be able to watch acestream content :)
