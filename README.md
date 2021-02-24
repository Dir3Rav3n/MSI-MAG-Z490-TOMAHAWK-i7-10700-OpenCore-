# MSI-MAG-Z490-TOMAHAWK-i7-10700-OpenCore-

Hello,

I have successfully installed MacOS on my i7 10700 non K on MSI MAG Z490 TOMAHAWK.



# Hardware

- Intel I7 10700
- MSI MAG Z490 TOMAHAWK
	- Audio: REALTEK/ALC1200-VD1
	- 1x Realtek® RTL8125B 2.5G LAN + 1x Intel I219V 1G LAN
	- 1x USB-C port
- RAM: 32GB DDR4 Corsair 3000MHz
- GPU: XFX AMD Radeon RX 580 GTS XXX Edition 8GB
- Fenvi FV-HB1200 for WiFi/Bluetooth 


# Geekbench

![Geekbench Score with OC](Geekbench/Geekbench.png)
![Geekbench Score with OC](Geekbench/Geekbench2.png)

# Cinebench

![Cinebench Score with OC](Cinebench/Cinebench.png)


# Working

- [x] **macOS Big Sur 11.0.1**
- [x] **Audio** Realtek ALC1200-VD1 (AppleALC.kext, layout-id=7)
- [x] **USB**, all ports
- [x] **iGPU UHD630 Headless mode**
- [x] **RX 580 works OOB no kext used**
- [x] **Dual Monitor**
- [x] **iMessage/FaceTime**
- [x] **WiFi/Bluetooth, Handoff and AirDrop** Fenvi FV-HB1200 (no kext required)
- [x] **Sleep/Wake**
- [x] **Shutdown**
- [x] **Restart**

# Instructions

BIOS Settings:

- Disable CFG Lock
- Disable Fastboot 
- Enable XMP Profile for RAM
- Enable Above 4G decoding
- Enable iGPU 64MB

1. Create a MacOS Big Sur bootable USB. You can do this on a real Mac
 	 - Go into the app store and search for macOS Big Sur, once downloaded you can find the Installer.app inside Applications folder.
   - Earse the USB by using Disk Utility and rename the USB to MyVolume
   - Create bootable USB by using this command: sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
  
2. Mount the EFI-partition of the "Install macOS Big Sur" disk.
   - You can do this using the Terminal with the following commands:
   - diskutil list
   - Once you have found the disk for example disk0s1 runt the following command to mount the EFI partition:
   - sudo diskutil mount disk0s1
   - Enter the password and the EFI partition should be mounted 
   
3. Delete all folders and then copy my EFI folder to the root of the EFI-partition
4. Go to EFI/OC and open the config.plist with a plist Editor (You can use PlistEditor Pro use google for this)
5. Once the config.plist is open navigate to PlatformInfo/Generic and paste your serials for MLB, SystemSerialNumber and SystemUUID. (you can use CorpNewt's GenSMBIOS)
6. Boot from the bootable USB and install macOS.
7. Once macOS is installed you can copy the EFI folder to the EFI partition of the internal SSD/HDD
