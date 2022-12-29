# Instalação do Debian 11 Sway
1. fazer o download do debian-firmware non-free e procegue com a instalação.
-> https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/

2. adicionar no arquivo /etc/apt/source.list:

	deb http://deb.debian.org/debian/ bullseye main non-free
	deb-src http://deb.debian.org/debian/ bullseye main non-free

	deb http://security.debian.org/debian-security bullseye-security main contrib non-free
	deb-src http://security.debian.org/debian-security bullseye-security main contrib non-free

	deb http://deb.debian.org/debian/ bullseye-updates main contrib non-free
	deb-src http://deb.debian.org/debian/ bullseye-updates main contrib non-free

	deb http://deb.debian.org/debian bullseye-backports main contrib non-free
	deb-src http://deb.debian.org/debian bullseye-backports main contrib non-free

3. atualizar os pacotes:
-> # apt update

-> # apt install sway xwayland xorg sudo waybar wofi kitty terminator swaybg swayidle wl-clipboard grim slurp wf-recorder light yad wlogout mpv mpd mpc viewnior imagemagick gir1.2-polkit-1.0

## configuracao

1. copiar o arquivo de configuração para HOME
-> $ mkdir .config/sway
-> $ cp /etc/sway/config ~/
 

--> ~/.config/sway/config
set $menu exec wofi --show drun

sudo apt install nautilus gnome-calendar dconf-editor chromium gedit --no-install-recommends

--> compactadores e descompactadores
sudo apt-get install p7zip-full p7zip-rar lzma lzma-dev rar unrar-free p7zip ark ncompress file-roller

--> icons
sudo apt install papirus-icon-theme arc-theme libreoffice libreoffice-style-papirus eog
