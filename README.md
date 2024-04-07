# Simple Arch Installation Guide

<p align=center>
<img src="https://github.com/PythonHacker24/Arch-Linux-Installation-Guide/blob/main/arch_logo.png?raw=true">
</p>

## A Simple Introduction

This Guide to Arch Installation is meant to be Simple by Desgin. The Arch OS is Simple by design and hence is this guide. The Official Guide is recommended as well as this serves as supplementary to installation. This was written step by step when I was Installing the OS for the first time and hence contains tested commands.  

This is super useful for understanding Linux in general. Debian users can also get an insight on setting up bare minimum setup on their distro too. 

### Setting up WiFi connection
```
iwctl
device list
station "device" connect "SSID"
```

### Time Date Settings 
```
timedatectl set-ntp true
```

### listing drive
```
lsblk
```

### Partition Management 
```
cfdisk "disk path"
```

`1. Atleast 512MB for the BootLoader (512 MB works well)`
`2. Rest for the Root Partition`

### Making the file partition 
```
mkfs.ext4 "disk path"
```

### path mounting 
```
mount "installation partition (Ex. /dev/sda2)" /mnt
mkdir /mnt/boot
mount "boot partition (Ex. /dev/sda1)" /mnt/boot
```

### Essential Tools Installation  
```
pacstrap /mnt base base-devel linux linux-firmware vim
```

### FSTAB Generation
```
genfstab -U /mnt >> /mnt/etc/fstab
```

### Get the arch run up
```
arch-chroot /mnt /bin/bash
```

### Install Network-Manager and GRUB
```
pacman -S networkmanager grub
```

### Enable the Network Manager 
```
systemctl enable NetworkManager
```

### GRUB installation
```
grub-install /dev/sda (just the drive)
```

### GRUB Configuration File Generation 
```
grub-mkconfig -o /boot/grub/grub.cfg
```

### Setting Passwork for the root user
```
passwd
``` 

### Generating Locale 
```
vim /etc/locale.gen
(Uncomment the language to use)
```

### Generate the Locale File 
```
vim /etc/locale.conf
LANG=en-US.UTF-8
```

### Setting up the Hostname
```
vim /etc/hostname
(add the hostname)
```

### Setting up the hostname 
```
ln -sf /usr/share/zoneinfo/<Region>/<Timezone>
```

### Exit the CHROOT Environment
```
exit
```

### Unmount the installation medium
```
umount -R /mnt
```

### Reboot the system 
```
reboot
```

Boot into the installation drive and Arch is installed

Here the installation will be command line only which is good. This way, it's lightweight and absolutely free of any bloated software. It's now on you how you want it to be and how should it perform.

I recommend going with xfce desktop environment for initial setup and then moving towards setting up dwm. xfce is fast and lightweight which works really well for starting up the initial work. Suckless terminal is one of my favourite so I recommended that one for a good experience. 

## Troubleshooting Issues while Installation (goes same for Debian)

These are some issues that you would face while installing utilities. I am referencing the packages here, it's same for both Arch and Debian.

### <X11/Xlib.h> not found
```
sudo apt install libx11-dev
```
### <X11/Xft/Xft.h> not found 
```
sudo pacman -Sy libxft-dev
sudo apt install libxft-dev
```
### <X11/extensions/Xinerama.h> not found
```
sudo apt-get install libx11-dev libxinerama-dev
```
### startx not found 
```
sudo apt install xinit
```
### Installing a Display Manager: lightdm
```
sudo apt install lightdm
```
Make sure to adjust them as per the distro you are using. 

## Additional Resources

### Arch Official Website 
https://archlinux.org/

### Arch Official Installation Guide
https://wiki.archlinux.org/title/installation_guide

### Suckless Official Website 
https://suckless.org/

### NeoVim Official Website
https://neovim.io/

### NvChad Official Website 
https://nvchad.com/

## Some of my setups when I made this repository
<p align=center>
<img src="https://github.com/PythonHacker24/Arch-Linux-Installation-Guide/blob/main/desktop.png?raw=true">
</p>

<p align=center>
<img src="https://github.com/PythonHacker24/Arch-Linux-Installation-Guide/blob/main/nvim.jpeg?raw=true">
</p>
