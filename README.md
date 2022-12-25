# HomeMediaServer

## Media server running on raspberry pi 4 via CasaOS.

### Apps: 

#### 01. AdGuardHome

  > Port:3000;3000

#### 02. JDownloader

#### 03. Jellyfin

##### V4L2 (Raspberry Pi)

> Hardware acceleration users for Raspberry Pi V4L2 will need to mount their /dev/video1X devices inside of the container by passing the following options when running or creating the container: 

    --device=/dev/video10:/dev/video10
    --device=/dev/video11:/dev/video11
    --device=/dev/video12:/dev/video12  

#### 04. Lidarr
#### 05. my-JD(weblink for my.jdownloader)
#### 06. Ombi
#### 07. OpenSpeedTest
#### 08. Prowlarr
#### 09. qBittorrent
#### 10. Radarr
#### 11. Sonarr
#### 12. UpTimeKuma

### Additional Setup

#### Mounting the disks/partitions with correct permission:  
> To auto mount external drives and partitions on boot, append **fstab**.  
    
    sudo nano /etc/fstab  

>> *(/dev/XXXX for partitions; PARTUUID for disks)*  

    /dev/sda3 /home/pi/ssd exfat defaults,uid=1000,gid=1000 0 0 


#### Last reboot/startup information.
    
    less /var/log/messages | grep Booting


