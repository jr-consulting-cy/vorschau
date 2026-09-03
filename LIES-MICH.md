# Vorschauen: ein Ordner je Firma, eine Adresse je Entwurf

Jeder Unterordner hier ist eine fertige Einzeldatei (`index.html`, Fotos eingebettet, noindex).
Claude baut sie mit `python3 werkzeuge/einzeldatei.py <ordner>`. Veröffentlicht wird nur durch Julian.

## Einmalig (Julian, rund 10 Minuten)
1. Leeres, öffentliches GitHub-Repository mit neutralem Namen anlegen (z. B. `vorschau`), ohne README.
2. Diesen Ordner `vorschauen/` als Repository einrichten und hochschieben:
   `cd vorschauen && git init -b main && git add . && git commit -m "Vorschauen" && git remote add origin <repo-url> && git push -u origin main`
3. Im Repository unter Settings → Pages: Source "Deploy from a branch", Branch `main`, Ordner `/ (root)`.
4. Basisadresse in `loop/STAND.md` unter "Vorschau-Basis" eintragen, z. B. `https://<konto>.github.io/vorschau`.
   Optional eigene Domain unter Pages → Custom domain, dann die Basis entsprechend.

## Je Lauf (Julian, ein Befehl, egal wie viele neue Entwürfe)
`cd vorschauen && git add . && git commit -m "neue Entwürfe" && git push`

Danach ist jeder Entwurf unter `<Basis>/<ordner>/` erreichbar, und Claude setzt genau diese Adresse
in den Knopf der jeweiligen Mail. Die Adresse steht schon vor dem Push fest, deshalb kann die Mail
vorbereitet werden, bevor gepusht ist. Verschickt wird erst nach dem Push.

## Was nicht hier rein darf
Keine MAIL.md, keine Notizen, keine Preise, kein Sichtungsordner. Nur `index.html` je Firma.
