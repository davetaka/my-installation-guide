# my fedora installation guide

[download fedora](https://getfedora.org/en/workstation/download/)  
actually version is **31**  
or create in fedora  
```console
$ sudo dnf install liveusb-creator
```

### nvidia
first of all, in this laptop i have problems with fedora 31 and nvidia graphic card  
so what i've to do is to follow this guide until remove nouveau  
[nvidia guide](https://www.if-not-true-then-false.com/2015/fedora-nvidia-guide/)    

the commands are:  
_# dnf update_  
_# reboot_  
_# dnf install kernel-devel kernel-headers gcc make dkms acpid libglvnd-glx libglvnd-opengl libglvnd-devel pkgconfig_  
_# echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf_  
Append ‘rd.driver.blacklist=nouveau’ to end of ‘GRUB_CMDLINE_LINUX=”…”‘.  
_# grub2-mkconfig -o /boot/grub2/grub.cfg_  
ou  
_# grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg_  
_# dnf remove xorg-x11-drv-nouveau_  
_# mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img_  
_# dracut /boot/initramfs-$(uname -r).img $(uname -r)_    

maybe in future i'll install the nvidia drivers correctly      


### tplink archer t3u ac1300
i need this because i has removed my wlan to install an external GPU, so to keep my wifi i buyed a tplink archer  
[driver tplink](https://github.com/cilynx/rtl88x2BU)    

clone repo  
install dkms and make if not already installed    

_$ cd rtl88x2bu_  
_$ VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)_  
_$ sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}_  
_$ sudo dkms add -m rtl88x2bu -v ${VER}_  
_$ sudo dkms build -m rtl88x2bu -v ${VER}_  
_$ sudo dkms install -m rtl88x2bu -v ${VER}_  
_$ sudo modprobe 88x2bu_      


### tilix
tilix is my favorite terminal emulator, just because tabs and shortcut in quake style and themes  
_$ sudo dnf install tilix_    

add shortcut with tilix --quake  
with ctrl+' and ctrl+`      


### shortcuts
hide all windows = super+d  
nautilus = super+e  
gnome-system-monitor = ctrl+shift+esc      


**enable third party repositories**    

### chrome
can be installed via software app  
_$ sudo dnf remove firefox_      


### vscode
_$ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc_  
_$ sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'_  
_$ sudo dnf check-update_  
_$ sudo dnf install code_      


### gnome-tweakes
_$ sudo dnf install gnome-tweaks_      



### alternate tab
install via software app alternateTab      



### dash to panel
install via software app dashToPanel      



### grub customizer
_$ sudo dnf install grub-customizer_       


### thefuck
_$ sudo dnf install python-pip python-devel_  
_$ sudo pip install thefuck_  
[thefuck git](https://github.com/nvbn/thefuck)      


### limit number of kernels
[guide for limit kernels](https://www.linuxbabe.com/linux-server/list-installed-linux-kernels-remove-old-ones-fedora)  
_$ sudo vi /etc/dnf/dnf.conf_  
installonly_limit=2      



### dotnet core
[download dotnet core for fedora](https://docs.microsoft.com/pt-br/dotnet/core/install/linux-package-manager-fedora31)  
_$ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc_  
_$ sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo_  
_$ sudo dnf install dotnet-sdk-3.1_      


### snap
_$ sudo dnf install snapd_      

### rambox
_$ sudo snap install rambox_      