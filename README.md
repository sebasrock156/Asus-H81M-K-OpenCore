[OpenCore Legacy Patcher]: https://github.com/dortania/OpenCore-Legacy-Patcher/releases

# Asus H81M-K OpenCore (MacOS Monterey 12.x.x)


![Screenshot](https://i.imgur.com/6eFolAP.png)


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

## For use Intel Graphics only:

1. Remove the boot-arg: "**radpg=15**" (because it's for AMD); if you have some incompatible GPU, use the boot-arg "**nv_disable=1**" (for disabling Nvidia) or "**-radvesa**"/"**-amd_no_dgpu_accel**" from *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*

2. Remove the tables "**PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties*

---

## For use AMD Graphics only:

1. Add the boot-arg: "**-igfxvesa**" (for disabling Intel iGPU) and use or add:

- "**radpg=15**" for enabling 3D Acceleration (In almost all 2017 or older GPUs, Eg: RX 580, RX 470, R9 Fury X, HD 7730, etc).

- "**agdpmod=pikera**" for try enabling drivers (In almost all 2018 or newer GPUs, Eg: Vega 56, Radeon VII, RX 5700XT, RX 6600, etc).
From *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* with your graphic card data (Eg: AMD Radeon RX 5700XT and Bermuda HDMI Audio [Navi Series])

---

## For use Nvidia Graphics only:

1. Remove the boot-arg: "**radpg=15**" (because it's for AMD); add the boot-arg: "**-igfxvesa**" (for disabling Intel iGPU), also, add "**nv_disable=1**" (for using Vesa drivers); later, create a new table like this (for enabling Nvidia Drivers):

![nvidiatable](https://i.imgur.com/1crQGj1.png)

**Usually for Pascal (GTX1000 Series), Maxwell (GTX900 Series) and Kepler (GTX600/700 Series) GPUs.***

all on *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*; if Nvidia GPU isn't recognize after that, add "**agdpmod=pikera**" boot-arg too.

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* (Eg: Nvidia GeForce GTX 1070Ti and Nvidia HDMI Output)

3. Download and install [OpenCore Legacy Patcher] for try patch your GPU (Pascal *GTX1000* and older generations *GTX900, 700, 600* are supported; **ALL RTX MODELS AREN'T SUPPORTED**), later, go to *config.plist --> NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82* and remove "**nv_disable=1**" and reboot.

---

## What audio codec I can use?:

With boot-arg "**alcid=**":

- If you have the Realtek ALC887 like me, you can use these layouts: *1, 2, 3, 5, 7, 11, 12, 13, 17, 18, 20, 33, 40, 50, 52, 53, 87, 99*

- If you have the Realtek ALC897, you can use these layouts: *11, 12, 13, 21, 23, 66, 69, 77, 98, 99*

--- 

## Do you want Wi-Fi on your PC?:

- If is a TP-Link, Edimax, Ralink or Mediatek wireless adapter, use the D-Link Utility (https://github.com/chris1111/D-LinkUtility-Package) or Wireless USB Adapters: (https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter) (*see the supported devices*)

- If is some Asus, TP-Link or Intel PCI wireless adapter, use the AirportItlwm (https://github.com/OpenIntelWireless/itlwm) (*see the supported devices on https://openintelwireless.github.io/itlwm/Compat.html*); for Asus and TP-Link adapters, check if the used Wi-Fi card is made by Intel.

---

## Do you only have your Android Phone/Device on hand?:

 1. Download HoRNDIS (https://github.com/jwise/HoRNDIS) and put it on your Hackintosh installation.

 2. Connect your device via USB and enable USB Tethering.


