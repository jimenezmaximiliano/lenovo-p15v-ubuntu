# Commands to run to install and setup basic apps that I use

## Sources
wget -O - https://dbeaver.io/debs/dbeaver.gpg.key | sudo apt-key add -
echo "deb https://dbeaver.io/debs/dbeaver-ce /" | sudo tee /etc/apt/sources.list.d/dbeaver.list
echo "deb https://dl.bintray.com/getinsomnia/Insomnia /" | sudo tee -a /etc/apt/sources.list.d/insomnia.list
wget --quiet -O - https://insomnia.rest/keys/debian-public.key.asc | sudo apt-key add -
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

sudo apt update

## Apt install
sudo apt install -y synaptic git vim snapd python3-gpg gdebi insomnia golang-go apt-transport-https ca-certificates software-properties-common gnupg-agent docker-ce calibre gnumeric libreoffice vlc php composer keepassxc steam gimp terraform awscli ansible docker-compose parallel gitg mysql-client pdfshuffler bleachbit

## Docker
sudo usermod -aG docker ${USER}
su - ${USER}

## NVM
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash

## Snap
sudo snap install snap-store && \
sudo snap install --classic pycharm-community && \
sudo snap install --classic code && \
sudo snap install --classic robo3t-snap && \
sudo snap install --classic postman && \
sudo snap install --classic spotify && \
sudo snap install --classic phpstorm && \
sudo snap install --classic goland && \
sudo snap install --classic sublime-text && \
sudo snap install --classic zoom-client && \
sudo snap install shutter && \
sudo snap install skype --classic && \
sudo snap install dbeaver-ce && \
sudo snap install --classic slack

## Git config
git config --global user.name "Maximiliano Jimenez"
git config --global user.email jimenez@maximiliano.com.ar
git config --global core.editor vim
git config --global core.fileMode false

## Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
rm google-chrome-stable_current_amd64.deb

## Teamviewer
wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
sudo gdebi teamviewer_amd64.deb
rm teamviewer_amd64.deb

## Manual install

- Express vpn
- Dropbox
- Mongodb compass ce