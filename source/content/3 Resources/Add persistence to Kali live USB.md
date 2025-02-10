---
created: 20230922-1514
tags:
  - Resources/Linux
  - Resources/Kali
---

What will you discover today?

A partir de un iso recién instalado de kali en un pendrive: 

``` bash
#!/bin/bash
usb=/dev/sdX
#make a new partition at the end of the drive
sudo fdisk $usb <<< $(printf "n\np\n\n\n\nw")
#format the new partition
sudo mkfs.ext4 -L persistence ${usb}3
#mount it
sudo mkdir -p /mnt/my_usb
sudo mount ${usb}3 /mnt/my_usb
#write the persistence config file
echo "/ union" | sudo tee /mnt/my_usb/persistence.conf
#close behind you
sudo umount ${usb}3

```

---
## Related Ideas:
* [[Kali]]

[Kali Documentation](https://www.kali.org/docs/usb/usb-persistence/)
