# Linux Debian/Ubuntu Passwort zurücksetzen via GRUB

Einfache Methode zum Zurücksetzen von Passwörtern auf Linux-Systemen mit GRUB-Bootloader.

## 🎥 Video-Anleitung

<https://youtu.be/dRS-LJPJr24>

## ⚡ Schnellanleitung

1. **Server neu starten** und bei GRUB-Menü **`e`** drücken
2. Zeile mit `linux` finden (beginnt meist mit `linux /boot/vmlinuz...`)
3. **Am Ende der Zeile** hinzufügen:
```
   init=/bin/bash
```
4. **Ctrl + X** oder **F10** zum Booten
5. Im Terminal eingeben:
```bash
   mount -o remount,rw /
   passwd benutzername
   exec /sbin/init
```

**Voraussetzung:** Physischer Zugang zur Konsole (oder IPMI/iLO/KVM)

## ⚠️ Hinweis
Diese Methode setzt voraus, dass die Festplatte **nicht verschlüsselt** ist.

