# Age und Rage Verschlüsselung

- Quelle <https://github.com/FiloSottile/age>
- Blazingly fast Variante von age: <https://github.com/str4d/rage>
- Mein Video: <https://youtu.be/PrfwzmFwO7k> 

Dieses Repo zeigt dir wie du Dateien mit age oder rage sicher verschlüsselst.  

Du kannst mit age verschlüsseln und mit rage entschlüsseln und umgekehrt. Beide Tools sind kompatibel.

## Schlüssel mit key.txt nutzen

Key erzeugen

```
age-keygen -o key.txt
```

Public Key anzeigen

```
cat key.txt
```

Verschlüsseln

```
age -r DEIN_PUBLIC_KEY -o iusearchbtw.csv.age iusearchbtw.csv
```

Entschlüsseln

```
age -d -i key.txt iusearchbtw.csv.age > iusearchbtw.csv
```

## SSH Keys verwenden

SSH Key nutzen ist einfacher. Du brauchst keinen extra age Key.  
Es geht mit deinem vorhandenen id_ed25519 Key Paar.

Verschlüsseln mit SSH Public Key

```
age -R ~/.ssh/id_ed25519.pub iusearchbtw.csv > iusearchbtw.csv.age
```

Entschlüsseln mit SSH Private Key

```
age -d -i ~/.ssh/id_ed25519 iusearchbtw.csv.age > iusearchbtw.csv
```

## Rage als Rust Alternative

Rage nutzt die gleichen Keys und ist voll kompatibel.

Verschlüsseln

```
rage -r ~/.ssh/id_ed25519.pub -o iusearchbtw.csv.age iusearchbtw.csv
```

Entschlüsseln

```
rage -d -i ~/.ssh/id_ed25519 iusearchbtw.csv.age > iusearchbtw.csv
```

Fertig. Du kannst frei zwischen age und rage wechseln.
