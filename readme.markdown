# my pop!os installation guide


## OS and hardware
[download pop!os](https://pop.system76.com/)  
i have chosen non nvidia drivers version, but this drivers can be installed via pop shop  
  
### tplink archer t3u ac1300
[driver tplink](https://github.com/cilynx/rtl88x2BU)  
i removed my wlan to install an external GPU, so to keep my wifi i bought a tplink archer  
  
clone repo  
install "dkms" and "make" if they already aren't installed  
  
```console
$ cd rtl88x2bu  
$ VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)  
$ sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}  
$ sudo dkms add -m rtl88x2bu -v ${VER}  
$ sudo dkms build -m rtl88x2bu -v ${VER}  
$ sudo dkms install -m rtl88x2bu -v ${VER}  
$ sudo modprobe 88x2bu  
```
  
### shortcuts
hide all windows = super+d  
nautilus = super+e  
gnome-system-monitor = ctrl+shift+esc  
  
### local time
[explanation for local time](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)  
to put an end in linux and windows clock fighting  
  
```console
$ timedatectl set-local-rtc 1 --adjust-system-clock  
```
  
### tilix
tilix is my favorite terminal emulator until now, due to its split screen mode, shortcut in quake style and themes  
```console
$ sudo apt-get install tilix  
```
  
add shortcut with tilix --quake  
```console
with ctrl+' and ctrl+`  
```
  
### vim
to keep sanity install vim, the old vi shortcuts and concepts are hard to use  
```console
$ sudo apt-get install vim
```
  
### gnome-tweaks
in this distro gnome-tweaks can be installed via pop shop  
  
### alternate tab
[alternateTab](https://extensions.gnome.org/extension/15/alternatetab/)  
makes alt+tab windows-like  
  
### dash to panel
[dashToPanel](https://extensions.gnome.org/extension/1160/dash-to-panel/)  
puts taskbar in bottom, and add a start button  
  
  
## daily utils
  
### chrome
default chrome comes with proprietary audio and video codecs to make navigation easier  
  
[download chrome](https://www.google.com.br/chrome/)  
i prefer .deb install over repository install because it needs a proprietary repository  
and update verifications time is affected when have several repositories added  
  
remove firefox  
```console
$ sudo apt-get remove firefox  
```
  
### snap
```console
$ sudo apt-get install snapd  
```
  
### rambox
```console
$ sudo snap install rambox
```
  
  
## working environment
  
### vscode
in this distro vscode can be installed via pop shop  
to install my current extensions:  
```console
$ code --install-extension alefragnani.Bookmarks
$ code --install-extension alexcvzz.vscode-sqlite
$ code --install-extension joaompinto.vscode-graphviz
$ code --install-extension ms-python.python
$ code --install-extension patbenatar.advanced-new-file
$ code --install-extension VisualStudioExptTeam.vscodeintellicode
$ code --install-extension zhuangtongfa.material-theme
```
*the command above was provided by this command:*  
```console
$ code --list-extensions | xargs -L 1 echo code --install-extension
```
  
### thefuck
[thefuck github](https://github.com/nvbn/thefuck)  
it's a great extension to correct and execute commands when it was spelled wrong
```console
$ sudo apt update
$ sudo apt install python3-dev python3-pip python3-setuptools
$ sudo pip3 install thefuck
```
  
### dotnet core
[download dotnet core for ubuntu](https://docs.microsoft.com/pt-br/dotnet/core/install/linux-package-manager-ubuntu-1910)  
```console
$ wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb  
$ sudo dpkg -i packages-microsoft-prod.deb  
$ sudo apt-get update  
$ sudo apt-get install apt-transport-https  
$ sudo apt-get update  
$ sudo apt-get install dotnet-sdk-3.1  
```
  
### docker
[docker install](https://docs.docker.com/engine/install/ubuntu/)  
```console
$ sudo apt-get remove docker docker-engine docker.io containerd runc  
$ sudo apt-get update  
$ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common  
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -  
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"  
$ sudo apt-get update  
$ sudo apt-get install docker-ce docker-ce-cli containerd.io  
```
  
[post-install](https://docs.docker.com/engine/install/linux-postinstall/)  
```console
$ sudo groupadd docker  
$ newgrp docker  
$ sudo usermod -aG docker $USER  
```
  
### tig
tig is the best text interface for git which i ever used  
```console
$ sudo apt install tig  
```