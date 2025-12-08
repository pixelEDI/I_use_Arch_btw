# sed und awk

- Mein Video: <https://youtu.be/B_uY-4JPDkc>
- 🧪 Übungsdateien zum Mitmachen https://www.pixeledi.eu/freebies?link=116


## Teil 1 – die Beispieldatei 

```csv
id,name,role,shell,home
1,markus,admin,/bin/bash,/home/markus
2,anna,user,/bin/zsh,/home/anna
3,tom,user,/bin/bash,/home/tom
4,lara,admin,/bin/fish,/home/lara
```

→ liegt im Ordner 02_files/people.csv


## Teil 2 – Einstieg in awk 

awk teilt jede Zeile in sogenannte Felder, standardmäßig durch Leerzeichen getrennt.  
Mit -F änderst du das Trennzeichen (Field Separator). Bei CSV-Dateien ist das Komma:

```bash
awk -F, '{print $2}' 02_files/people.csv
```

- -F, → Komma als Trennzeichen
- {print $2} → gib die zweite Spalte jeder Zeile aus (also name)

nur Zeilen, in denen in Spalte 3 „admin“ steht:

```bash
awk -F, '$3=="admin" {print $2}' 02_files/people.csv
```

- $3=="admin" → Bedingung: dritte Spalte ist „admin“
- {print $2} → Aktion: gib zweite Spalte (Name) aus

mehrere Spalten:

```bash
awk -F, '{print $2 " → " $4}' 02_files/people.csv
```

- " → Zeichenkette
- " → " → Text zwischen Spalten, um die Ausgabe zu trennen


## Teil 3 – formatierte Ausgabe

awk kann Spalten schön ausrichten. Mit printf steuerst du das Format genau:

```bash
awk -F, 'NR>1 {printf "%-10s | %-8s | %s\n", $2, $3, $4}' 02_files/people.csv
```

- NR>1 → überspringt die Kopfzeile (NR = Number of Records = Zeilennummer)
- printf → wie in C oder Bash, formatiert Text
- %-10s → Textfeld, links ausgerichtet, 10 Zeichen breit
- | → Trennsymbol
- %-8s → 8 Zeichen breit
- %s\\n → Text + Zeilenumbruch

ergibt:

```
markus     | admin    | /bin/bash
anna       | user     | /bin/zsh
...
```


## Teil 4 – Auswerten mit awk 

Zählen nach Rolle:

```bash
awk -F, 'NR>1 {role[$3]++} END {for (r in role) print r, role[r]}' 02_files/people.csv
```

- role\[$3\]++ → zählt, wie oft eine Rolle vorkommt
- END {…} → wird nach allen Zeilen ausgeführt
- for (r in role) → Schleife über alle Rollen
- print r, role\[r\] → gibt Rolle und Anzahl aus

Zeilen zählen:

```bash
awk 'END {print NR-1, "Benutzer"}' 02_files/people.csv
```

- NR → aktuelle Zeilennummer, hier also Gesamtzahl
- NR-1 → minus Kopfzeile


## Teil 5 – sed für schnelle Änderungen 

sed ist ein Stream Editor, perfekt für Ersetzungen oder Zeilenoperationen.

Text ersetzen:

```bash
sed -i 's/user/member/' 02_files/people.csv
```

- -i → ändert die Datei direkt (in-place)
- s/alt/neu/ → „substitute“: ersetzt ersten Treffer „user“ durch „member“

Zeilen löschen:

```bash
sed -i '/fish/d' 02_files/people.csv
```

- /fish/ → Muster, nach dem gesucht wird
- d → löscht Zeilen mit diesem Muster

Kopfzeile löschen, Rest anzeigen:

```bash
sed '1d' 02_files/people.csv
```

- 1d → löscht Zeile 1 (Header)


## Teil 6 – Kombination aus sed und awk 

zuerst mit sed filtern, dann mit awk auswerten:

```bash
sed '/bash/d' 02_files/people.csv | awk -F, 'NR>1 {print $2, $3}'
```

- sed '/bash/d' → entfernt Zeilen mit „bash“
- | → leitet Ergebnis an awk weiter
- awk -F, 'NR>1 {print $2, $3}' → zeigt Name und Rolle der übrigen


## Fazit

„sed bearbeitet Text, awk versteht ihn spaltenweise. Zusammen sind sie wie ein Schweizer Taschenmesser für jede Shell-Aufgabe – schnell, mächtig und überall verfügbar.“
