# ASUS Z170 Maximus VIII HERO / i7 6700k OpenCore

[OpenCore](https://github.com/acidanthera/OpenCorePkg/releases) 0.8.5 EFI directory for my build. 

It works perfectly on macOS Ventura (13.0). FCPX GPU rendering works smoothly. HDR can be enabled. Sleep, Airdrop and Handoff are supported.

### Known issues
 - ASMedia USB3.1 (both Type A and C) do not carry data, but they charge with 1,4A -> for me they were dead in Windows/Linux anyway for some reason, maybe faulty board
 - Thunderbolt 3 not available
 - HD 530 DP is broken, needs port fix, need help with it
 - you tell me 

### Hardware
| Item | Brand | Model | Kext | Comment |
|-----|-----|-----|-----|-----|
| Motherboard | ASUS | Z170 Maximus VIII Hero | USBMap.kext | |
| CPU | Intel | i7-6700K | | oc to 4.6GHz 1.33v |
| RAM | HyperX | Fury Black 4x8GB DDR4 | XMP | oc to 2800 MHz 1.35v |
| iGPU | Intel | HD Graphics 530 | [WEG](https://github.com/acidanthera/WhateverGreen) | Headless mode |
| dGPU | ASUS | RX 5700XT TUF | [WEG](https://github.com/acidanthera/WhateverGreen) |  |
| SSD | Samsung | 970 EVO 250GB NVMe | [NVMeFix](https://github.com/acidanthera/NVMeFix) | |
| Ethernet | Intel | I219-V | [IntelMausi](https://github.com/acidanthera/IntelMausi) | |
| Audio | Realtek | ALC1150 | [AppleALC](https://github.com/acidanthera/AppleALC) | |

## How to

In general, follow this [guide](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html) and this [documentation](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Configuration.pdf). 

Below are my notes for this specific hardware config:

### UEFI Setup

Load files from "UEFI settings" folder on a USB drive and load them from Tools -> OC Profile. If you are applying after a CMOS reset, you should first disable CSM, reboot

**Warning**: They have my overclocking settings, please check the CPU / RAM settings before applying on your machine.

As the installer reboots several times, set the USB drive with macOS installer as the 1st boot option.

### Preparing installer drive

Generate your own ```SSDT-EC.aml``` and ```SSDT-PLUG.aml``` using [this](https://github.com/corpnewt/SSDTTime), as mine used the overclocking settings and copy them in ```./EFI/OC/ACPI```, then just copy over the entire folder in the EFI directory (depending on the method of USB creation used).

### Edit config.plist 

Generate your own SMBIOS values using [this](https://github.com/corpnewt/GenSMBIOS) tool and use your network card's MAC address (without dashes) on the ROM field, and update the file ```./EFI/OC/config.plist```.

```xml 
<dict>
    <key>AdviseFeatures</key>
    <false/>
    <key>MLB</key>
    <string>${MLB}</string>
    <key>MaxBIOSVersion</key>
    <false/>
    <key>ProcessorType</key>
    <integer>0</integer>
    <key>ROM</key>
    <data>${ROM}</data>
    <key>SpoofVendor</key>
    <true/>
    <key>SystemMemoryStatus</key>
    <string>Auto</string>
    <key>SystemProductName</key>
    <string>MacPro7,1</string>
    <key>SystemSerialNumber</key>
    <string>${SYSTEM_SERIAL_NUMBER}</string>
    <key>SystemUUID</key>
    <string>${SYSTEM_UUID}</string>
</dict>
```

### Post install

Mount EFI using [this](https://github.com/corpnewt/MountEFI) and copy over the entire EFI folder from the USB to the root of the EFI partition on the drive you installed macOS on.

(optional) - run ```osx.sh``` from [here](https://raw.githubusercontent.com/hecz0r/config/master/osx.sh) to get my dotfiles and some software I use.

### Troubleshooting

If any part of the boot process hangs or throws errors, enable debugging in config.plist and replace the provided files with ones from OpenCore Debug version, and respectively, the Kext you suspect is faulty in Debug version. The files provided by me are Release versions.
