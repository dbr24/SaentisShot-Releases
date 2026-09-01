# SäntisShot — Screenshot-Tool für Linux und macOS 🏔️📸

*Deutsch · [English below](#english)*

**SäntisShot ist ein kostenloses Screenshot-Programm für Linux und macOS**
(unter Linux X11 und Wayland) mit Bereichsauswahl, **Scrolling-Screenshots**
(ganze Webseiten in einem Bild), einem Annotations-Editor, **Texterkennung
(OCR)** und einer Historie.

SäntisShot gibt es für **Linux Mint**, **Ubuntu**, **Pop!_OS**, **CachyOS** und
**macOS (Apple Silicon)** – und nur für diese. Für andere Systeme bieten wir
bewusst nichts an: Wir könnten es dort weder prüfen noch unterstützen.

**Geprüft** haben wir Linux Mint, Ubuntu, CachyOS und macOS. Pop!_OS nutzt
dasselbe Paket wie Ubuntu und wurde von einem Nutzer installiert.

### ⬇️ [Aktuelle Version herunterladen](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

> Dieses Repository enthält ausschliesslich die **fertigen Installationspakete**.
> Der Quellcode wird nicht veröffentlicht.

## Was kann SäntisShot?

| | |
|---|---|
| **Aufnehmen** | Ganzer Bildschirm, einzelnes Fenster, frei gewählter Bereich – oder **scrollend**, wenn die Seite länger ist als der Bildschirm |
| **Bearbeiten** | Pfeile, Linien, Rechtecke, Kreise, Text, Nummern-Stempel, Schatten; Elemente rasten aneinander ein |
| **Unkenntlich machen** | Verpixeln sensibler Stellen – nachträglich verschiebbar und drehbar |
| **Text auslesen** | OCR direkt aus dem Bild, vollständig offline (Tesseract) |
| **Verwalten** | Historie nach Datum, verlustfreie Projekte, Export als PNG, JPG oder WebP |
| **Sprache** | Oberfläche auf **Deutsch und Englisch**, folgt der Systemsprache |

**Datenschutz:** Alles läuft lokal auf dem Gerät. Der einzige Netzwerkaufruf ist
die Suche nach Updates auf GitHub, und die lässt sich abschalten. Keine
Telemetrie, keine Konten, keine Cloud.

## Häufige Fragen

**Ist SäntisShot kostenlos?** Ja. Lizenz: Elastic License 2.0.

**Funktioniert es unter Wayland?** Ja. Wayland lässt Programme aus
Sicherheitsgründen nicht selbst den Bildschirm lesen, deshalb wird ein natives
Werkzeug benötigt (`grim`+`slurp`, `gnome-screenshot` oder `kde-spectacle`,
siehe unten). Unter X11 ist nichts zusätzlich nötig.

**Kann es ganze Webseiten aufnehmen?** Ja – der Scrolling-Screenshot nimmt
laufend Bilder auf und fügt sie automatisch zu einem hohen Bild zusammen.

**Gibt es eine Version für Windows oder macOS?** Für macOS (Apple Silicon) gibt
es ein `.dmg` – siehe [Installation](#-macos-apple-silicon). Für Windows und für
Intel-Macs gibt es zurzeit kein Paket.

## Installation

### Welche Datei brauche ich?

Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
liegen mehrere Dateien. Die richtige findest du hier:

| Dein System | Datei | Anleitung |
|---|---|---|
| **Mac** mit Apple-Chip (M1–M4) | `SaentisShot_…_aarch64.dmg` | [macOS](#-macos-apple-silicon) |
| **Linux Mint**, Ubuntu, Pop!_OS | `SaentisShot_…_amd64.deb` | [Debian-Familie](#-linux-mint-ubuntu-und-pop_os) |
| **CachyOS** | `PKGBUILD` | [CachyOS](#-cachyos) |

Im Release liegt zusätzlich ein `AppImage` für andere Linux-Systeme. Es ist
**nicht getestet** und wird nicht unterstützt; wer es versuchen will, macht es
mit `chmod +x` ausführbar und startet es direkt.

Die Datei `SHA256SUMS.txt` brauchst du nur, wenn du den Download
[überprüfen](#download-prüfen-empfohlen) möchtest.

> **Mac mit Intel-Prozessor?** Dafür gibt es zurzeit kein Paket – die
> `aarch64`-Fassung läuft dort nicht.

Unten steht bei jedem System **der einfachste Weg zuerst**. Wer noch nie ein
Terminal benutzt hat, folgt einfach dem ersten Block – das genügt. Die kurzen
Befehle darunter sind nur eine Abkürzung für Geübte; sie holen die aktuelle
Version selbst.

> **Terminal öffnen:** unter Linux mit `Strg`+`Alt`+`T`, unter macOS mit
> `Cmd`+`Leertaste`, dann «Terminal» tippen. Befehl hineinkopieren, `Enter`.
> Beim Passwort bewegt sich nichts auf dem Bildschirm – das ist so gewollt und
> kein Fehler.

### 🐧 Linux Mint, Ubuntu und Pop!_OS

**Schritt für Schritt:**

1. Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   die Datei anklicken, die auf `_amd64.deb` endet. Sie landet im Ordner
   **Downloads**.
2. Terminal öffnen und diese eine Zeile hineinkopieren:

   ```bash
   sudo apt install -y ~/Downloads/SaentisShot_*_amd64.deb
   ```

Unter **Linux Mint** reicht auch ein Doppelklick auf die geladene Datei – die
Paketinstallation öffnet sich und macht den Rest. Bei Ubuntu und Pop!_OS
kommt es auf die Fassung an, was der Doppelklick öffnet; der Befehl oben
funktioniert dagegen überall.

**Abkürzung** – lädt und installiert in einem Rutsch:

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*_amd64\.deb' | head -n1)"
sudo apt install -y ./SaentisShot_*_amd64.deb
```

`apt` zieht die benötigten Bibliotheken selbst nach. Danach steht **SäntisShot**
im Anwendungsmenü. Empfohlen für Texterkennung (OCR):

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

> **Auf einer Wayland-Sitzung** (bei Ubuntu die Vorgabe) zusätzlich
> `sudo apt install -y gnome-screenshot` – sonst fragt GNOME bei jeder Aufnahme
> nach. Der kurze Blitz beim Auslösen kommt von GNOME selbst und lässt sich
> nicht abschalten.

*Deinstallieren:* `sudo apt remove saentisshot`

### 🐧 CachyOS

Hier führt kein Weg am Terminal vorbei: CachyOS baut das Paket selbst
zusammen. Die vier Zeilen der Reihe nach einfügen – die zweite legt einen
eigenen, leeren Ordner an, weil beim Bauen Dateien entstehen:

```bash
sudo pacman -S --needed base-devel curl          # einmalig, falls noch nicht da
mkdir -p ~/saentisshot-bau && cd ~/saentisshot-bau
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*/PKGBUILD' | head -n1)"
makepkg -si
```

> **Nicht als `root` und nicht mit `sudo makepkg` ausführen.** `makepkg`
> verweigert das grundsätzlich und bricht mit einer Fehlermeldung ab. Als
> normaler Nutzer aufrufen – nach dem Bauen fragt es von selbst nach dem
> Passwort.

Das PKGBUILD lädt das offizielle Paket, **prüft dessen SHA-256-Prüfsumme** und
installiert es als `saentisshot-bin`. Empfohlen für Texterkennung (OCR):

```bash
sudo pacman -S tesseract tesseract-data-deu tesseract-data-eng
```

*Deinstallieren:* `sudo pacman -R saentisshot-bin`

### 🍎 macOS (Apple Silicon)

**Mit der Maus:** `.dmg` von der
[Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
laden, doppelklicken und **SäntisShot** in den Ordner **Programme** ziehen.
Weiter beim Abschnitt «Beim ersten Start» unten.

**Oder im Terminal** – lädt, öffnet und legt die App nach «Programme»:

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*_aarch64\.dmg' | head -n1)"
hdiutil attach SaentisShot_*_aarch64.dmg
cp -R /Volumes/SaentisShot/SaentisShot.app /Applications/
hdiutil detach /Volumes/SaentisShot
xattr -dr com.apple.quarantine /Applications/SaentisShot.app   # Gatekeeper-Hinweis abnehmen
open /Applications/SaentisShot.app
```

#### Beim ersten Start

macOS meldet, die App könne nicht geöffnet werden (SäntisShot
ist nicht bei Apple notarisiert). Einmalig freigeben – der Weg hängt von der
macOS-Fassung ab:

- **macOS 15 (Sequoia) und neuer:** App doppelklicken, die Meldung mit
  **Fertig** schliessen. Dann **Systemeinstellungen → Datenschutz & Sicherheit**
  öffnen, nach unten scrollen zu «SaentisShot wurde blockiert …» und auf
  **Trotzdem öffnen** klicken. Mit Touch ID oder Passwort bestätigen.
  *(Der frühere Rechtsklick-Trick funktioniert ab dieser Fassung nicht mehr.)*
- **macOS 14 (Sonoma) und älter:** **Rechtsklick** auf die App → **Öffnen** →
  im Dialog nochmals **Öffnen**.

Danach startet sie immer normal. Wer den Weg abkürzen will, nimmt den
Terminal-Befehl oben – er nimmt die Markierung gleich ab.

**Zwei Dinge beim ersten Start:**

1. macOS fragt nach der Berechtigung **Bildschirmaufnahme** (Systemeinstellungen
   → Datenschutz & Sicherheit → Bildschirmaufnahme). Ohne sie nimmt jedes
   Programm unter macOS nur den Schreibtischhintergrund auf. Nach dem Erteilen
   SäntisShot einmal neu starten – danach bleibt die Berechtigung auch über
   Updates hinweg erhalten.
2. SäntisShot ist eine **Menüleisten-App**: Sie erscheint oben rechts bei den
   Symbolen, nicht im Dock.

Für Texterkennung (OCR) genügen zwei Befehle – das grosse Sprachpaket
(`tesseract-lang`, über 1 GB) braucht es nicht, SäntisShot nutzt nur Deutsch
und Englisch:

```bash
brew install tesseract
curl -fsSL https://github.com/tesseract-ocr/tessdata/raw/main/deu.traineddata \
  -o "$(brew --prefix tesseract)/share/tessdata/deu.traineddata"
```

SäntisShot legt beim ersten Erkennen eine eigene Kopie der Sprachdaten an – ein
späteres Tesseract-Update kann die Erkennung damit nicht mehr auf Englisch
zurückwerfen.

*Deinstallieren:* `rm -rf /Applications/SaentisShot.app`

### Download prüfen (empfohlen)

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*/SHA256SUMS\.txt' | head -n1)"
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Die Ausgabe muss für jede vorhandene Datei `OK` melden. Unter macOS lautet der
Befehl `shasum -a 256 -c SHA256SUMS.txt --ignore-missing`.

## Optionale Zusatzpakete

Texterkennung (OCR) im Editor:

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng   # Mint, Ubuntu, Pop!_OS
sudo pacman -S tesseract tesseract-data-deu tesseract-data-eng          # CachyOS
```

Nur bei **Wayland**-Sitzungen nötig, je nach Desktop:

```bash
sudo apt install -y grim slurp          # Sway, Hyprland
sudo apt install -y gnome-screenshot    # GNOME, Cinnamon
sudo apt install -y kde-spectacle       # KDE Plasma
```

Unter X11 (Standard bei Linux Mint) sind keine Zusatztools nötig.

## Erste Schritte

**Screenshot machen:** Drück die **Druck-Taste** (je nach Tastatur beschriftet
mit `Druck`, `Print` oder `PrtSc`). Es erscheint eine kleine Auswahl mit den vier
Aufnahmearten — Bildschirm, Fenster, Bereich, Scrollend. Wähle mit der Maus oder
den Tasten `1` bis `4`; `Enter` wiederholt die zuletzt benutzte Art.

Das Programm läuft dabei im Hintergrund. Erreichbar ist es jederzeit über das
Symbol im Infobereich neben der Uhr.

**Nach der Aufnahme** liegt das Bild sofort in der Zwischenablage — du kannst es
mit `Ctrl+V` einfügen. Unten rechts erscheint zusätzlich eine kleine Vorschau;
ein Klick darauf öffnet den Editor.

**Eine andere Taste festlegen:** *Einstellungen → Globaler Hotkey* → ins Feld
klicken und die gewünschte Taste drücken. Sie gilt sofort, `Esc` bricht ab. Für
Kombinationen `Ctrl`, `Alt`, `Shift` oder `Super` gedrückt halten.

**Die Druck-Taste tut nichts?** Dafür gibt es zwei übliche Gründe:

- **Der Desktop belegt sie selbst.** Cinnamon und GNOME legen von Haus aus ihr
  eigenes Screenshot-Werkzeug darauf. Entweder du entfernst die Belegung in den
  Tastatur-Einstellungen deines Systems, oder du legst in SäntisShot eine andere
  Taste fest.
- **Du bist in einer Wayland-Sitzung.** Dort darf kein Programm Tasten global
  abfangen. SäntisShot trägt die Taste deshalb selbst in der Tastaturbelegung
  der Arbeitsumgebung ein — bei Cinnamon und GNOME automatisch. Nachsehen kannst
  du unter *Einstellungen → Aufnahme-Taste unter Wayland*.

Fängt deine Arbeitsumgebung eine Taste ab, kommt sie beim Aufnehmen gar nicht
erst an. Für diesen Fall gibt es unter dem Feld den Weg **«Von Hand
eintragen»** — dort schreibst du sie als Text hinein, etwa `Ctrl+PrintScreen`.

## Wenn etwas nicht klappt

Geht etwas schief, erscheint unten rechts eine rote Meldung. Sie **bleibt
stehen**, bis du sie schliesst — du kannst sie also in Ruhe lesen.

Der Knopf **«Bericht kopieren»** legt diese Meldung zusammen mit den technischen
Angaben in die Zwischenablage: Version, Betriebssystem, Arbeitsumgebung,
Ablageorte und die letzten Zeilen des Protokolls. Genau das wird zur Klärung
gebraucht — füg es einfach in deine Fehlermeldung ein.

Der Bericht entsteht erst beim Klick und geht ausschliesslich in die
Zwischenablage; von selbst sendet SäntisShot nichts. Er enthält Dateipfade aus
deinem Benutzerordner — wirf vor dem Weitergeben kurz einen Blick darauf.

**Texterkennung meldet einen Fehler?** Dann fehlen meist die Sprachdateien von
Tesseract. Prüfen lässt sich das im Terminal mit `tesseract --list-langs`;
stehen dort `deu` und `eng` nicht, hilft der passende Befehl aus
[Optionale Zusatzpakete](#optionale-zusatzpakete). Auf CachyOS ist das häufig: Das Paket `tesseract` bringt dort **keine einzige**
Sprachdatei mit.

## Updates

SäntisShot prüft beim Start und danach täglich, ob hier eine neuere Version
liegt, und meldet sie in der App – das ist der einzige Netzwerkaufruf des
Programms und lässt sich in den Einstellungen abschalten. Installiert wird nur
auf ausdrücklichen Klick; der Download wird gegen Grösse und SHA-256-Prüfsumme
des Releases verifiziert und dann eingespielt – unter Linux über den
System-Installer, auf macOS im Finder zum Ziehen nach «Programme».

Willst du eine Version auslassen, drück im Update-Bereich auf **«Diese Version
überspringen»** – dann meldet sie sich nicht mehr von selbst. Wer dort später
wieder auf «Jetzt nach Updates suchen» drückt, bekommt sie trotzdem angezeigt.

## Sicherheit

Sicherheitslücken bitte **nicht** über öffentliche Issues melden, sondern
vertraulich über den Reiter **Security → Report a vulnerability**.

Alle Bildverarbeitung, die Historie und die Texterkennung laufen vollständig
lokal auf dem Gerät. Es werden keine Nutzungsdaten erhoben oder versendet.
Aufnahmen werden mit Dateirechten `0600` gespeichert – auf Rechnern mit
mehreren Benutzerkonten kann niemand sonst sie lesen.

## Lizenz

Elastic License 2.0 – siehe [LICENSE](LICENSE).

---

<a name="english"></a>

# SäntisShot — Screenshot tool for Linux and macOS

**SäntisShot is a free screenshot tool for Linux and macOS** (X11 and Wayland on
Linux) with region selection, **scrolling screenshots** (capture a whole web
page as one image), an annotation editor, **text recognition (OCR)** and a
history.

SäntisShot is available for **Linux Mint**, **Ubuntu**, **Pop!_OS**, **CachyOS**
and **macOS (Apple Silicon)** — and for those only. We deliberately offer
nothing for other systems: we could neither test nor support it there.

**Verified** on Linux Mint, Ubuntu, CachyOS and macOS. Pop!_OS uses the same
package as Ubuntu and was installed by a user.


### ⬇️ [Download the current version](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

> This repository contains the **ready-made installation packages** only. The
> source code is not published.

## What SäntisShot does

| | |
|---|---|
| **Capture** | Whole screen, a single window, a freely chosen region — or **scrolling**, when the page is taller than the screen |
| **Annotate** | Arrows, lines, rectangles, circles, text, numbered stamps, shadows; elements snap to each other |
| **Redact** | Pixelate sensitive areas — movable and rotatable afterwards |
| **Read text** | OCR straight from the image, fully offline (Tesseract) |
| **Organise** | History by date, lossless projects, export as PNG, JPG or WebP |
| **Language** | Interface in **German and English**, follows the system language |

**Privacy:** everything runs locally on your device. The only network request is
the update check against GitHub, and it can be switched off. No telemetry, no
accounts, no cloud.

## Frequently asked questions

**Is SäntisShot free?** Yes. Licence: Elastic License 2.0.

**Does it work on Wayland?** Yes. For security reasons Wayland does not let
applications read the screen themselves, so a native helper is required
(`grim`+`slurp`, `gnome-screenshot` or `kde-spectacle`, see below). Under X11
nothing extra is needed.

**Can it capture entire web pages?** Yes — the scrolling screenshot keeps
capturing frames and stitches them into one tall image automatically.

**Is there a Windows or macOS build?** macOS (Apple Silicon) ships as a `.dmg` —
see [Installation](#-macos-apple-silicon-1). There is no package for Windows or
for Intel Macs at the moment.

## Installation

### Which file do I need?

The [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
holds several files. Here is the right one:

| Your system | File | Instructions |
|---|---|---|
| **Mac** with Apple chip (M1–M4) | `SaentisShot_…_aarch64.dmg` | [macOS](#-macos-apple-silicon-1) |
| **Linux Mint**, Ubuntu, Pop!_OS | `SaentisShot_…_amd64.deb` | [Debian family](#-linux-mint-ubuntu-and-pop_os) |
| **CachyOS** | `PKGBUILD` | [CachyOS](#-cachyos-1) |

The release also contains an `AppImage` for other Linux systems. It is **not
tested** and not supported; if you want to try it, make it executable with
`chmod +x` and run it directly.

`SHA256SUMS.txt` is only needed if you want to
[verify](#verifying-the-download-recommended) the download.

> **Mac with an Intel processor?** There is no package for it at the moment –
> the `aarch64` build will not run there.

For every system below, **the simplest route comes first**. If you have never
used a terminal, just follow the first block — that is enough. The short
commands underneath are a shortcut for the practised; they fetch the current
version themselves.

> **Opening a terminal:** on Linux press `Ctrl`+`Alt`+`T`, on macOS press
> `Cmd`+`Space` and type "Terminal". Paste the command, press `Enter`. While
> you type a password nothing moves on screen — that is intended, not a fault.

### 🐧 Linux Mint, Ubuntu and Pop!_OS

**Step by step:**

1. On the [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   click the file ending in `_amd64.deb`. It lands in your **Downloads** folder.
2. Open a terminal and paste this single line:

   ```bash
   sudo apt install -y ~/Downloads/SaentisShot_*_amd64.deb
   ```

On **Linux Mint** a double-click on the downloaded file works just as well —
the package installer opens and does the rest. On Ubuntu and Pop!_OS what the
double-click opens depends on the release; the command above works everywhere.

**Shortcut** — downloads and installs in one go:

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*_amd64\.deb' | head -n1)"
sudo apt install -y ./SaentisShot_*_amd64.deb
```

`apt` pulls in the required libraries. Recommended for text recognition (OCR):

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

> **On a Wayland session** (the default on Ubuntu) also install
> `sudo apt install -y gnome-screenshot` — otherwise GNOME asks for confirmation
> on every capture. The brief flash when capturing comes from GNOME itself and
> cannot be switched off.

*Uninstall:* `sudo apt remove saentisshot`

### 🐧 CachyOS

There is no way around the terminal here: CachyOS assembles the package itself.
Paste the four lines in order — the second one creates a dedicated empty
folder, because building produces files:

```bash
sudo pacman -S --needed base-devel curl          # once, if not present yet
mkdir -p ~/saentisshot-build && cd ~/saentisshot-build
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*/PKGBUILD' | head -n1)"
makepkg -si
```

> **Do not run this as `root`, and not with `sudo makepkg`.** `makepkg` refuses
> to run as root and aborts with an error. Call it as your normal user — it asks
> for the password itself once the package is built.

The PKGBUILD downloads the official package, **verifies its SHA-256 digest** and
installs it as `saentisshot-bin`. Recommended for OCR:

```bash
sudo pacman -S tesseract tesseract-data-deu tesseract-data-eng
```

*Uninstall:* `sudo pacman -R saentisshot-bin`

### 🍎 macOS (Apple Silicon)

**With the mouse:** download the `.dmg` from the
[download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest),
double-click it and drag **SäntisShot** into **Applications**. Then continue at
“On first launch” below.

**Or in a terminal** – downloads, mounts and installs into Applications:

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*_aarch64\.dmg' | head -n1)"
hdiutil attach SaentisShot_*_aarch64.dmg
cp -R /Volumes/SaentisShot/SaentisShot.app /Applications/
hdiutil detach /Volumes/SaentisShot
xattr -dr com.apple.quarantine /Applications/SaentisShot.app   # clear the Gatekeeper flag
open /Applications/SaentisShot.app
```

#### On first launch

macOS refuses to open the app (SäntisShot is not notarised with
Apple). Allow it once – the route depends on your macOS version:

- **macOS 15 (Sequoia) and newer:** double-click the app, dismiss the message
  with **Done**. Then open **System Settings → Privacy & Security**, scroll down
  to “SaentisShot was blocked …” and click **Open Anyway**. Confirm with Touch
  ID or your password. *(The old right-click trick no longer works on these
  versions.)*
- **macOS 14 (Sonoma) and older:** **right-click** the app → **Open** →
  **Open** again.

After that it always starts normally. The terminal command above skips this by
removing the quarantine flag right away.

**Two things on first launch:**

1. macOS asks for the **Screen Recording** permission (System Settings → Privacy
   & Security → Screen Recording). Without it, any app on macOS only captures
   the desktop wallpaper. Restart SäntisShot once after granting it – the
   permission then survives future updates.
2. SäntisShot is a **menu bar app**: it lives in the status bar at the top
   right, not in the Dock.

For text recognition (OCR) two commands are enough – the big language pack
(`tesseract-lang`, over 1 GB) is not needed, SäntisShot only uses German and
English:

```bash
brew install tesseract
curl -fsSL https://github.com/tesseract-ocr/tessdata/raw/main/deu.traineddata \
  -o "$(brew --prefix tesseract)/share/tessdata/deu.traineddata"
```

On first use SäntisShot keeps its own copy of the language data, so a later
Tesseract upgrade cannot silently fall back to English.

*Uninstall:* `rm -rf /Applications/SaentisShot.app`

### Verifying the download (recommended)

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://github.com/dbr24/SaentisShot-Releases/releases/download/[^"]*/SHA256SUMS\.txt' | head -n1)"
sha256sum -c SHA256SUMS.txt --ignore-missing
```

The output must read `OK` for every file present. On macOS the command is
`shasum -a 256 -c SHA256SUMS.txt --ignore-missing`.

## Optional extras

Text recognition (OCR) in the editor:

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng   # Mint, Ubuntu, Pop!_OS
sudo pacman -S tesseract tesseract-data-deu tesseract-data-eng          # CachyOS
```

Only needed for **Wayland** sessions, depending on your desktop:

```bash
sudo apt install -y grim slurp          # Sway, Hyprland
sudo apt install -y gnome-screenshot    # GNOME, Cinnamon
sudo apt install -y kde-spectacle       # KDE Plasma
```

Under X11 (the default on Linux Mint) no extra tools are needed. On GNOME 42 and
newer, `gnome-screenshot` is no longer installed by default; SäntisShot then
falls back to the GNOME Shell’s own interface.

## First steps

**Taking a screenshot:** press the **Print key** (labelled `Print`, `PrtSc` or
`Druck`, depending on your keyboard). A small chooser appears with the four
capture types — screen, window, region, scrolling. Pick one with the mouse or
the keys `1` to `4`; `Enter` repeats the type you used last.

The app runs in the background while you work. You can reach it any time through
its icon in the system tray next to the clock.

**After the capture** the image is already in your clipboard — paste it with
`Ctrl+V`. A small preview also appears in the bottom right corner; clicking it
opens the editor.

**Choosing a different key:** *Settings → Global hotkey* → click the field and
press the key you want. It takes effect immediately, `Esc` cancels. Hold `Ctrl`,
`Alt`, `Shift` or `Super` for a combination.

**The Print key does nothing?** There are two usual reasons:

- **Your desktop claims it.** Cinnamon and GNOME bind their own screenshot tool
  to it out of the box. Either remove that binding in your system’s keyboard
  settings, or choose a different key in SäntisShot.
- **You are in a Wayland session.** There, no application may grab keys
  globally. SäntisShot therefore registers the key in your desktop’s own
  keyboard shortcuts — automatically on Cinnamon and GNOME. You can check under
  *Settings → Capture key under Wayland*.

If your desktop intercepts a key, it never reaches the recorder in the first
place. For that case there is **“Enter it manually”** below the field, where you
type it as text, for example `Ctrl+PrintScreen`.

## When something goes wrong

If something fails, a red message appears in the bottom right corner. It **stays
there** until you close it, so you can read it at your leisure.

The **“Copy report”** button puts that message into your clipboard together with
the technical details: version, operating system, desktop environment, storage
folders and the last lines of the log. That is exactly what is needed to work
out what happened — just paste it into your bug report.

The report is only assembled when you click, and it only ever goes to your
clipboard; SäntisShot never sends anything on its own. It contains file paths
from your home folder, so do have a quick look before passing it on.

**Text recognition reports an error?** Usually Tesseract’s language files are
missing. Check with `tesseract --list-langs` in a terminal; if `deu` and `eng`
are not listed, use the matching command from
[Optional extras](#optional-extras). This is especially common on CachyOS: there the `tesseract` package ships **no**
language file at all.

## Updates

The app checks for new versions itself and installs them on explicit click – on
Linux through the system installer, on macOS by opening the `.dmg` in Finder. The
check is the only network request it makes and can be switched off in the settings.

To leave a version out, press **“Skip this version”** in the update section — it
will no longer announce itself. Checking manually later still shows it.

## Security

Please do **not** report vulnerabilities through public issues, but privately via
the **Security** tab → **Report a vulnerability**.

All image processing, the history and the text recognition run entirely locally
on your device. No usage data is collected or transmitted. Captures are stored
with file mode `0600` — on machines with several user accounts nobody else can
read them.

## Licence

Elastic License 2.0 — see [LICENSE](LICENSE).
