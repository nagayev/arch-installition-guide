# Arch installation guide
## Obtaining iso
First of all, we should obtain arch iso from official website.    
Then burn it to your usb/cd/dvd drive and load.
## Installing the base system
Now we are going to parte our disk.  
Run `cfdisk /dev/sda`.  
`mkfs.ext4 /dev/sdaX`  
`mount /dev/sdaX /mnt`  
`mkdir /mnt/boot /mnt/home /mnt/var`  
`packstrap /mnt base linux linux-firmware`  
`genfstab -p /mnt >> /mnt/etc/fstab`  
`arch-chroot /mnt`  
`hwclock —systohc —utc`  
`mkinitcpio -p linux`  
`passwd root`  
`useradd -mg users -g wheel -s /bin/bash ${OUR_NAME}`  
`passwd marat`  
`pacman -S dhcpcd iwd`  
`systemctl start iwd`  
`exit`  
`reboot`  
After rebooting:
`iwctl`  
`connect wlan0 ${OUR_NETWORK}`
## Installing Desktop Envirioment
`pacman -S lxdm`  
`pacman -S plasma`  
`systemctl start lxdm`  
