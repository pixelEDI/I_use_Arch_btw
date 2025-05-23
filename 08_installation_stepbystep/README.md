# Arch Linux Installation – Schritt-für-Schritt-Anleitung

Meine Notizen zur Installation:
Original Anleitung: <https://wiki.archlinux.org/title/Installation_guide>

## Vorbereitung

- ISO herunterladen und prüfen
- Bootfähigen USB-Stick erstellen
- Vom USB starten (Live-System)

## SSH-Zugang vorbereiten

iwctl
station wlan0 connect "SSID"
exit

#### Falls Probleme:
iwctl
device list
station wlan0 scan
station wlan0 get-networks

### IP-Adresse prüfen
ip a

### root-Passwort setzen
passwd

### SSH starten
systemctl start sshd

## Verbindung vom anderen Rechner
ssh root@<IP-ADRESSE>

## Terminal-Setup und Verbindungstest

export TERM=xterm
ping -c 3 archlinux.org

## Partitionierung

lsblk
oder
fdisk -l

# Partitionen anlegen/löschen
`cfdisk /dev/nvme0n1`

- Beispiel:
- /dev/nvme0n1p1 EFI System (300M)
- /dev/nvme0n1p2 Linux swap (4G oder mehr)
- /dev/nvme0n1p3 Linux filesystem (Rest)

# Dateisysteme erstellen und mounten
```
mkfs.fat -F32 /dev/nvme0n1p1
mkswap /dev/nvme0n1p2
swapon /dev/nvme0n1p2
mkfs.ext4 /dev/nvme0n1p3


mount /dev/nvme0n1p3 /mnt
mkdir /mnt/boot
mount /dev/nvme0n1p1 /mnt/boot
```
# Basissystem installieren

`pacstrap -K /mnt base linux linux-firmware sudo vim networkmanager`

# Konfiguration im neuen System

```
genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt

ln -sf /usr/share/zoneinfo/Europe/Vienna /etc/localtime
hwclock --systohc
```

# Sprache

`vim /etc/locale.gen`

# en_US.UTF-8 UTF-8 aktivieren

```
locale-gen
echo LANG=en_US.UTF-8 > /etc/locale.conf

```

# Hostname

```
echo "arch" > /etc/hostname
vim /etc/hosts
```

Inhalt:
```
127.0.0.1 localhost
::1       localhost
127.0.1.1 arch
```
# Passwort für root

`passwd`

# Bootloader installieren (systemd-boot)

```
pacman -S efibootmgr
bootctl install
```

`vim /boot/loader/loader.conf`

Inhalt:
```
 default  arch.conf
 timeout  10
 console-mode max
 editor   no
```

`vim /boot/loader/entries/arch.conf`


Beispiel (UUID ersetzen mit blkid):

```
title   Arch Linux
linux   /vmlinuz-linux
initrd  /initramfs-linux.img
options root=UUID=<deine-UUID> rw quiet
```
Testen: `bootctl status`

# Benutzeroberfläche (i3) installieren

`pacman -S xorg-server xorg-xinit i3-wm i3status dmenu xterm ghostty networkmanager ttf-dejavu iwd iproute2 dhcpcd`

# GPU-Treiber

```
lspci | grep -i vga
pacman -S xf86-video-intel   # bei Intel-Grafik
```

ggf. xf86-video-amdgpu oder nvidia

# Benutzer einrichten

```
useradd -m -G wheel pixeledi
passwd pixeledi
EDITOR=vim visudo
```
Änderung
`%wheel ALL=(ALL) ALL einkommentieren`

# Abschließende Schritte

```
exit
umount -R /mnt
```
falls Probleme: `umount -l /mnt`

und dann `reboot`

# Danach im neuen System:

```
systemctl enable NetworkManager
systemctl enable sshd
systemctl enable dhcpcd
systemctl enable iwd

```

# i3 starten

```
startx
i3-config-wizard
```

# pacman anpassen

`sudo vim /etc/pacman.conf`

'Color' und 'Multilib' aktivieren

# Microcode

`sudo pacman -S intel-ucode`

# Fonts

`sudo pacman -S noto-fonts noto-fonts-extra ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-liberation ttf-opensans ttf-roboto`

# Yay installieren (AUR Helper)
```
sudo pacman -S git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

Optional: Paru statt Yay

# Sound

```
sudo pacman -S pulseaudio pulseaudio-alsa pavucontrol
systemctl --user start pulseaudio
systemctl --user enable pulseaudio

```

# Display-Helligkeit

```
sudo pacman -S brightnessctl
brightnessctl s 10%
brightnessctl s 100%
brightnessctl s -10%

```

