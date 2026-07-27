# Sicherheitsrichtlinie

## Unterstützte Versionen

Sicherheitsupdates gibt es für die jeweils aktuelle Minor-Version.

## Schwachstelle melden

Bitte **nicht** über öffentliche Issues melden, sondern vertraulich über
GitHub: Reiter **Security** → **Report a vulnerability**. Der Bericht ist nur
für die Projektbetreuung sichtbar, bis eine Korrektur bereitsteht.

Nützliche Angaben: betroffene Version, Betriebssystem und Sitzungstyp
(X11/Wayland), Reproduktionsschritte, mögliche Auswirkung. Eingangsbestätigung
in der Regel innerhalb von 7 Tagen.

## Sicherheitsdesign

- **Lokal.** Bildverarbeitung, Historie und OCR laufen vollständig auf dem
  Gerät. Der einzige Netzwerkaufruf ist der Update-Check gegen die GitHub-API
  (in den Einstellungen abschaltbar).
- **Keine Telemetrie, keine Analytics, keine Nutzerkonten.**
- **Aufnahmen sind privat.** Screenshots, Projektdaten und Vorschaubilder
  werden mit Dateirechten 0600 in Verzeichnissen mit 0700 abgelegt – andere
  Nutzer desselben Rechners können sie nicht lesen.
- **Verifizierte Updates.** Downloads kommen ausschliesslich von GitHub-Hosts
  und werden gegen die im Release hinterlegte Grösse und SHA-256-Prüfsumme
  geprüft. Installiert wird nie automatisch, sondern nur auf Klick über den
  System-Installer.
- **Prüfsummen selbst kontrollieren:** Jedes Release enthält `SHA256SUMS.txt`.

  ```bash
  sha256sum -c SHA256SUMS.txt --ignore-missing
  ```
