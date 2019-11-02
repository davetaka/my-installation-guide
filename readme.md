#getfedora

until this date, my favorite distro is fedora

in windows:
https://getfedora.org/

in another distro:
sudo dnf install liveusb-creator

remember!!! there's a way to create the home partition sharing two devices differents
sudo dnf install fedora-workstation-repositories

enable third party repositories for chrome, vscode, etc


#chrome
sudo dnf config-manager --set-enabled google-chrome
sudo dnf install google-chrome-stable


#vscode
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

sudo dnf check-update
sudo dnf install code


#tplink archer t3u ac1300
github.com/cilynx/rtl88x2BU

follow the instructions with dkms

#guake
sudo dnf install guake

add shortcut
ctrl+'
guake -t


#nautilus
add shortcut
win+e
nautilus

#task manager
add shortcut
shift+ctrl+escape
gnome-system-monitor

#gnome
win+d
hide all windows


#gnome tweaks
install gnome tweaks

#alternateTab
install alternate tab

#dashToPanel
install dash to panel

#docker
https://docs.docker.com/install/linux/docker-ce/fedora/

installation:
sudo dnf -y install dnf-plugins-core

sudo dnf config-manager \
    --add-repo \
    https://download.docker.com/linux/fedora/docker-ce.repo
	
sudo dnf install docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
sudo docker run hello-world

post-install configuration for run without sudo
sudo groupadd docker
sudo usermod -aG docker $USER

docker run hello-world

start with linux
sudo systemctl enable docker

#todo
add steps for disable middle click paste