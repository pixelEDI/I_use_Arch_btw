# Foot Terminal

https://codeberg.org/dnkl/foot/wiki#user-content-jumping-between-prompts

Foot ist ein schneller, schlanker und Wayland nativer Terminal Emulator für Linux.

## Warum Foot?

Für meinen Workflow soll der Terminal Emulator vor allem eines machen: Terminal Emulation.

Andere Aufgaben übernehmen separate Tools:

* Niri: Fensterverwaltung
* tmux: Sessions und Splits
* Yazi: Dateiverwaltung
* Foot: Terminal Emulation

Das passt gut zum Unix Gedanken: `Do one thing and do it well.`

## Wichtige Features

* Wayland nativ
* sehr geringer Ressourcenverbrauch
* Sixel Support für Bilder im Terminal
* True Color und Color Emoji
* Scrollback Suche
* Tastatur gesteuerter URL Mode
* Shell Integration über OSC 7 und OSC 133
* optionaler Servermodus mit `footclient`
* einfache INI Konfiguration

## Yazi und Sixel

Für mich einer der wichtigsten Punkte: Foot unterstützt Sixel und kann dadurch Bildvorschauen in Yazi direkt im Terminal darstellen.

```bash
yazi
```

## Nützliche Shortcuts

```text
Ctrl+Shift+O   URL Mode
Ctrl+Shift+R   Scrollback Suche
Ctrl+Shift+N   neues Terminal
Ctrl+Shift+Z   vorheriger Prompt
Ctrl+Shift+X   nächster Prompt
```


Vorteile sind geringerer gemeinsamer Speicherverbrauch und schnelleres Öffnen neuer Fenster. Dafür hängen alle Fenster am gleichen Serverprozess.

## Konfiguration

```text
~/.config/foot/foot.ini
```

Beispiel:

```ini
include=~/.config/foot/colors.ini

[colors-dark]
alpha=0.8

[main]
font=JetBrains Mono:size=13
pad=0x0 center
dpi-aware=no

[mouse]
hide-when-typing=yes
```

## Fazit

Foot ist nicht interessant, weil es möglichst wenig kann. Es konzentriert sich auf Terminal Emulation und bringt trotzdem moderne Funktionen wie Wayland Support, Sixel und Shell Integration mit.
