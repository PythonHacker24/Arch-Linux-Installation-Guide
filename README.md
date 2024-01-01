# ⚡️ ARCH Installation Guide 🗡️

## A Simple Introduction

This Guide to Arch Installation is meant to be Simple by Desgin. The Arch OS is Simple by design and hence is this guide. The Official Guide is recommended as well as this serves as supplementary to installation. This was written step by step when I was Installing the OS for the first time and hence contains tested commands.  

### Setting up WiFi connection
`iwctl`
`device list`
`station "device" connect "SSID"`

### Time Date Settings 
`timedatectl set-ntp true`

### listing drive
`lsblk`

### Partition Management 
`cfdisk "disk path"`

`1. Atleast 512MB for the BootLoader (512 MB works well)`
`2. Rest for the Root Partition`

### Making the file partition 
`mkfs.ext4 "disk path"`

### path mounting 
`mount "installation partition (Ex. /dev/sda2)" /mnt`
`mkdir /mnt/boot`
`mount "boot partition (Ex. /dev/sda1)" /mnt/boot`

### Essential Tools Installation  
`pacstrap /mnt base base-devel linux linux-firmware vim`

### FSTAB Generation
`genfstab -U /mnt >> /mnt/etc/fstab`

### Get the arch run up
`arch-chroot /mnt /bin/bash`

### Install Network-Manager and GRUB
`pacman -S networkmanager grub`

### Enable the Network Manager 
`systemctl enable NetworkManager`

### GRUB installation
`grub-install /dev/sda (just the drive)`

### GRUB Configuration File Generation 
`grub-mkconfig -o /boot/grub/grub.cfg`

### Setting Passwork for the root user
`passwd` 

### Generating Locale 
`vim /etc/locale.gen`
`(Uncomment the language to use)`

### Generate the Locale File 
`vim /etc/locale.conf`
`LANG=en-US.UTF-8`

### Setting up the Hostname
`vim /etc/hostname` 
`(add the hostname)`

### Setting up the hostname 
`ln -sf /usr/share/zoneinfo/<Region>/<Timezone>`

### Exit the CHROOT Environment
`exit`

### Unmount the installation medium
`umount -R /mnt`

### Reboot the system 
`reboot`

Boot into the installation drive and Arch is installed

Here the installation will be command line only which is good. This way, it's lightweight and absolutely free of any bloated software. It's now on you how you want it to be and how should it perform.

## Some of my setups when I made this repository
<p align=center>
<img src="https://github.com/PythonHacker24/PythonHacker24/blob/main/desktop.png?raw=true">
</p>

<p align=center>
<img src="https://github.com/PythonHacker24/PythonHacker24/blob/main/desktop.png?raw=true">
</p>
