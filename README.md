# GO TIENG VIET TRONG UBUNTU



```ruby
 -- SettingUBUNTU
$ sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
$ sudo apt-get update
$ sudo apt-get install ibus ibus-bamboo --install-recommends
$ ibus restart
-- Đặt ibus-bamboo làm bộ gõ mặc định
$ env DCONF_PROFILE=ibus dconf write /desktop/ibus/general/preload-engines "['BambooUs', 'Bamboo']" && gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'Bamboo')]"

```

https://itsmeit.net/cai-unikey-go-tieng-viet-tren-ubuntu-22-04-20-04.html

FONT SF: https://github.com/asterik12/x-special-nautilus-clipboard-copy-file-home-ashish-Downloads-San-Francisco-Pro-Fonts-master.git

# CAI DAT THEME MACOS
https://youtu.be/Y6k7THQ3x6U

```ruby
STEP 1:

sudo apt install gnome-tweaks gnome-shell-extensions -y

https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep

STEP 2: Gnome Extensions org
https://extensions.gnome.org/

-> TURN ON: 
User themes
Blur my shell
Compiz alike magic lamp effect



STEP 3: THEME
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git
cd WhiteSur-gtk-theme
./install.sh -t all -N glassy -s 220
sudo ./tweaks.sh -g

STEP 4: ICONS
https://www.gnome-look.org/p/1400021
-> EXTRACT to COPY to FOLDER: /home/.icons

STEP5: TRUE FONTS
sudo add-apt-repository multiverse
sudo apt update && sudo apt install ttf-mscorefonts-installer


```

# CAI DAT NVIDIA
```ruby

ROOT USER: sudo -s

nvidia-xconfig -a --cool-bits=28 --allow-empty-initial-configuration

nvidia-settings -a GPUFanControlState=1 -a GPUTargetFanSpeed=30
nvidia-settings -V -c :0 -a '[gpu:0]/GPUFanControlState=1' -a '[fan:0]/GPUTargetFanSpeed='"30" -a '[fan:1]/GPUTargetFanSpeed='"40"
----------------------------------


SOLUTION 1:

apt install nvidia-utils-510
apt install nvidia-settings


---------------------

SOLUTION 2:

Solved this issue by editing the file: /./etc/X11/Xwrapper.config
Steps:

    cd /./etc/X11/
    sudo -s [because you need root access]
    gedit Xwrapper.config &
    add the line needs_root_rights=yes before allowed_users=console.

Therefore the Xwrapper.config file will be:

# Xwrapper.config (Debian X Window System server wrapper configuration file)
#
# This file was generated by the post-installation script of the
# xserver-xorg-legacy package using values from the debconf database.
#
# See the Xwrapper.config(5) manual page for more information.
#
# This file is automatically updated on upgrades of the xserver-xorg-legacy
# package *only* if it has not been modified since the last upgrade of that
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command as root:
#   dpkg-reconfigure xserver-xorg-legacy
needs_root_rights=yes
allowed_users=console


---
SOLUTION 3

sudo nvidia-xconfig
sudo nvidia-xconfig --cool-bits=4


---------------------------

nvidia-settings -a ‘[gpu:0]/GPUFanControlState=1’
nvidia-settings -a ‘[fan:0]/GPUTargetFanSpeed=100’

```

# INSTALL SOFTWARES
```C
# INSTALL GOOGLE CHROME
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb

# INSTALL SNAP -> SPOTIFY , VLC , AUDACITY, TELEGRAM,...
sudo apt install snap
sudo apt install git
sudo apt install telegram-desktop

sudo snap install spotify
sudo snap install vlc
sudo snap install telegram-desktop
sudo snap install code --classic

```
# INSTALL R AND PYTHON
```c
# INSTALL R

wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/r-project.gpg
echo "deb [signed-by=/usr/share/keyrings/r-project.gpg] https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" | sudo tee -a /etc/apt/sources.list.d/r-project.list
sudo apt update
sudo apt install --no-install-recommends r-base

install.packages('txtplot')


# INSTALL R STUDIO
https://www.rstudio.com/products/rstudio/download/#download
sudo dpkg -i rstudio.deb
sudo apt --fix-broken install

```


# INSTALL SQL SERVER
```ruby
sudo apt install docker
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker 
sudo systemctl enable docker.service
sudo systemctl enable containerd.service

sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
----
sudo docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=1111" \
   -p 1433:1433 --name sql1 --hostname sql1 \
   -d \
   mcr.microsoft.com/mssql/server:2019-latest
   
sudo docker ps -a
docker exec -t sql1 cat /var/opt/mssql/log/errorlog | grep connection

SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName');
    
Connect to SQL Server
sudo docker exec -it sql1 "bash"
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "1111"


https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-ver15&preserve-view=true&pivots=cs1-bash

Create a new database

CREATE DATABASE TestDB;
SELECT Name from sys.databases;
USE TestDB;
CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT);
INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
SELECT * FROM Inventory WHERE quantity > 152;


sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install postgresql



```


# INSTALL POSTGRESQL
```ruby
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install postgresql

```

# INSTALL WINDOWS 11
```ruby 
sudo apt install gparted
```
