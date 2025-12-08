# fzf mit bat – Dateien schnell finden und ansehen

Mein Video: <https://youtu.be/XnW6vMS16xQ>

Kombination aus [fzf](https://github.com/junegunn/fzf) und [bat](https://github.com/sharkdp/bat) für eine farbige Vorschau und schnelles Öffnen in `nvim`.

## 🔍 fzf – interaktive Dateisuche

Einfacher Start:
```bash
fzf --preview="cat {}"
````

Das zeigt Dateien im Klartext, aber ohne Syntax-Highlighting.


## 🎨 bat – schöner Ersatz für cat

Mit `bat` bekommst du Syntax-Highlighting, Zeilennummern und Git-Integration.

Beispiel mit Vorschau:

```bash
fzf --preview="bat --style=numbers --color=always {}"
```

Damit kannst du Dateien farbig durchsuchen und ihren Inhalt direkt ansehen.


## 🧠 Kombination mit Neovim

Dateien direkt aus der Vorschau heraus öffnen:

```bash
fzf -m --preview="bat --color=always {}" --bind "enter:become(nvim {+})"
```

* `-m` → erlaubt Mehrfachauswahl
* `--bind` → definiert, dass Enter die Auswahl in `nvim` öffnet


## ⚡ Praktischer Alias

Für den schnellen Zugriff kannst du dir einen Alias anlegen:

```bash
alias nf='fzf -m --preview="bat --color=always {}" --bind "enter:become(nvim {+})"'
```

Jetzt reicht ein einfaches:

```bash
nf
```

um Dateien mit Vorschau zu durchsuchen und mit Enter direkt in Neovim zu öffnen.


**Kurz gesagt:**
`fzf` findet, `bat` zeigt an, und `nvim` bearbeitet – effizient, schnell und schön.

