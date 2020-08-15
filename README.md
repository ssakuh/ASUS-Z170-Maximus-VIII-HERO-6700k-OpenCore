# ASUS-Z170-Maximus-VIII-HERO-6700k-OpenCore

This is an OpenCore version of ASUS Z170i Pro Gaming Hackintosh EFI. It works perfectly on macOS Catalina (10.15.6). FCPX GPU rendering works smoothly. HDR can be enabled. Sleep, Airdrop and Handoff are supported.

## Hardware
| Item | Brand | Model | Driver | Comment |
|-----|-----|-----|-----|-----|
| Motherboard | ASUS | Z170 Maximus VIII Hero | | |
| CPU | Intel | i7-6700K  | | | oc to 4.6GHz 1.33v |
| RAM | HyperX | Fury Black 4x8GB DDR4 2133MHz | | oc to 2800 1.35v |
| iGPU | Intel | HD Graphics 530 | built-in | Headless mode |
| dGPU | ASUS | RX 5700XT TUF |  |  |
| SSD | Samsung | 970 EVO 250GB NVMe | [NVMeFix](https://github.com/acidanthera/NVMeFix) | |
| Ethernet | Intel | I219-V | [IntelMausi](https://github.com/acidanthera/IntelMausi) | |
| Audio | Realtek | ALC1150 | [AppleALC](https://github.com/acidanthera/AppleALC) | |


## BIOS Setup
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
