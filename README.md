# HomeMediaServer

## Media server running on raspberry pi 4 via CasaOS.

**Install casaOS:**

      curl -fsSL https://get.casaos.io | sudo bash

### **Apps:** 

#### 01. AdGuardHome

      webUI Port = 3000

#### 02. JDownloader

Docker Image URL:  
      
      jaymoulin/jdownloader:latest  

logo:  

      https://icon.casaos.io/main/all/jdownloader.png  

Ports:

      webUI port = 3129
      Port = 3129:3129

Environment Variables:

    MYJD_USER = username  
    MYJD_PASSWORD = password  
    MYJD_DEVICE_NAME = device name  

Volumes:  

> Choose a download path for JDownloader  

    /XXXX/XXXX/XXXX:/opt/JDownloader/Downloads 
    /DATA/AppData/JDownloader/cfg:/opt/JDownloader/cfg  

Commands:  

    /opt/JDownloader/daemon.sh

#### 03. Jellyfin  

##### V4L2 (Raspberry Pi)  

> Hardware acceleration users for Raspberry Pi V4L2 will need to mount their /dev/video1X devices inside of the container by passing the following options when running or creating the container: 

    --device=/dev/video10:/dev/video10
    --device=/dev/video11:/dev/video11
    --device=/dev/video12:/dev/video12  

#### 04. Lidarr  

#### 05. my-JD(weblink for my.jdownloader)  

URL:  

      https://my.jdownloader.org/  

Logo:  

      https://icon.casaos.io/main/all/jdownloader.png  

#### 06. OpenSpeedTest  

#### 07. OpenVPN  

Install OpenVPN.

    apt instal openvpn

Change to OpenVPN directory, download and unzip OpenVPN config files. 

    cd etc/openvpn 

Download the PIA VPN config files.

    sudo wget https://www.privateinternetaccess.com/openvpn/openvpn.zip

Install Unzip. Download and decompress the VPN files (PIA).  

    apt install unzip

    sudo unzip openvpn.zip

Copy one of the ????.ovpn files as openvpn config file.

    sudo cp ????.ovpn pia-??.conf

Edit the config file.
> Change auth-user-pass to: auth-user-pass login.conf  
    
    sudo vi pia-??.conf

Create a login.conf file and put in credentials.
> usernamePIA  
> passwordPIA

    sudo vi login.conf

Change permissions to root read-only.

    sudo chmod 400 login.conf

Configure OpenVPN to start on boot.

> Uncomment and add the config file name. 

    sudo vi /etc/default/openvpn

>

    AUTOSTART="pia-??"
    
Check current ip address.    

    curl ifconfig.me

#### 08. Prowlarr  

#### 09. qBittorrent  

#### 10. Radarr  

#### 11. Sonarr  

#### 12. UpTimeKuma   

### **Additional Setup:**

#### Running RPi OS Lite 64-Bit

#### Update and upgrade

     sudo apt update && sudo apt upgrade

#### Mounting the disks/partitions with the correct permissions  

To view disks/partitions.

     sudo fdisk -l
     lsblk
     blkid

To auto-mount external drives and partitions on boot, append **fstab**.  
    
    sudo nano /etc/fstab  

> */dev/???? for partitions; PARTUUID for disks*  

    /dev/???? /home/pi/ssd exfat defaults,uid=1000,gid=1000 0 0 


#### Last reboot/startup information
    
    less /var/log/messages | grep Booting
    
#### Schedule daily reboots

To schedule a reboot, append **crontab**
 
    sudo crontab -e

This schedules a reboot every day at 6 am.

    0 6 * * * /sbin/shutdown -r now

#### Change user to superuser
      
      sudo -s
