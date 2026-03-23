# Zoxide

* Zoxide: [https://github.com/ajeetdsouza/zoxide](https://github.com/ajeetdsouza/zoxide)
* Integration in Yazi: https://github.com/sxyazi/yazi
* Video: [https://youtu.be/gLkZaiY1GcQ](https://youtu.be/gLkZaiY1GcQ)

Zoxide ist ein smarter `cd` Ersatz für das Terminal. Es merkt sich häufig genutzte Ordner und bringt dich mit kurzen Suchbegriffen direkt an dein Ziel.

## Shell Integration mit Bash

```bash
echo 'eval "$(zoxide init bash)"' >> ~/.bashrc
source ~/.bashrc
```

## Beispiele

```bash
z proj
zi
```

`z proj` springt in einen passenden, häufig genutzten Ordner.
`zi` zeigt dir eine interaktive Liste deiner gespeicherten Verzeichnisse.

