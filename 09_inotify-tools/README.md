
# 🔔 Automatisierte Dateiüberwachung mit `inotify-tools`, `rsync` und `systemd`

Dieses Projekt demonstriert, wie man unter Linux ein Verzeichnis in Echtzeit auf Änderungen überwacht und diese automatisch mit `rsync` sichert – ideal für Notizen, Skripte oder Projekte.

---

## 📦 Voraussetzungen

- Linux-System (z.B. Debian/Ubuntu)
- `inotify-tools`
- `rsync`
- optional: `systemd` für automatischen Start

Installation:
```bash
sudo apt-get update
sudo apt-get install inotify-tools rsync
````

---

## 📁 Szenario

Wir wollen das Verzeichnis `~/Documents/MyNotes` überwachen. Bei jeder Änderung (Erstellen, Löschen, Modifizieren von Dateien) wird das Verzeichnis automatisch in ein Backup-Verzeichnis (z.B. `~/Documents/MyNotesBackup`) synchronisiert.

---

## 🧪 Beispiel: Manuelle Überwachung mit `inotifywait`

```bash
inotifywait -m -r -e close_write,create,delete,move ~/Documents/MyNotes
```

Parameter:

* `-m`: Dauermodus
* `-r`: rekursiv (auch Unterverzeichnisse)
* `-e`: zu überwachende Events

---

## 📜 Automatisierung mit Bash-Skript

### 🔧 `backupnotes.sh`

```bash
#!/bin/bash

SOURCE_DIR="$HOME/Documents/MyNotes"
BACKUP_DIR="$HOME/Documents/MyNotesBackup"

echo "📡 Überwachung gestartet: $SOURCE_DIR → $BACKUP_DIR"

inotifywait -m -r -e close_write,create,delete,move "$SOURCE_DIR" | while read -r directory events filename; do
    echo "📁 Änderung erkannt: $events – $filename"
    rsync -av --delete "$SOURCE_DIR/" "$BACKUP_DIR/"
done
```

Speichern, ausführbar machen:

```bash
chmod +x backupnotes.sh
./backupnotes.sh
```

---

## ⚙️ Systemd Integration

Damit die Überwachung automatisch beim Booten startet, legen wir eine systemd-Service-Datei an:

### 🔧 `~/.config/systemd/user/backupnotes.service`

```ini
[Unit]
Description=Backup Notes via inotify and rsync

[Service]
ExecStart=%h/backupnotes.sh
Restart=always

[Install]
WantedBy=default.target
```

Aktivieren & starten:

```bash
systemctl --user daemon-reexec
systemctl --user enable --now backupnotes.service
```

---

## 🧼 Hinweise

* Achte auf absolute Pfade im Skript
* `rsync` synchronisiert auch Löschungen (`--delete`)
* Inotify hat Limits → bei vielen Dateien ggf. `fs.inotify.max_user_watches` erhöhen

---

## 📎 Nützlich für

* Obsidian/Markdown-Notizen
* Config-Dateien
* Lokale Projekte mit Cloud-Backup
* Echtzeit-Sicherung für Entwickler

---


Video-Tutorial von <https://youtube.com/@pixeledi>
