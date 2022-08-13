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

sudo apt install gnome-tweaks gnome-shell-extenstions -y

STEP 2: Gnome Extensions org
https://extensions.gnome.org/

-> TURN ON: 
User themes


STEP 3: THEME
https://github.com/vinceliuice/WhiteSur-gtk-theme.git
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git
cd WhiteSur-gtk-theme
./install.sh -t all -N glassy -s 220
sudo ./tweaks.sh -g

STEP 4: ICONS
https://www.gnome-look.org/p/1400021


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
```
# INSTALL R AND PYTHON
```c
# INSTALL R

wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/r-project.gpg
echo "deb [signed-by=/usr/share/keyrings/r-project.gpg] https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" | sudo tee -a /etc/apt/sources.list.d/r-project.list

```
