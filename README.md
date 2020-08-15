# ASUS-Z170-Maximus-VIII-HERO-6700k-OpenCore

OpenCore 0.6.0 EFI directory for my build. 

It works perfectly on macOS Catalina (10.15.6). FCPX GPU rendering works smoothly. HDR can be enabled. Sleep, Airdrop and Handoff are supported.

### Hardware
| Item | Brand | Model | Kext | Comment |
|-----|-----|-----|-----|-----|
| Motherboard | ASUS | Z170 Maximus VIII Hero | | |
| CPU | Intel | i7-6700K | | oc to 4.6GHz 1.33v |
| RAM | HyperX | Fury Black 4x8GB DDR4 2133MHz | | oc to 2800 1.35v |
| iGPU | Intel | HD Graphics 530 | built-in | Headless mode |
| dGPU | ASUS | RX 5700XT TUF |  |  |
| SSD | Samsung | 970 EVO 250GB NVMe | [NVMeFix](https://github.com/acidanthera/NVMeFix) | |
| Ethernet | Intel | I219-V | [IntelMausi](https://github.com/acidanthera/IntelMausi) | |
| Audio | Realtek | ALC1150 | [AppleALC](https://github.com/acidanthera/AppleALC) | |

## How to

Follow this guide: https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html

### BIOS Setup
| Name | Option |
| --- | --- |
| SW Guard Extensions (SGX) | Disabled |
| CFG Lock | Disabled |
| VT-d | Disabled |
| Above 4G Decoding | Enabled |
| Primary Display | PCIE |
| iGPU-Multi-Monitor | Enabled |
| DVMT Pre-Allocated | 64M |
| IOAPIC 24-119 Entries | Disabled |
| Network Stack | Disabled |
| Legacy USB Support| Enabled |
| Fast Boot | Disabled |
| OS Type | Other OS |
| Launch CSM | Disabled |

### Generate ACPI

Generate your own SSDT-EC.aml and SSDT-PLUG.aml, as mine used the overclocking settings.

### Edit config.plist 

Generate your own values and use the NIC MAC on the ROM field.

```xml 
		<dict>
			<key>AdviseWindows</key>
			<false/>
			<key>MLB</key>
			<string>MLB</string>
			<key>ROM</key>
			<data>ROM</data>
			<key>SpoofVendor</key>
			<true/>
			<key>SystemProductName</key>
			<string>iMac17,1</string>
			<key>SystemSerialNumber</key>
			<string>SN</string>
			<key>SystemUUID</key>
			<string>UUID</string>
		</dict>
```
