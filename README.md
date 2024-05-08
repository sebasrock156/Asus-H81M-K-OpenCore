![OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher/releases)
# Asus H81M-K OpenCore (MacOS Monterey 12.x.x)

Hardware | Model
--- |:--:
![motherboard](https://i.imgur.com/IM3kGTn.png) | Asus H81M-K (Haswell)
![bios](https://i.imgur.com/RmYixFt.png) | Asus EZ Aptio V's v3.603/v3.802 (by American Megatrends (AMI)/Asus)
![processor](https://i.imgur.com/BzXF1mf.png) | Intel Core i5 (4th Gen) 4440 4 Cores/4 Threads@3,1Ghz
![igpu](https://i.imgur.com/KQsHndn.png) | Intel 4600 HD Graphics 1GB VRAM @1200Mhz (Supported until MacOS Monterey)
![dgpu](https://i.imgur.com/7TZmF2e.png) | AMD/Sapphire Radeon RX 580 Nitro+ 8GB VRAM @1500Mhz 
![audio](https://i.imgur.com/A7RRuUn.png) | ALC887 (in-build)
Ethernet | Realtek RTL8111G
![ddr3](https://i.imgur.com/5MAnSyf.png) | Corsair Vengeance/Kingston HyperX 12GB(4+8x2) DDR3@1600Mhz
![ssd](https://i.imgur.com/pozDx4X.png) | Kingston A400 SSD 960GB (QLC SM2259XT Controller)
---


### Works:
---
<details>

- Installer Boot ✅ (Installation on SSD: ~45/50 minutes)

- System Boot ✅

- USB Ports (2.0 and 3.0) ✅

- Screen ✅ (1336x768, 1080x1920)

- Audio Card ✅ (Inputs and Outputs)

- Ethernet ✅

- PCI Express Ports ✅

- Sleep Mode ✅

 
</details>


### IMPORTANT NOTES:
---
<details>

---
## For use Intel Graphics only:

1. Remove the boot-arg: "**radpg=15**" from *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*

2. Remove the tables "**PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties*

---

## For use Nvidia Graphics only:
1. Enable the boot-arg: "**igfxvesa**" from *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* (Eg: Nvidia GeForce GTX 1070Ti and Nvidia HDMI Output)

3. Download and install [OpenCore Legacy Patcher] for try patch your GPU (Pascal *GTX1000* and older generations *GTX900, 700, 600* are supported; **ALL RTX MODELS AREN'T SUPPORTED**)

---

## What audio codec I can use?:

With boot-arg "**alcid=**":

- If you have the Realtek ALC887 like me, you can use these layouts: *1, 2, 3, 5, 7, 11, 12, 13, 17, 18, 20, 33, 40, 50, 52, 53, 87, 99*

- If you have the Realtek ALC897, you can use these layouts: *11, 12, 13, 21, 23, 66, 69, 77, 98, 99*

 
</details>

