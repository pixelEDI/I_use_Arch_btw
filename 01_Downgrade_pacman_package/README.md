# Downgrade Pacman Packages auf Arch Linux

In diesem Repository findest du eine kurze Anleitung, wie du ein Arch Linux Package downgraden kannst, falls es nach einem Update Probleme verursacht.

## Schritte

### 1. Logs überprüfen
Überprüfe, welche Pakete du geupdatet hast, indem du das Pacman-Log filterst:
```bash
grep -i "upgraded.*rocm"  /var/log/pacman.log
```

### 2. Überprüfen, ob das alte Package im Cache ist
Schau nach, ob das alte Paket noch im Pacman-Cache vorhanden ist:
```bash
ls /var/cache/pacman/pkg/ | grep python-pytorch-rocm
```

### 3. Altes Package installieren
Falls das alte Package noch im Cache ist, installiere es mit:
```bash
sudo pacman -U /var/cache/pacman/pkg/python-pytorch-rockcam-2.5.1-7.pkg.tar.zst
```

### 4. Alternative: Paket aus dem Arch Linux Archive
Falls das alte Package nicht mehr im Cache ist, lade es aus dem Arch Linux Archive herunter:
- Gehe zu: [Arch Linux Archive](https://archive.archlinux.org/packages/)
- Suche nach deinem Paket (z.B. `python-pytorch-rockcam`)
- Kopiere den Link zur gewünschten Version und installiere es mit:
```bash
sudo pacman -U https://archive.archlinux.org/packages/p/python-pytorch-rocm/python-pytorch-rocm-2.5.1-7-x86_64.pkg.tar.zst
```

### 5. Paket ignorieren, um Updates zu verhindern
Um zu verhindern, dass Pacman das Paket bei zukünftigen Updates erneut aktualisiert, füge es zur `pacman.conf` hinzu:
```bash
sudo vim /etc/pacman.conf
```
Füge die folgende Zeile unter `IgnorePkg` hinzu:
```bash
IgnorePkg = python-pytorch-rockm
```

### 6. Testen
Starte das Programm (z.B. Whisper) und stelle sicher, dass es wieder wie erwartet funktioniert:
```bash
whisper 10.mp4
```

## Weitere Links
- https://wiki.archlinux.org/title/Downgrading_packages
- https://archive.archlinux.org/packages/

### Hinweis
Dieser Workaround hilft dir natürlich nur temporär! 
