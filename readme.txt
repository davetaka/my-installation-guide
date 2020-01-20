my fedora installation guide

https://getfedora.org/en/workstation/download/
actually is version 31
or create in fedora
$ sudo dnf install liveusb-creator

first of all, in this laptop i have problems with fedora 31 and nvidia graphic card
so what i've to do is to follow this guide until remove nouveau

the commands are:
$ sudo -i
$ dnf update
$ reboot
$ dnf install kernel-devel kernel-headers gcc make dkms acpid libglvnd-glx libglvnd-opengl libglvnd-devel pkgconfig
$ echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
Append ‘rd.driver.blacklist=nouveau’ to end of ‘GRUB_CMDLINE_LINUX=”…”‘.
$ grub2-mkconfig -o /boot/grub2/grub.cfg
ou
$ grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
$ dnf remove xorg-x11-drv-nouveau
$ mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img
$ dracut /boot/initramfs-$(uname -r).img $(uname -r)

maybe in future i'll install the nvidia drivers correctly


tplink archer t3u ac1300

i need this because i has removed my wlan to install an external GPU, so to keep my wifi i buyed a tplink archer
 
https://github.com/cilynx/rtl88x2BU

clone repo
install dkms and make if not already installed

$ cd rtl88x2bu
$ VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
$ sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
$ sudo dkms add -m rtl88x2bu -v ${VER}
$ sudo dkms build -m rtl88x2bu -v ${VER}
$ sudo dkms install -m rtl88x2bu -v ${VER}
$ sudo modprobe 88x2bu



guake

guake is my favorite terminal emulator, just because tabs and shortcut in quake style
$ sudo dnf install guake

adjust configurations at your taste, i don't have any specific preferences, just the transparency
add shortcut with guake -t
with ctrl+' and ctrl+`



shortcuts

hide all windows = super+d
nautilus = super+e
gnome-system-monitor = ctrl+shift+esc



enable third party repositories

chrome

can be installed via software app
$ sudo dnf remove firefox


vscode

$ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
$ sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
$ sudo dnf check-update 
$ sudo dnf install code



gnome-tweakes

$ sudo dnf install gnome-tweaks



alternate tab

install via software app alternateTab



dash to panel

install via software app dashToPanel



grub customizer

$ sudo dnf install grub-customizer


