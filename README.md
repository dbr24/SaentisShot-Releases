# SäntisShot — Screenshot-Tool für Linux und macOS 🏔️📸

*Deutsch · [English below](#english)*

**SäntisShot ist ein kostenloses Screenshot-Programm** mit Bereichsauswahl,
**Scrolling-Screenshots** (ganze Webseiten in einem Bild), einem Editor zum
Beschriften, **Texterkennung (OCR)** und einer Historie. Alles läuft lokal auf
deinem Gerät.

Für die aktuellen Fassungen von **Ubuntu** (24.04, 26.04), **Linux Mint** (22),
**Pop!_OS** (24.04, 26.04), **CachyOS** und **macOS** auf einem Mac mit
Apple-Chip. Ältere Fassungen werden nicht unterstützt.

### ⬇️ [Aktuelle Version herunterladen](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

> Dieses Repository enthält nur die fertigen Installationspakete, nicht den
> Quellcode.

## Installation

| Dein System | So geht's |
|---|---|
| **Linux Mint** | [Datei laden, doppelklicken – fertig](#-linux-mint) |
| **Ubuntu**, **Pop!_OS** | [Eine Zeile im Terminal](#-ubuntu-und-pop_os) |
| **CachyOS** | [Vier Zeilen im Terminal](#-cachyos) |
| **Mac** mit Apple-Chip | [Datei laden, App in «Programme» ziehen](#-mac) |

> **Terminal öffnen:** unter Linux `Strg`+`Alt`+`T`, auf dem Mac
> `Cmd`+`Leertaste`, «Terminal» tippen und `Enter`. Befehl einfügen (Rechtsklick
> → Einfügen) und `Enter` drücken. **Beim Passwort erscheinen keine Zeichen** –
> das ist normal, einfach blind tippen.

### 🐧 Linux Mint

1. Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   die Datei anklicken, die auf **`_amd64.deb`** endet.
2. Im Ordner **Downloads** doppelklicken, **«Paket installieren»** wählen und
   das Passwort eingeben.

Oder im Terminal die Zeile unter [Ubuntu](#-ubuntu-und-pop_os) nehmen.

### 🐧 Ubuntu und Pop!_OS

Diese **eine Zeile** im Terminal lädt die aktuelle Version und installiert sie:

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

Fertig – **SäntisShot** steht im Anwendungsmenü.

### 🐧 CachyOS

Die vier Zeilen nacheinander im Terminal einfügen:

```bash
sudo pacman -S --needed base-devel
mkdir -p ~/saentisshot-bau && cd ~/saentisshot-bau
curl -fLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/PKGBUILD
makepkg -si
```

Die letzte Zeile **ohne** `sudo` – `makepkg` fragt am Ende selbst nach dem
Passwort. Das PKGBUILD lädt das offizielle Paket und prüft dessen Prüfsumme.

### 🍎 Mac

1. Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   die Datei laden, die auf **`_aarch64.dmg`** endet, und sie doppelklicken.
2. **SaentisShot** in den Ordner **Programme** ziehen.
3. Beim ersten Öffnen blockiert macOS die App, weil sie nicht bei Apple
   notarisiert ist: Meldung mit **Fertig** schliessen, dann
   **Systemeinstellungen → Datenschutz & Sicherheit** öffnen und ganz unten
   **«Trotzdem öffnen»** klicken.
4. Die Frage nach **Bildschirmaufnahme** erlauben und SäntisShot einmal neu
   starten – sonst nimmt macOS nur den Schreibtischhintergrund auf.

Das Symbol erscheint oben rechts in der Menüleiste, nicht im Dock.

<details>
<summary><b>Oder im Terminal</b> (erspart Schritt 3)</summary>

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

Die Texterkennung braucht das kostenlose Programm Tesseract – einmal den Befehl
für dein System ausführen:

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

**Screenshot machen:** **Druck-Taste** drücken (`Druck`, `Print` oder `PrtSc`).
Auf dem Mac, der keine hat, ist es `Cmd`+`Shift`+`2` (bis Fassung 1.9.2 dort
einmal unter *Einstellungen → Globaler Hotkey* eine Taste festlegen). Unten
rechts erscheint eine Auswahl mit den vier Aufnahmearten – mit der Maus oder den
Tasten `1` bis `4` wählen; `Enter` wiederholt die letzte.

**Danach** liegt das Bild in der Zwischenablage (`Strg`+`V` fügt es überall
ein), und ein Klick auf die Vorschau unten rechts öffnet den Editor.

SäntisShot läuft im Hintergrund weiter – erreichbar über das Symbol neben der
Uhr (Mac: oben rechts). Andere Taste: *Einstellungen → Globaler Hotkey*.

## Wenn etwas nicht klappt

**Eine rote Meldung erscheint:** Der Knopf **«Bericht kopieren»** legt sie samt
technischen Angaben in die Zwischenablage – genau das wird zur Klärung
gebraucht. Von selbst sendet SäntisShot nichts.

**Die Druck-Taste tut nichts:** Meist hält das System sie selbst (unter KDE etwa
Spectacle). Unter *Einstellungen → Aufnahme-Taste unter Wayland* zeigt
SäntisShot, ob die Taste eingetragen ist. Sonst in den Tastatur-Einstellungen
des Systems ein eigenes Kürzel mit dem Befehl `saentisshot --hotkey` anlegen –
oder in SäntisShot eine andere Taste wählen.

**Ubuntu zeigt bei jeder Aufnahme sein eigenes Aufnahme-Fenster:**
`sudo apt install -y gnome-screenshot` und SäntisShot neu starten.

**Das Terminal zeigt «… nicht Sandbox-geschützt durchgeführt …»:** nur ein
Hinweis – die Installation hat geklappt.

**Die Texterkennung meldet einen Fehler:** Meist fehlen die Sprachdateien –
siehe [Texterkennung einrichten](#texterkennung-ocr-einrichten). Unter CachyOS
bringt `tesseract` keine einzige mit.

## Updates

SäntisShot sucht beim Start und danach täglich nach einer neuen Version und
meldet sie in der App. Installiert wird erst auf Knopfdruck, nach Prüfung von
Vollständigkeit und Echtheit (SHA-256). Das ist der einzige Netzwerkzugriff des
Programms; abschaltbar in den Einstellungen.

## Deinstallieren

- **Linux Mint, Ubuntu, Pop!_OS:** `sudo apt remove saentis-shot`
- **CachyOS:** `sudo pacman -R saentisshot-bin`
- **Mac:** SaentisShot aus **Programme** in den Papierkorb ziehen.

Die Aufnahmen bleiben erhalten (Ordner *Bilder/SäntisShot*).

## Häufige Fragen

**Kostet es etwas?** Nein. Lizenz: Elastic License 2.0.

**Werden Daten gesendet?** Nein. Keine Telemetrie, keine Konten, keine Cloud.
Die Aufnahmen kann kein anderes Benutzerkonto auf dem Rechner lesen.

**Andere Systeme?** Andere Linux-Systeme können die `AppImage` aus dem Release
versuchen (ausführbar machen, starten) – ungetestet und ohne Unterstützung.
Für Windows und Macs mit Intel-Prozessor gibt es kein Paket.

## Für Fortgeschrittene: Download prüfen

Im Ordner mit der heruntergeladenen Datei:

```bash
curl -fsSLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Für jede vorhandene Datei muss `OK` erscheinen (Mac:
`shasum -a 256 -c SHA256SUMS.txt --ignore-missing`).

## Sicherheit und Lizenz

Sicherheitslücken bitte **nicht** öffentlich melden, sondern vertraulich über
**Security → Report a vulnerability**. Lizenz: Elastic License 2.0 – siehe
[LICENSE](LICENSE).

---

<a name="english"></a>

# SäntisShot — Screenshot tool for Linux and macOS

**SäntisShot is a free screenshot tool** with region selection, **scrolling
screenshots** (a whole web page in one image), an annotation editor, **text
recognition (OCR)** and a history. Everything runs locally on your device.

For the current releases of **Ubuntu** (24.04, 26.04), **Linux Mint** (22),
**Pop!_OS** (24.04, 26.04), **CachyOS** and **macOS** on a Mac with Apple
silicon. Older releases are not supported.

### ⬇️ [Download the current version](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

> This repository contains the ready-made installation packages only, not the
> source code.

## Installation

| Your system | How |
|---|---|
| **Linux Mint** | [Download, double-click – done](#-linux-mint-1) |
| **Ubuntu**, **Pop!_OS** | [One line in a terminal](#-ubuntu-and-pop_os) |
| **CachyOS** | [Four lines in a terminal](#-cachyos-1) |
| **Mac** with Apple silicon | [Download, drag the app to Applications](#-mac-1) |

> **Opening a terminal:** on Linux `Ctrl`+`Alt`+`T`; on a Mac `Cmd`+`Space`,
> type "Terminal", `Enter`. Paste the command (right-click → Paste) and press
> `Enter`. **Nothing appears while you type a password** – that is normal.

### 🐧 Linux Mint

1. On the [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   click the file ending in **`_amd64.deb`**.
2. Double-click it in **Downloads**, choose **"Install Package"** and enter your
   password.

Or use the terminal line under [Ubuntu](#-ubuntu-and-pop_os).

### 🐧 Ubuntu and Pop!_OS

This **single line** in a terminal fetches the current version and installs it:

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

Done – **SäntisShot** is in the application menu.

### 🐧 CachyOS

Paste the four lines into a terminal, one after the other:

```bash
sudo pacman -S --needed base-devel
mkdir -p ~/saentisshot-bau && cd ~/saentisshot-bau
curl -fLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/PKGBUILD
makepkg -si
```

Run the last line **without** `sudo` – `makepkg` asks for the password itself.
The PKGBUILD downloads the official package and verifies its checksum.

### 🍎 Mac

1. On the [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
   download the file ending in **`_aarch64.dmg`** and double-click it.
2. Drag **SaentisShot** into **Applications**.
3. On first launch macOS blocks the app because it is not notarised by Apple:
   close the message with **Done**, open **System Settings → Privacy &
   Security** and click **"Open Anyway"** at the bottom.
4. Allow **Screen Recording** when asked and restart SäntisShot once –
   otherwise macOS only captures the desktop background.

The icon appears at the top right of the menu bar, not in the Dock.

<details>
<summary><b>Or in a terminal</b> (saves step 3)</summary>

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

Text recognition needs the free program Tesseract – run the command for your
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

**Taking a screenshot:** press the **Print key** (`Print`, `PrtSc` or `Druck`).
On a Mac, which has none, it is `Cmd`+`Shift`+`2` (up to version 1.9.2, set a
key once under *Settings → Global hotkey* there). A chooser with the four
capture types appears at the bottom right – pick one with the mouse or keys `1`
to `4`; `Enter` repeats the last one.

**Afterwards** the image is in your clipboard (`Ctrl`+`V` pastes it anywhere),
and a click on the preview at the bottom right opens the editor.

SäntisShot keeps running in the background – reachable via the icon next to the
clock (Mac: top right). Different key: *Settings → Global hotkey*.

## When something goes wrong

**A red message appears:** the **"Copy report"** button puts it, with the
technical details, into your clipboard – exactly what is needed to work out what
happened. SäntisShot never sends anything on its own.

**The Print key does nothing:** usually the system holds it itself (on KDE e.g.
Spectacle). *Settings → Capture key on Wayland* shows whether SäntisShot's key
is registered. Otherwise add a custom shortcut with the command
`saentisshot --hotkey` in your system's keyboard settings – or pick a different
key in SäntisShot.

**Ubuntu shows its own capture window on every capture:**
`sudo apt install -y gnome-screenshot`, then restart SäntisShot.

**The terminal shows "… performed unsandboxed as root …":** only a notice – the
installation worked.

**Text recognition reports an error:** usually the language files are missing –
see [Setting up text recognition](#setting-up-text-recognition-ocr). On CachyOS
`tesseract` ships none at all.

## Updates

SäntisShot checks for a new version at startup and daily after that and shows it
in the app. It is only installed when you press the button, after checking
completeness and authenticity (SHA-256). This is the program's only network
access; it can be switched off in the settings.

## Uninstalling

- **Linux Mint, Ubuntu, Pop!_OS:** `sudo apt remove saentis-shot`
- **CachyOS:** `sudo pacman -R saentisshot-bin`
- **Mac:** drag SaentisShot from **Applications** to the Bin.

Your captures are kept (folder *Pictures/SäntisShot*).

## FAQ

**Does it cost anything?** No. Licence: Elastic License 2.0.

**Is any data sent?** No. No telemetry, no accounts, no cloud. No other user
account on the computer can read your captures.

**Other systems?** Other Linux systems can try the `AppImage` from the release
(make it executable, start it) – untested and unsupported. There is no package
for Windows or Intel Macs.

## For advanced users: verifying the download

In the folder with the downloaded file:

```bash
curl -fsSLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Every file present must show `OK` (Mac:
`shasum -a 256 -c SHA256SUMS.txt --ignore-missing`).

## Security and licence

Please do **not** report security issues publicly – use **Security → Report a
vulnerability**. Licence: Elastic License 2.0 – see [LICENSE](LICENSE).
