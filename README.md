# SäntisShot — Screenshot-Tool für Linux und macOS 🏔️📸

*Deutsch · [English below](#english)*

**SäntisShot ist ein kostenloses Screenshot-Programm** mit Bereichsauswahl,
**Scrolling-Screenshots** (ganze Webseiten in einem Bild), einem Editor zum
Beschriften, **Texterkennung (OCR)** und einer Historie. Alles läuft lokal auf
deinem Gerät.

Es gibt SäntisShot für **Linux Mint**, **Ubuntu**, **Pop!_OS**, **CachyOS** und
**Macs mit Apple-Chip**.

### ⬇️ [Aktuelle Version herunterladen](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

> Dieses Repository enthält nur die fertigen Installationspakete, nicht den
> Quellcode.

## Installation

| Dein System | So geht's |
|---|---|
| **Linux Mint** | [Datei laden, doppelklicken – fertig](#-linux-mint) |
| **Ubuntu**, **Pop!_OS** | [Eine Zeile im Terminal](#-ubuntu-und-pop_os) |
| **CachyOS** | [Vier Zeilen im Terminal](#-cachyos) |
| **Mac** mit Apple-Chip (M1 oder neuer) | [Datei laden, App in «Programme» ziehen](#-mac) |

Für Windows und für Macs mit Intel-Prozessor gibt es zurzeit kein Paket.

> **Terminal öffnen:** unter Linux mit `Strg`+`Alt`+`T`, auf dem Mac mit
> `Cmd`+`Leertaste`, dann «Terminal» tippen und `Enter`. Befehl hineinkopieren
> (Rechtsklick → Einfügen) und mit `Enter` bestätigen. **Beim Passwort erscheinen
> keine Zeichen** – das ist normal. Einfach blind tippen und `Enter` drücken.

### 🐧 Linux Mint

1. Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   die Datei anklicken, die auf **`_amd64.deb`** endet.
2. Den Ordner **Downloads** öffnen und die Datei **doppelklicken**.
3. Auf **«Paket installieren»** klicken und dein Passwort eingeben.

Fertig – **SäntisShot** steht jetzt im Startmenü.

**Oder im Terminal** – diese eine Zeile lädt die aktuelle Version selbst und
installiert sie:

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

### 🐧 Ubuntu und Pop!_OS

Terminal öffnen und diese **eine Zeile** einfügen – sie lädt die aktuelle
Version selbst und installiert sie:

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

Fertig – **SäntisShot** steht jetzt im Anwendungsmenü. (Ein Doppelklick auf
die heruntergeladene Datei öffnet je nach Ubuntu-Fassung ein anderes Programm;
die Zeile oben funktioniert überall gleich.)

> **Ubuntu mit Wayland** (die Vorgabe) – zusätzlich einmal:
>
> ```bash
> sudo apt install -y gnome-screenshot
> ```
>
> Ohne das fragt Ubuntu bei jeder Aufnahme nach. Den kurzen Blitz beim
> Auslösen macht Ubuntu selbst. Die Scrolling-Aufnahme ist unter Ubuntu mit
> Wayland nicht möglich; Bildschirm, Fenster und Bereich funktionieren.

### 🐧 CachyOS

Hier geht es nur über das Terminal, weil CachyOS das Paket selbst
zusammenbaut. Die vier Zeilen nacheinander einfügen:

```bash
sudo pacman -S --needed base-devel
mkdir -p ~/saentisshot-bau && cd ~/saentisshot-bau
curl -fLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/PKGBUILD
makepkg -si
```

Die letzte Zeile **nicht** mit `sudo` davor ausführen – `makepkg` fragt am
Ende von selbst nach dem Passwort. Das PKGBUILD lädt das offizielle Paket und
prüft dessen SHA-256-Prüfsumme.

### 🍎 Mac

1. Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   die Datei anklicken, die auf **`_aarch64.dmg`** endet, und sie doppelklicken.
2. **SaentisShot** in den Ordner **Programme** ziehen.
3. **Beim ersten Öffnen** meldet macOS, die App könne nicht überprüft werden
   (sie ist nicht bei Apple notarisiert). Einmalig freigeben:
   - **macOS 15 (Sequoia) und neuer:** Die Meldung mit **Fertig** schliessen,
     dann **Systemeinstellungen → Datenschutz & Sicherheit** öffnen, ganz nach
     unten scrollen und bei «SaentisShot wurde blockiert» auf **Trotzdem
     öffnen** klicken.
   - **macOS 14 und älter:** **Rechtsklick** auf die App → **Öffnen** → nochmals
     **Öffnen**.
4. Die Frage nach **Bildschirmaufnahme** erlauben und SäntisShot danach einmal
   neu starten. Ohne diese Berechtigung nimmt macOS nur den
   Schreibtischhintergrund auf.

SäntisShot ist eine **Menüleisten-App**: Das Symbol erscheint oben rechts in der
Menüleiste, nicht im Dock.

<details>
<summary><b>Oder im Terminal</b> (erspart auch Schritt 3)</summary>

```bash
curl -fLo /tmp/SaentisShot.dmg "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_aarch64\.dmg' | head -n1)"
hdiutil attach /tmp/SaentisShot.dmg
cp -R /Volumes/SaentisShot/SaentisShot.app /Applications/
hdiutil detach /Volumes/SaentisShot
xattr -dr com.apple.quarantine /Applications/SaentisShot.app
open /Applications/SaentisShot.app
```

</details>

## Texterkennung (OCR) einrichten

Für die Texterkennung braucht SäntisShot das kostenlose Programm Tesseract.
Einmal den Befehl für dein System ausführen:

**Linux Mint, Ubuntu, Pop!_OS:**

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

**CachyOS:**

```bash
sudo pacman -S --needed tesseract tesseract-data-deu tesseract-data-eng
```

**Mac** (setzt [Homebrew](https://brew.sh) voraus):

```bash
brew install tesseract
curl -fsSL https://github.com/tesseract-ocr/tessdata/raw/main/deu.traineddata -o "$(brew --prefix tesseract)/share/tessdata/deu.traineddata"
```

## Erste Schritte

**Screenshot machen:** Drück die **Druck-Taste** (je nach Tastatur `Druck`,
`Print` oder `PrtSc`). Unten rechts erscheint eine kleine Auswahl mit den vier
Aufnahmearten – Bildschirm, Fenster, Bereich, Scrollend. Wähle mit der Maus oder
den Tasten `1` bis `4`; `Enter` wiederholt die zuletzt benutzte Art.

**Nach der Aufnahme** liegt das Bild sofort in der Zwischenablage – mit
`Strg`+`V` fügst du es überall ein. Unten rechts erscheint eine Vorschau; ein
Klick darauf öffnet den Editor.

SäntisShot läuft im Hintergrund weiter. Erreichbar ist es jederzeit über das
Symbol neben der Uhr (Mac: oben rechts in der Menüleiste).

**Andere Taste gewünscht?** *Einstellungen → Globaler Hotkey* → ins Feld klicken
und die gewünschte Taste drücken.

## Wenn etwas nicht klappt

**Eine rote Meldung erscheint:** Sie bleibt stehen, bis du sie schliesst. Der
Knopf **«Bericht kopieren»** legt die Meldung samt den technischen Angaben in
die Zwischenablage – genau das wird zur Klärung gebraucht. Von selbst sendet
SäntisShot nichts. Der Bericht enthält Ordnerpfade aus deinem Benutzerordner;
wirf vor dem Weitergeben kurz einen Blick darauf.

**Die Druck-Taste tut nichts:** Meist belegt der Desktop sie selbst mit seinem
eigenen Screenshot-Werkzeug. Entweder diese Belegung in den
Tastatur-Einstellungen des Systems entfernen oder in SäntisShot eine andere
Taste festlegen. Kommt die Taste gar nicht an, gibt es unter dem Feld den Weg
**«Kommt beim Drücken nichts an? Von Hand eintragen»**, etwa
`Ctrl+PrintScreen`.

**Das Terminal meldet «Nicht unterstützte Datei … auf Befehlszeile
angegeben»:** Die Datei liegt nicht dort, wo der Befehl sie sucht (Download noch
nicht fertig oder in einem anderen Ordner gespeichert). Nimm die Zeile aus der
Anleitung oben – sie lädt die Datei selbst.

**Das Terminal zeigt «Der Download wird als root und nicht Sandbox-geschützt
durchgeführt …»:** Das ist nur ein Hinweis, kein Fehler. Die Installation hat
trotzdem geklappt.

**Die Texterkennung meldet einen Fehler:** Dann fehlen meist die Sprachdateien.
Den passenden Befehl unter [Texterkennung (OCR)
einrichten](#texterkennung-ocr-einrichten) ausführen. Unter CachyOS ist das
besonders häufig: Das Paket `tesseract` bringt dort keine einzige Sprachdatei
mit.

## Updates

SäntisShot prüft beim Start und danach täglich, ob es eine neue Version gibt,
und meldet sie in der App. Installiert wird nur, wenn du auf den Knopf drückst;
der Download wird vorher auf Vollständigkeit und Echtheit (SHA-256) geprüft.
Die Prüfung ist der einzige Netzwerkzugriff des Programms und lässt sich in den
Einstellungen abschalten. Eine Version auslassen: **«Diese Version
überspringen»**.

## Deinstallieren

- **Linux Mint, Ubuntu, Pop!_OS:** `sudo apt remove saentis-shot`
- **CachyOS:** `sudo pacman -R saentisshot-bin`
- **Mac:** SaentisShot aus dem Ordner **Programme** in den Papierkorb ziehen.

Deine Aufnahmen bleiben dabei erhalten (Ordner *Bilder/SäntisShot*).

## Häufige Fragen

**Ist SäntisShot kostenlos?** Ja. Lizenz: Elastic License 2.0.

**Funktioniert es unter Wayland?** Ja, ohne Zusatzpakete. Nur unter Ubuntu
empfiehlt sich `gnome-screenshot` (siehe [Ubuntu](#-ubuntu-und-pop_os)).

**Werden Daten gesendet?** Nein. Bildbearbeitung, Historie und Texterkennung
laufen vollständig auf dem Gerät. Keine Telemetrie, keine Konten, keine Cloud.
Aufnahmen werden so gespeichert, dass andere Benutzerkonten auf demselben
Rechner sie nicht lesen können.

**Gibt es SäntisShot für andere Systeme?** Nein. Andere Linux-Systeme können
die `AppImage` aus dem Release versuchen (ausführbar machen, dann starten) – sie
ist aber nicht getestet und wird nicht unterstützt.

## Für Fortgeschrittene: Download prüfen

Im Ordner mit der heruntergeladenen Datei:

```bash
curl -fsSLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Für jede vorhandene Datei muss `OK` erscheinen. Auf dem Mac lautet der zweite
Befehl `shasum -a 256 -c SHA256SUMS.txt --ignore-missing`.

## Sicherheit

Sicherheitslücken bitte **nicht** über öffentliche Issues melden, sondern
vertraulich über den Reiter **Security → Report a vulnerability**.

## Lizenz

Elastic License 2.0 – siehe [LICENSE](LICENSE).

---

<a name="english"></a>

# SäntisShot — Screenshot tool for Linux and macOS

**SäntisShot is a free screenshot tool** with region selection, **scrolling
screenshots** (a whole web page in one image), an annotation editor, **text
recognition (OCR)** and a history. Everything runs locally on your device.

SäntisShot is available for **Linux Mint**, **Ubuntu**, **Pop!_OS**,
**CachyOS** and **Macs with Apple silicon**.

### ⬇️ [Download the current version](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

> This repository contains the ready-made installation packages only, not the
> source code.

## Installation

| Your system | How |
|---|---|
| **Linux Mint** | [Download, double-click – done](#-linux-mint-1) |
| **Ubuntu**, **Pop!_OS** | [One line in a terminal](#-ubuntu-and-pop_os) |
| **CachyOS** | [Four lines in a terminal](#-cachyos-1) |
| **Mac** with Apple silicon (M1 or newer) | [Download, drag the app into Applications](#-mac-1) |

There is currently no package for Windows or for Intel Macs.

> **Opening a terminal:** on Linux press `Ctrl`+`Alt`+`T`; on a Mac press
> `Cmd`+`Space`, type "Terminal" and press `Enter`. Paste the command
> (right-click → Paste) and press `Enter`. **Nothing appears while you type a
> password** – that is normal. Just type it blind and press `Enter`.

### 🐧 Linux Mint

1. On the [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   click the file ending in **`_amd64.deb`**.
2. Open your **Downloads** folder and **double-click** the file.
3. Click **"Install Package"** and enter your password.

Done – **SäntisShot** is now in the start menu.

**Or in a terminal** – this single line fetches the current version and
installs it:

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

### 🐧 Ubuntu and Pop!_OS

Open a terminal and paste this **single line** – it fetches the current version
and installs it:

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

Done – **SäntisShot** is now in the application menu. (What a double-click on
the downloaded file opens depends on the Ubuntu release; the line above works
the same everywhere.)

> **Ubuntu with Wayland** (the default) – additionally, once:
>
> ```bash
> sudo apt install -y gnome-screenshot
> ```
>
> Without it Ubuntu asks for confirmation on every capture. The brief flash when
> capturing comes from Ubuntu itself. Scrolling capture is not possible on
> Ubuntu with Wayland; screen, window and region work.

### 🐧 CachyOS

There is no way around the terminal here, because CachyOS builds the package
itself. Paste the four lines one after another:

```bash
sudo pacman -S --needed base-devel
mkdir -p ~/saentisshot-build && cd ~/saentisshot-build
curl -fLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/PKGBUILD
makepkg -si
```

Do **not** put `sudo` in front of the last line – `makepkg` asks for the
password itself at the end. The PKGBUILD downloads the official package and
verifies its SHA-256 checksum.

### 🍎 Mac

1. On the [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   click the file ending in **`_aarch64.dmg`** and double-click it.
2. Drag **SaentisShot** into the **Applications** folder.
3. **On first launch** macOS says the app cannot be verified (it is not
   notarised with Apple). Allow it once:
   - **macOS 15 (Sequoia) and newer:** close the message with **Done**, then
     open **System Settings → Privacy & Security**, scroll all the way down and
     click **Open Anyway** next to "SaentisShot was blocked".
   - **macOS 14 and older:** **right-click** the app → **Open** → **Open**
     again.
4. Allow **Screen Recording** when asked, then restart SäntisShot once. Without
   this permission macOS only captures the desktop wallpaper.

SäntisShot is a **menu bar app**: its icon appears at the top right of the menu
bar, not in the Dock.

<details>
<summary><b>Or in a terminal</b> (also skips step 3)</summary>

```bash
curl -fLo /tmp/SaentisShot.dmg "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_aarch64\.dmg' | head -n1)"
hdiutil attach /tmp/SaentisShot.dmg
cp -R /Volumes/SaentisShot/SaentisShot.app /Applications/
hdiutil detach /Volumes/SaentisShot
xattr -dr com.apple.quarantine /Applications/SaentisShot.app
open /Applications/SaentisShot.app
```

</details>

## Setting up text recognition (OCR)

Text recognition needs the free program Tesseract. Run the command for your
system once:

**Linux Mint, Ubuntu, Pop!_OS:**

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

**CachyOS:**

```bash
sudo pacman -S --needed tesseract tesseract-data-deu tesseract-data-eng
```

**Mac** (requires [Homebrew](https://brew.sh)):

```bash
brew install tesseract
curl -fsSL https://github.com/tesseract-ocr/tessdata/raw/main/deu.traineddata -o "$(brew --prefix tesseract)/share/tessdata/deu.traineddata"
```

## First steps

**Taking a screenshot:** press the **Print key** (labelled `Print`, `PrtSc` or
`Druck`, depending on your keyboard). A small chooser with the four capture
types appears at the bottom right – screen, window, region, scrolling. Pick one
with the mouse or the keys `1` to `4`; `Enter` repeats the type you used last.

**After the capture** the image is already in your clipboard – paste it
anywhere with `Ctrl`+`V`. A preview appears at the bottom right; clicking it
opens the editor.

SäntisShot keeps running in the background. You can reach it any time through
its icon next to the clock (Mac: top right in the menu bar).

**Want a different key?** *Settings → Global hotkey* → click the field and
press the key you want.

## When something goes wrong

**A red message appears:** it stays until you close it. The **"Copy report"**
button puts the message together with the technical details into your
clipboard – exactly what is needed to work out what happened. SäntisShot never
sends anything on its own. The report contains folder paths from your home
folder, so have a quick look before passing it on.

**The Print key does nothing:** usually your desktop claims it for its own
screenshot tool. Either remove that binding in your system's keyboard settings
or choose a different key in SäntisShot. If the key never arrives at all, use
**"Nothing registered when pressing? Enter it manually"** below the field, for
example `Ctrl+PrintScreen`.

**The terminal says "Unsupported file … given on commandline":** the file is
not where the command looks for it (the download has not finished, or it was
saved to a different folder). Use the line from the instructions above – it
downloads the file itself.

**The terminal shows "Download is performed unsandboxed as root …":** that is
only a notice, not an error. The installation worked anyway.

**Text recognition reports an error:** usually the language files are missing.
Run the matching command under [Setting up text recognition
(OCR)](#setting-up-text-recognition-ocr). This is especially common on CachyOS:
there the `tesseract` package ships no language file at all.

## Updates

SäntisShot checks for a new version at start-up and daily after that, and
announces it in the app. It only installs when you press the button; the
download is checked for completeness and authenticity (SHA-256) first. The
check is the program's only network access and can be switched off in the
settings. To leave a version out: **"Skip this version"**.

## Uninstalling

- **Linux Mint, Ubuntu, Pop!_OS:** `sudo apt remove saentis-shot`
- **CachyOS:** `sudo pacman -R saentisshot-bin`
- **Mac:** drag SaentisShot from **Applications** to the Trash.

Your captures are kept (folder *Pictures/SäntisShot*).

## Frequently asked questions

**Is SäntisShot free?** Yes. Licence: Elastic License 2.0.

**Does it work on Wayland?** Yes, without extra packages. Only on Ubuntu is
`gnome-screenshot` recommended (see [Ubuntu](#-ubuntu-and-pop_os)).

**Is any data sent?** No. Image editing, history and text recognition run
entirely on your device. No telemetry, no accounts, no cloud. Captures are
stored so that other user accounts on the same computer cannot read them.

**Is SäntisShot available for other systems?** No. Other Linux systems can try
the `AppImage` from the release (make it executable, then run it) – but it is
not tested and not supported.

## For advanced users: verifying the download

In the folder containing the downloaded file:

```bash
curl -fsSLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Every file present must report `OK`. On a Mac the second command is
`shasum -a 256 -c SHA256SUMS.txt --ignore-missing`.

## Security

Please do **not** report vulnerabilities through public issues, but privately
via the **Security** tab → **Report a vulnerability**.

## Licence

Elastic License 2.0 — see [LICENSE](LICENSE).
