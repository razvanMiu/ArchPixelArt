# ArchPixelArt

# Arch Linux Installation Setup

1. Download Arch linux from https://www.archlinux.org/download/
2. Write the iso into USB drive:
  - Windows: use rufus https://rufus.ie/
  - Linux: `sudo dd bs=4M if=Downloads/ubuntu-19.04-desktop-amd64.iso of=/dev/sdb conv=fdatasync`
    * sudo: You need to be a superuser to issue dd commands. You will be prompted for your password.
    * dd: The name of the command we’re using.
    * bs=4M: The -bs (blocksize) option defines the size of each chunk that is read from the input file and wrote to the output device. 4 MB is a good choice because it gives decent throughput and it is an exact multiple of 4 KB, which is the blocksize of the ext4 filesystem. This gives an efficient read and write rate.
    * if=Downloads/ubuntu-19.04-desktop-amd64.iso: The -if (input file) option requires the path and name of the Linux ISO image you are using as the input file.
    * of=/dev/sdb: The -of (output file) is the critical parameter. This must be provided with the device that represents your USB drive. This is the value we identified by using the lsblk command previously. in our example it is sdb, so we are using /dev/sdb. Your USB drive might have a different identifier. Make sure you provide the correct identifier.
    * conv=fdatasync: The conv parameter dictates how dd converts the input file as it is written to the output device. dd uses kernel disk caching when it writes to the USB drive. The fdatasync modifier ensure the write buffers are flushed correctly and completely before the creation process is flagged as having finished.
3. Mount USB and start the PC
4. Install Arch Linux:
```
$ wifi-menu       //  connect to internet
$ pacman -Sy      //  Update database
$ pacman -S git   //  Install git
$ git clone http://github.com/razvanMiu/ArchPixelArt
$ cd ArchPixelArt
$ chmod a+x 0-setupmirrors.sh
$ sh 0-setupmirrors.sh
$ wget archfi.sf.net/archfi
$ sh archfi       //  Follow the setup installing lxde as a desktop environment
                  //  Useful yay, firefox,
                  //  Make sure to install display server and NetworkManager
```
5. Reboot system and connect to internet
```
$ nmcli r wifi on
$ nmcli d wifi list
$ nmcli d wifi connect *SSID* password *password*
```
6. (Optional) Install useful applications
```
$ yay -S nautilus terminator google-chrome
```
7. Install KDE Plasma
```
$ yay -S plasma
$ yay -S sddm
$ yay -S cmake
$ yay -S sddm-kcm
```
8. Install Login Theme https://github.com/Catvert/kde-plasma-chili
Go to `System Settings > Startup and Shutdown > Login Screen (SDDM) > Get New Theme` and search for "Chili for KDE".
