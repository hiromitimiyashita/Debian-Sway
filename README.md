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
-> # apt install -t bullseye-backports xorg xwayland qt6-wayland qt5ct
-> # apt install sway sudo waybar wofi foot kitty terminator swaybg swayidle wl-clipboard grim slurp wf-recorder light yad wlogout mpv mpd mpc viewnior imagemagick gir1.2-polkit-1.0 lightdm lightdm-gtk-greeter-settings fonts-font-awesome fonts-cantarell fzf gcc build-essential papirus-icon-theme arc-theme libreoffice libreoffice-style-papirus libreoffice-l10n-pt-br libreoffice-gtk3 network-manager alsa-utils pulseaudio pavucontrol



## configuracao
1. adicionar usuário ao sudo
-> # nano /etc/sudoers
  	user ALL=(ALL:ALL) ALL

1. ativar o gerenciador de login lightdm
-> sudo systemctl enable lightdm.service
1.1 dar permissão para alterar o lightdm
-> $ sudo chmod 777 /etc/lightdm/lightdm-gtk-greeter.cong

1.2 criar as pastas do usuãrios automaticamente
-> $ xdg-user-dirs-update

1.3 adicionar as variáveis de ambientes do sistema sway
--> ~/.profile
-> export MOZ_ENABLE_WAYLAND=1 # FOR FIREFOX
-> export XDG_SESSION_TYPE=wayland
-> export GDK_BACKEND=wayland
-> export QT_QPA_PLATFORM=wayland
-> export QT_WAYLAND_DISABLE_WINDOWDECORATION=1
-> export QT_QPA_PLATFORMTHEME=qt5ct
-> export CLUTTER_BACKEND=wayland
-> export SDL_VIDEODRIVER=wayland

-> export GTK_IM_MODULE=ibus
-> export XMODIFIERS=@im=ibus
-> export QT_IM_MODULE=ibus
-> export SDL_IM_MODULE=ibus
-> export XDG_CURRENT_DESKTOP=KDE ibus-daemon -drx

# resolvendo o problema com java
if [ "$XDG_SESSION_DESKTOP" = "sway" ] ; then
    # https://github.com/swaywm/sway/issues/595
    export _JAVA_AWT_WM_NONREPARENTING=1
fi

--> $ ln -s $HOME/.profile $HOME/.bash_profile
--> $ ln -s $HOME/.profile $HOME/.zprofile
--> $ touch .Xresources
--> $ ln -s $HOME/.Xresources $HOME/.Xdefaults

1.3 renicia sistema
-> $ systemctl reboot

obs: na tela de login escolher Sway Window Manager

4. Conectar e baixar os arquivos necessários do Github
-> # apt install -t bullseye-backports git
-> $ git clone https://github.com/hiromitimiyashita/Debian-Sway
-> # 

# configurar o sway 
1. copiar o arquivo de configuração
-> $ mkdir ~/.config/sway
-> $ cp /etc/sway/config ~/.config/sway/

2. edição básica do sway, ~/.config/sway/config:
-> set $term terminator
-> set $menu exec wofi --show drunalex
-> # configurar o teclado para japonês e abnt2
-> input * {
	xkb_layout "jp, br"
	xkb_model "jp106"
	xkb_options "grp:alt_space_toggle"
}
-> exec nm-applet --indicator
-> bar {
	swaybar_command waybar
}
-> font pango: Cantarell 11
-> #gaps outer 1
-> #gaps inner 5
-> default_border pixel 5

-> set $mode_system System (e)xit, (s)leep, (r)eboot, (p)oweroff
-> mode "$mode_system" {
	bindsym e exec swaymsg exit, mode "default"
	bindsym r exec systemctl reboot, mode "default"
	bindsym p exec systemctl poweroff, mode "default"
	bindsym s exec systemctl syspend, mode "default"
	
	# back to normal: Enter or Escape
	bindsym Return mode "default"
	bindsym Escape mode "default"
}
-> bindsym $mod+Shift+x mode "$mode_system"

-> set $menu exec wofi --show drun




# configuraçao do waybar
1. copiar o arquivo de configuração
-> $ mkdir ~/.config/waybar
-> cp /etc/xdg/waybar/* ~/.config/waybar/







# programas essenciais
## compactadores e descompactadores
-> sudo apt install p7zip-full p7zip-rar lzma lzma-dev rar unzip unrar-free p7zip ncompress file-roller

## explorador de arquivos e outros programas
-> sudo apt install nautilus gedit gedit-plugins eog eog-plugins firefox-esr firefox-esr-l10n-pt-br

## instalação do Nodejs e npm
--> https://nodejs.org/en/download/

## instalação do tree-sitter-cli
-> sudo npm install -g tree-sitter-cli
 
 # instalação da fonts Adobe
 -> git clone https://github.com/adobe-fonts/source-code-pro
 -> fc-cache -vf






--> icons
sudo apt install papirus-icon-theme arc-theme libreoffice libreoffice-style-papirus eog
