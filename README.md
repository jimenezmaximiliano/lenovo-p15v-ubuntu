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

The laptop is connected to an external screen (Dell) and a usb hub through USB c (j5create dongle) 

### Ubuntu

- Kernel: 5.6.0-1035-oem
- Nvidia drivers: 440-server

### Current issues

- Sometimes after waking up the laptop my usb ethernet adapter connected through a USB c dongle (j5create) and a usb hub
on my Dell monitor doesn't connect. Unplugging and pluging back again or a reboot fixes it.
- Sometimes when I suspend the laptop it goes to the login screen and after logging in it actually suspends (random)
- Sometimes after waking up the laptop my main screen is black. Closing the lid and opening it again fixes the issue
- If you turn off the laptop and immediately close the lid, you get the alternate modes error (see change log)

## Change log

- BIOS upgrade
- Windows is installed on disk 1. Ubuntu will be installed on disk 2
- Install Ubuntu 20.04, minimal install + third party drivers
  
| Kernel        | GPU driver    |
| ------------- |:-------------:|
| 5.4.0         | nvidia 440    |

| Test                | Result        | Notes                                                 |
| ------------------- |:-------------:|:-----------------------------------------------------:|
| Reboot              | OK            | -                                                     |
| Reboot (lid closed) | OK            | -                                                     |
| Shutdown            | OK            | -                                                     |
| Suspend             | OK            | -                                                     |
| Additional drivers  | OK            | -                                                     |
| Nvidia settings     | KO            | Shows only the nvidia gpu                             |

---

- sudo apt update
- sudo apt upgrade
- reboot
- Now additional drivers shows an unknown device set to not use
- Graphics are now in nouveau
- Switched to 455 fails, unmet dependencies
- sudo ubuntu-drivers autoinstall fails
- sudo apt update
- sudo apt autoremove
- sudo apt install synaptic
- Synaptic: reload and mark all upgrades, apply
- sudo apt autoremove
- Still problems with ubuntu drivers so I installed the package manually for 455 and now ubuntu-drivers autoinstall does something
- Kernel 5.6.0-1035 oem was installed

---

| Kernel        | GPU driver    |
| ------------- |:-------------:|
| 5.6.0-1935    | nvidia 455    |


| Test                | Result        | Notes                                                 |
| ------------------- |:-------------:|:-----------------------------------------------------:|
| Reboot              | OK            | -                                                     |
| Reboot (lid closed) | OK            | -                                                     |
| Shutdown            | OK            | -                                                     |
| Suspend             | OK            | -                                                     |
| Additional drivers  | OK            | -                                                     |
| Nvidia settings     | KO            | Shows a white screen                                  |

- Revert back to 450
- reboot
- ERROR: ucsi_acpi USBC000:00 con1: failed to register alternate modes

---

- Back to 440

| Kernel        | GPU driver        |
| ------------- |:-----------------:|
| 5.6.0-1935    | nvidia 440-server |

| Test                | Result        | Notes                                                 |
| ------------------- |:-------------:|:-----------------------------------------------------:|
| Reboot              | OK            | -                                                     |
| Reboot (lid closed) | OK            | -                                                     |
| Shutdown            | OK            | -                                                     |
| Suspend             | OK            | -                                                     |
| Additional drivers  | OK            | -                                                     |
| Nvidia settings     | KO            | Shows a white screen                                  |

---

- Firefox: disable save password
- sudo apt install git
- Generate ssh key
- expressvpn preferences set network_lock on
- expressvpn preferences set auto_connect on
- sudo snap install pycharm-community --classic
