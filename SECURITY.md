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

---

<a name="english"></a>

# Security policy — English

## Reporting a vulnerability

Please do **not** report security issues through public issues. Use GitHub's
private reporting instead: the **Security** tab → **Report a vulnerability**.
The report stays visible to the maintainer only until a fix is available.

Useful details: affected version, operating system and session type (X11 or
Wayland), steps to reproduce, and the possible impact. You can normally expect
an acknowledgement within 7 days.

## What the app does with your data

- **Everything stays on your device.** Image processing, the history and the text
  recognition (OCR) run entirely locally.
- **One network request only.** The app checks the GitHub releases for a newer
  version. It can be switched off in the settings. Nothing else leaves the
  device — no telemetry, no analytics, no user accounts.
- **Updates are verified.** Downloads are restricted to GitHub hosts and checked
  against the size and SHA-256 digest published with the release. The app never
  installs on its own; installation is handed to the system installer.
- **Captures are private.** Screenshots, thumbnails and temporary files are
  created with file mode `0600` and their directories with `0700`. On machines
  with several user accounts nobody else can read them.
