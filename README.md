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

- Sometimes after waking up the laptop my usb ethernet adapter connected through a USB c dongle (j5create), and an usb 
  hub on my Dell monitor doesn't connect. Unplugging and plugging it back again, or a reboot fixes it.
- Sometimes when I suspend the laptop it goes to the login screen and after logging in it actually suspends (random)
- Sometimes after waking up the laptop my main screen is black. Closing the lid and opening it again fixes the issue
- Expressvpn looks connected but doesn't work after waking up
- After switching users my bluetooth headset connects and freezes every bluetooth device and also doesn't work. Trying
to disconnect and connect again doesn't work either. Disabling bluetooth and enabling it again doesn't fix it either.
  Restarting the bluetooth service works
  
### Issues that were fixed

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
| 5.6.0-1035    | nvidia 455    |


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
| 5.6.0-1035    | nvidia 440-server |

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
- sudo apt install vim

---

- sudo apt-add-repository ppa:jtaylor/keepass
- sudo apt install python3-gpg (for Dropbox)
- Install dropbox

---

- sudo snap install --classic code
- wget -O - https://dbeaver.io/debs/dbeaver.gpg.key | sudo apt-key add -
- echo "deb https://dbeaver.io/debs/dbeaver-ce /" | sudo tee /etc/apt/sources.list.d/dbeaver.list
- sudo apt update
- sudo apt -y install dbeaver-ce
- Install mongodb compass ce
- sudo snap install robo3t-snap
- Install teamviewer
- sudo apt install gdebi
- echo "deb https://dl.bintray.com/getinsomnia/Insomnia /" \
    | sudo tee -a /etc/apt/sources.list.d/insomnia.list
- wget --quiet -O - https://insomnia.rest/keys/debian-public.key.asc \
    | sudo apt-key add -
- sudo apt-get update
- sudo apt-get install insomnia
- sudo snap install postman
- wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
- nvm install 12
- sudo apt install curl gitg golang
- sudo apt install apt-transport-https ca-certificates curl software-properties-common
- curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
- sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
- sudo apt update
- sudo apt install docker-ce
- sudo usermod -aG docker ${USER}
- su - ${USER}
- Install chrome
- sudo snap install spotify
- sudo snap install phpstorm --classic
- sudo snap install goland --classic
- Install steam
- Install sublime
- Install zoom
- sudo snap install slack --classic
- sudo apt install calibre

---

| Kernel        | GPU driver    |
| ------------- |:-------------:|
| 5.6.0-1035    | nvidia 440    |

| Test                | Result        | Notes                                                 |
| ------------------------------ |:-------------:|:-----------------------------------------------------:|
| Reboot                         | OK            | -                                                     |
| Reboot (lid closed)            | OK            | -                                                     |
| Shutdown                       | OK            | -                                                     |
| Shutdown (lid closed)          | OK            | -                                                     |
| Suspend                        | OK            | -                                                     |
| Suspend (lid closed)           | OK            | -                                                     |
| Additional drivers             | OK            | As expected (one unknown device)                      |
| Nvidia settings                | OK            | -                                                     |
| Logout                         | OK            | -                                                     |
| Logout (lid closed)            | KO            | The screen goes black                                 |
| Switch user                    | OK            | -                                                     |
| Switch user (lid closed)       | KO            | The screen goes black                                 |
| Power on and quickly close lid | OK            | It started working :)                                 |

---

sudo apt install gnumeric libreoffice vlc