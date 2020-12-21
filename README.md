# Lenovo P15V

## Certification

https://certification.ubuntu.com/hardware/202008-28186
This system was tested with 20.04 LTS, running the 5.6.0-1021-oem kernel.

## Current setup

### BIOS

Version: 1.15 2020-10-26

- Set to default
- Secure boot: disabled

### Connections

The laptop is connected to an external screen through HDMI

### Ubuntu Pop OS

- Kernel: 5.8.0-7630-generic
- Nvidia drivers: 455.38

### Current issues

- WIP
  
## Issues that I had with Ubuntu 20.04

- Sometimes after waking up the laptop my usb ethernet adapter connected through a USB c dongle (j5create), and an usb 
  hub on my Dell monitor doesn't connect. Unplugging and plugging it back again, or a reboot fixes it.
- Sometimes when I suspend the laptop it goes to the login screen and after logging in it actually suspends (random)
- Sometimes after waking up the laptop my main screen is black. Closing the lid and opening it again fixes the issue
- Expressvpn looks connected but doesn't work after waking up
- After switching users my bluetooth headset connects and freezes every bluetooth device and also doesn't work. Trying
to disconnect and connect again doesn't work either. Disabling bluetooth and enabling it again doesn't fix it either.
  Restarting the bluetooth service works
- Sometimes both wifi and bluetooth stop working and it only starts working again when I reboot
- If you turn off the laptop and immediately close the lid, you get the alternate modes error (see change log)
- After suspending I cannot change the keyboard layout

## Change logs

- I've tried to use Ubuntu 20.04 (see changelogs/1-Ubuntu-20-04.md)
- I've installed Ubuntu 20.10 for a couple of hours, it seemed to work better but I decided to give Pop OS a go
- Pop OS is the current OS I'm using