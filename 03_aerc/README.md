# aerc TUI Mail
Auf der Suche nach einem einfachen TUI-E-Mail-Client bin ich vorher über NeoMutt zu `aerc` gekommen. Einfacher geht's nicht, und genau da soll es auch sein. 

<https://aerc-mail.org/>

## cmnds
- `?` für keybindings
- `s` um Mails in Splitscreen zu sehen

## config
- ~/.config/aerc/
- Account-Details `accounts.conf`
- Keybindings `binds.conf`

## navigation
Wenn man in Vim gerne unterwegs ist, ist aerc genau das richtige
- `j` und `k` auf und ab
- `shift+j` bzw `k` ist für die Sidebar
- `enter` zum Bestätigen und `q` zum beenden oder zurückspringen

## verschieben 
- `:move`und leertaste alternativ `:mv`
- vorschläge werden geladen und mit Arrow-Keys auswählen

## löschen
- entweder mit select und d, kein Umweg über Trash folder
- oder per `:mv Trash` 

## Antworten 
- mail selektieren
- `:rq` für reply quote
- `ctrl+k` und `ctrl+j` spring man zwischen den feldern to from und subject wie auch text hin und her

## Attachments
- `ctrl+j` bzw `+k` zum auswählen im unteren Menü
- Achtung `shift+k` wechselt zu den anderen Nachrichten

## HTML emails
- text/html im unteren Bereich auswählen
- `:open` und die Mail wird im Browser geöffnet

## 2 accounts
- mit `ctrl+n` zwischen tabs also accounts wechseln

## carddav-query
`address-book-cmd = carddav-query -s https://mynextcloud.com/remote.php/dav/addressbooks/users/pixeledi/contacts/ -u pixeledi -p apppasswort_nichtuserpasswort %s`

## Ansicht Mails geantwortet
`Shift + T` 

## filter
`:filter -d namefrom`

## gmail
Funktioniert hervorragend mit oauth.

- https://www.maths.tcd.ie/~fionn/misc/aerc/
- https://www.dennisc.net/writing/tech/gmail-aerc

Viel Spaß mit aerc
