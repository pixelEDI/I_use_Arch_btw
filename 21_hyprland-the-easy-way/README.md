# Hyprland Setup mit mylinuxforwork Dotfiles

Kurze Mitschrift für eine funktionierende Hyprland Installation auf Arch Linux mit den ML4W Dotfiles.

Mein YT-Video: <https://youtu.be/yyvW46bIsfw>

## Basis Installation

System aktualisieren und benötigte Pakete installieren:

```bash
sudo pacman -Syu
sudo pacman -S hyprland rofi-wayland nwg-displays hyprcursors waybar unzip
````

Offizielle Beispielkonfigurationen findest du hier:

[https://wiki.hypr.land/Configuring/Example-configurations/](https://wiki.hypr.land/Configuring/Example-configurations/)

Ab hier kannst du entweder selbst ricing betreiben oder direkt die mylinuxforwork Dotfiles nutzen.

## mylinuxforwork Dotfiles Installation

Flatpak installieren:

```bash
sudo pacman -S flatpak
```

Dotfiles Installer installieren und starten:

```bash
flatpak install com.ml4w.dotfilesinstaller
flatpak run com.ml4w.dotfilesinstaller
```

Danach das Programm „Hyprland Settings“ öffnen und die Konfiguration nach Bedarf anpassen.

## Links

Dokumentation und Installer:
[https://mylinuxforwork.github.io/dotfiles/getting-started/install](https://mylinuxforwork.github.io/dotfiles/getting-started/install)

Direkte Dotfiles Definition:
[https://raw.githubusercontent.com/mylinuxforwork/dotfiles/main/hyprland-dotfiles-stable.dotinst](https://raw.githubusercontent.com/mylinuxforwork/dotfiles/main/hyprland-dotfiles-stable.dotinst)
