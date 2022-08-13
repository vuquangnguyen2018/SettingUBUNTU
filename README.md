-- GO TIENG VIET TRONG UBUNTU

# SettingUBUNTU
$ sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
$ sudo apt-get update
$ sudo apt-get install ibus ibus-bamboo --install-recommends
$ ibus restart
# Đặt ibus-bamboo làm bộ gõ mặc định
$ env DCONF_PROFILE=ibus dconf write /desktop/ibus/general/preload-engines "['BambooUs', 'Bamboo']" && gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'Bamboo')]"

https://itsmeit.net/cai-unikey-go-tieng-viet-tren-ubuntu-22-04-20-04.html


-- CAI DAT THEME MACOS
https://youtu.be/Y6k7THQ3x6U
