---
created: 20241216-1514
tags:
  - Resources/windows
  - Resources/os
  - Resources/install
---

## Use Rufus

_This method is handy if you want a quick and easy way to create USB installation media for Windows 11. You will need an 8GB or larger USB flash drive_

1. [ ] Download the Windows 11 iso [Download](https://www.microsoft.com/en-us/software-download/windows11)
2. [ ] Download Rufus version 3.16 or later [Download](https://github.com/pbatard/rufus/releases)
3. [ ] Run the Rufus application
4. [ ] Select the target USB device (double check the selection, all data on the USB device will be lost)
5. [ ] Click the Select button next to Disk or ISO image > Browse to and select the downloaded Windows 11 iso file
6. [ ] Select Extended Windows 11 Installation (no TPM / no Secure Boot) from the Image option dropdown
7. [ ] Select MBR from the Partition scheme dropdown
8. [ ] Click the Start button to write the modified installation media to the target USB device
9. [ ] Wait for Rufus to write the files to the USB device
10. [ ] That's it! Boot to the USB device on any machine you wish to install Windows 11 on

---
### Source

https://i12bretro.github.io/tutorials/0635.html

---
[[permanent]]
