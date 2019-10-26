#getfedora

until this date, my favorite distro is fedora

in windows:
https://getfedora.org/

in another distro:
sudo dnf install liveusb-creator

there's a way to create the home partition sharing two devices differents
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

