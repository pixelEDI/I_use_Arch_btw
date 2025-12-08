# Hyprland unter Debian Trixie

Diese Anleitung zeigt dir wie du Hyprland sauber unter Debian Trixie einrichtest. Da Hyprland noch nicht vollständig in den stabilen Repositories liegt, verwendest du am besten den Easy Installer von JaKooLit. Damit sparst du dir manuelle Konfigurationen und bekommst ein funktionierendes Setup.

## Easy Installer

GitHub
[https://github.com/JaKooLit/Debian-Hyprland](https://github.com/JaKooLit/Debian-Hyprland)

Offizielle Hinweise
[https://wiki.hypr.land/Getting-Started/Installation/](https://wiki.hypr.land/Getting-Started/Installation/)

Hyprland ist aktuell nur in Debian SID direkt verfügbar. Unter Trixie gibt es kein apt Paket. Der Installer übernimmt die Einrichtung automatisch und richtet alle benötigten Komponenten ein.

## Voraussetzungen prüfen

System aktualisieren

```bash
sudo apt-get update
sudo apt-get upgrade
```

Wayland prüfen

```bash
echo $XDG_SESSION_TYPE
ps -e | grep -i wayland
```

Quellen prüfen

```bash
sudo vim /etc/apt/sources.list
```

Die src Zeile muss aktiv sein.

Wenn der Installer SDDM entfernt ist das normal. GNOME bleibt aktiv. Du kannst Hyprland jederzeit direkt aus einem TTY starten

```bash
hyprland
```
