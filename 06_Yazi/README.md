# Yazi – Blazingly fast Terminal-Dateimanager

**Yazi** ist ein extrem schneller, moderner Dateimanager für dein Terminal – geschrieben in Rust, mit Vim-ähnlicher Steuerung und vielen Extras.

## Features im Überblick

- Blazingly fast durch Rust
- Vim-ähnliche Steuerung (h, j, k, l)
- Vorschau für Bilder, PDFs, Videos & mehr
- Tabs & Split-View
- Mausunterstützung

## Installation (Linux/macOS)

- https://yazi-rs.github.io/docs/installation
- sudo pacman -S ttf-nerd-fonts-symbols

## Schnellstart

```bash
yazi  # startet Yazi im aktuellen Ordner
```

### Shell-Wrapper: 

- https://yazi-rs.github.io/docs/quick-start

```
vim ~/.bashrc
```

1. `y` statt `yazi` ausführen
2. Mit `q` beenden → aktuelles Verzeichnis ändert sich
3. Mit `Q` beenden → bleibt im ursprünglichen Verzeichnis

## Konfiguration:

- https://github.com/sxyazi/yazi/tree/shipped/yazi-config/preset

## Wichtige Tastenbefehle
- `h` / `j` / `k` / `l` – Navigation  
- `q` – beenden  
- `.` – versteckte Dateien ein-/ausblenden  
- `a` – Ordner / Datei anlegen  
- `<Leertaste>` – Datei zur Auswahl hinzufügen  
- `v` – Selektieren 
- `x` – Datei ausschneiden 
- `y` – kopieren (in Zwischenablage legen)  
- `p` – einfügen (aus Zwischenablage einfügen)  
- `d` – löschen (Dateien/Ordner löschen)  
- `r` – umbenennen, auch bulk rename möglich
- `,` – Sortieren 
- `m` – Fileinfos in Treeansicht 
- `Tab` – Fileinfo pro Datei 

## Image Preview

- Kitty oder Ghostty funktionieren gut

## kein drag & drop mehr

Mit `c c` oder `c f` Dateipfad oder Namen kopieren und dann einfügen in Browser.

## bulk rename

- mehrere Datein Selektieren
- r 
- nvim öffnet sich
- strg+v 
- Selektieren
- I 
- `1_`
- esc und es steht nun 1_ an der ersten Stelle von allen Dateien
- ab 2 eintrag markieren mit strg+v 
- g + strg a
- speichern mit wq


---
