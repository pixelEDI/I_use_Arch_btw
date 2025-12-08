# Starship Setup für eine schnelle und klare Shell

Mein Video: <https://youtu.be/UMk0xDheRvQ>

Dieses Repository zeigt wie du Starship unter Zsh einrichtest und erweiterst. Starship ist ein moderner Prompt der schnell lädt und sehr gut anpassbar ist. Mehr Infos findest du auf der offiziellen Seite  
https://starship.rs

## Installation in Zsh

Füge diese Zeile in deine `.zshrc` ein

```sh
eval "$(starship init zsh)"
````

## Starship Presets

Hier findest du viele fertige Designs die du direkt übernehmen kannst
[https://starship.rs/presets/#bracketed-segments](https://starship.rs/presets/#bracketed-segments)

## Zsh Autosuggestions

Empfehlung für komfortables Tippen
[https://github.com/zsh-users/zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

## Eigene Icons für Arduino und PlatformIO

Lege die Datei `~/.config/starship.toml` an oder erweitere sie

```toml
[custom.ino]
when = 'test -f *.ino'
symbol = "♾ "
format = "[$symbol]($style)"
style = "bold cyan"

[custom.pio]
when = 'test -f platformio.ini'
symbol = "♾ "
format = "[$symbol]($style)"
style = "bright-blue"
```

## Betriebssystem Logo einfügen

Du kannst in der `starship.toml` auch ein OS Symbol einblenden. Beispiel

```toml
[os]
disabled = false
style = "bold cyan"
```

Passe Farbe und Stil einfach an deinen Geschmack an.

Viel Spaß mit Starship
