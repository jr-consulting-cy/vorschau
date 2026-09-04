# Vorschauen: ein Ordner je Firma, eine Adresse je Entwurf

Jeder Unterordner hier ist eine fertige Einzeldatei (`index.html`, Fotos eingebettet, noindex).
Claude baut sie mit `python3 werkzeuge/einzeldatei.py <ordner>`. Veröffentlicht wird nur durch Julian.

## Einmalig (Julian, rund 10 Minuten)
1. Leeres, öffentliches GitHub-Repository mit neutralem Namen anlegen (z. B. `vorschau`), ohne README.
2. Diesen Ordner `vorschauen/` als Repository einrichten und hochschieben:
   `cd vorschauen && git init -b main && git add . && git commit -m "Vorschauen" && git remote add origin https://github.com/jr-consulting-cy/vorschau.git && git push -u origin main`
3. Im Repository unter Settings → Pages: Source "Deploy from a branch", Branch `main`, Ordner `/ (root)`.
4. Basisadresse in `loop/STAND.md` unter "Vorschau-Basis" eintragen, z. B. `https://jr-consulting-cy.github.io/vorschau` (Organisation jr-consulting-cy, seit 3.9.2026).
   Optional eigene Domain unter Pages → Custom domain, dann die Basis entsprechend.

## Je Lauf (Julian, ein Befehl, egal wie viele neue Entwürfe)
`cd vorschauen && git add . && git commit -m "neue Entwürfe" && git push`

Danach ist jeder Entwurf unter `<Basis>/<ordner>/` erreichbar, und Claude setzt genau diese Adresse
in den Knopf der jeweiligen Mail. Die Adresse steht schon vor dem Push fest, deshalb kann die Mail
vorbereitet werden, bevor gepusht ist. Verschickt wird erst nach dem Push.

## Was nicht hier rein darf
Keine MAIL.md, keine Notizen, keine Preise, kein Sichtungsordner. Nur `index.html` je Firma.

## Namenssperre
Das Werkzeug einzeldatei.py bricht ab, wenn "Julian" oder "Riegler" in der Ausgabe stünde (auch in Kommentaren). Dann die Stelle im Entwurf ändern, nie die Sperre.

## Versand (einmalig, Julian, rund 5 Minuten)
Der Gmail-Baustein in Claude hüllt jeden Link in eine google.com-Weiterleitung (Weiterleitungshinweis
beim Empfänger). Deshalb geht der Versand direkt über Gmail per Skript `werkzeuge/mail-senden.py`.
1. Google-Konto office.julian99 → Sicherheit → Bestätigung in zwei Schritten muss an sein.
2. Dort "App-Passwörter" → neues App-Passwort, Name "Website-Flip Versand", 16 Zeichen kopieren.
3. Im Terminal ablegen (fragt das Passwort ab, es landet nur in der Keychain):
   `security add-generic-password -s gmail-app-password -a office.julian99@gmail.com -w`
Danach je Mail: `python3 werkzeuge/mail-senden.py <ordner> --an <adresse>` zeigt die Vorschau,
mit `--senden` geht sie raus und liegt in Gmail unter Gesendet.
