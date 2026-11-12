# SäntisShot — Screenshot-Tool für Linux und macOS 🏔️📸

*Deutsch · [English below](#english)*

**Kostenloses Screenshot-Programm** mit Bereichsauswahl, **Scrolling-Screenshots**
(ganze Webseiten in einem Bild), Editor, **Texterkennung (OCR)** und Historie.
Alles bleibt auf deinem Gerät.

### ⬇️ [Aktuelle Version herunterladen](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

## Installation

Für die aktuellen Fassungen dieser Systeme, getestet mit ihrer Standard-Oberfläche:

| System | Oberfläche | So geht's |
|---|---|---|
| **Linux Mint** | Cinnamon | [Datei laden, doppelklicken](#-linux-mint) |
| **Ubuntu** | GNOME | [Eine Zeile im Terminal](#-ubuntu-und-pop_os) |
| **Pop!_OS** | COSMIC | [Eine Zeile im Terminal](#-ubuntu-und-pop_os) |
| **CachyOS** | KDE Plasma | [Vier Zeilen im Terminal](#-cachyos) |
| **Mac** mit Apple-Chip | macOS | [Datei laden, in «Programme» ziehen](#-mac) |

Andere Oberflächen (etwa Mint mit Xfce) laufen meist auch – die Druck-Taste
richtet man dort eventuell selbst ein (siehe [Hilfe](#wenn-etwas-nicht-klappt)).

> **Terminal öffnen:** Linux `Strg`+`Alt`+`T`, Mac `Cmd`+`Leertaste` → «Terminal».
> Befehl einfügen, `Enter`. Beim Passwort erscheinen keine Zeichen – das ist normal.

### 🐧 Linux Mint

Auf der [Download-Seite](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
die Datei mit **`_amd64.deb`** laden, im Ordner **Downloads** doppelklicken,
**«Paket installieren»**.

### 🐧 Ubuntu und Pop!_OS

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

### 🐧 CachyOS

```bash
sudo pacman -Syu --needed base-devel
mkdir -p ~/saentisshot-bau && cd ~/saentisshot-bau
curl -fLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/PKGBUILD
makepkg -si
```

Die letzte Zeile **ohne** `sudo` – `makepkg` fragt selbst nach dem Passwort.

### 🍎 Mac

1. Die Datei mit **`_aarch64.dmg`** laden, doppelklicken, **SaentisShot** in
   **Programme** ziehen.
2. Beim ersten Öffnen blockiert macOS die App (nicht bei Apple notarisiert):
   Meldung schliessen, **Systemeinstellungen → Datenschutz & Sicherheit →
   «Trotzdem öffnen»**.
3. **Bildschirmaufnahme** erlauben und SäntisShot einmal neu starten.

<details>
<summary>Oder im Terminal (erspart Schritt 2)</summary>

```bash
curl -fLo /tmp/SaentisShot.dmg "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_aarch64\.dmg' | head -n1)"
hdiutil attach /tmp/SaentisShot.dmg
cp -R /Volumes/SaentisShot/SaentisShot.app /Applications/
hdiutil detach /Volumes/SaentisShot
xattr -dr com.apple.quarantine /Applications/SaentisShot.app
open /Applications/SaentisShot.app
```

</details>

## Erste Schritte

- **Druck-Taste** drücken (Mac: `Cmd`+`Shift`+`2`). Unten rechts erscheint die
  Auswahl der vier Aufnahmearten – Maus oder Tasten `1`–`4`.
- **Beim ersten Öffnen** fragt das System einmal, ob SäntisShot Bildschirmfotos
  machen darf (nicht unter Mint): **«Allow»**, **«Erlauben»** bzw. **«OK»**.
  Dort steht «jederzeit» – SäntisShot nimmt aber nur auf, wenn du es auslöst.
- Das Bild liegt danach in der Zwischenablage; ein Klick auf die Vorschau öffnet
  den Editor. SäntisShot läuft im Hintergrund weiter (Symbol neben der Uhr).

## Texterkennung (OCR) einrichten

Unter Ubuntu und Pop!_OS kommt das nötige Programm (Tesseract) gleich mit.
Sonst einmal im Terminal:

**Linux Mint:**

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

**CachyOS:**

```bash
sudo pacman -S --needed tesseract tesseract-data-deu tesseract-data-eng
```

**Mac** (mit [Homebrew](https://brew.sh)), beide Zeilen – die zweite holt Deutsch:

```bash
brew install tesseract
curl -fsSL https://github.com/tesseract-ocr/tessdata/raw/main/deu.traineddata -o "$(brew --prefix tesseract)/share/tessdata/deu.traineddata"
```

## Wenn etwas nicht klappt

- **Mint meldet beim Installieren «Programmfehler in aptkit»:** Das Passwort
  kam zu spät (Mint wartet nur rund 25 Sekunden). Fenster schliessen, die Datei
  noch einmal doppelklicken und das Passwort zügig eingeben.
- **Rote Meldung:** «Bericht kopieren» legt sie samt Details in die
  Zwischenablage – genau das hilft bei der Klärung. SäntisShot sendet nichts.
- **Druck-Taste tut nichts:** *Einstellungen → Aufnahme* zeigt unter
  «Aufnahme-Taste», ob sie eingetragen ist. Sonst im System ein Kürzel mit dem Befehl
  `saentisshot --hotkey` anlegen oder in SäntisShot eine andere Taste wählen.
- **Ubuntu fragt bei jeder Aufnahme mit eigenem Fenster:** Die Erlaubnis wurde
  abgelehnt. In SäntisShot unter *Einstellungen → Aufnahme* auf **«Erneut
  fragen»** klicken, dann «Weiter» und «Allow».
- **Texterkennung meldet einen Fehler:** Die Meldung nennt den passenden Befehl.
- **Pop!_OS: «Bereich» nimmt den ganzen Bildschirm:** In COSMICs Leiste beim
  ersten Mal links die Auswahl anklicken – COSMIC merkt sich das.
- **«… nicht Sandbox-geschützt durchgeführt …»** beim Installieren: nur ein
  Hinweis, die Installation hat geklappt.

## Updates und Deinstallieren

SäntisShot meldet neue Versionen in der App und installiert sie erst auf
Knopfdruck, nach Prüfung der Echtheit (SHA-256). Das ist sein einziger
Netzwerkzugriff; abschaltbar in den Einstellungen.

Entfernen: `sudo apt remove saentis-shot` (Mint, Ubuntu, Pop!_OS),
`sudo pacman -R saentisshot-bin` (CachyOS), Mac: App in den Papierkorb. Die
Aufnahmen bleiben (*Bilder/SäntisShot*); die Druck-Taste gehört danach wieder
dem System (unter Mint ab dem nächsten Anmelden).

Im Benutzerordner bleiben ausserdem Einstellungen, Protokoll und Vorschaubilder
liegen (zusammen wenige MB). Wer auch sie nicht mehr will:

```bash
rm -rf ~/.config/saentisshot ~/.local/share/saentisshot ~/.cache/saentisshot ~/.config/autostart/SaentisShot.desktop
```

<details>
<summary>Download prüfen (für Fortgeschrittene)</summary>

Im Ordner mit der heruntergeladenen Datei – für jede Datei muss `OK` erscheinen:

```bash
wget -qO SHA256SUMS.txt https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Auf dem Mac: `curl -fsSLO` statt `wget -qO SHA256SUMS.txt` und `shasum -a 256` statt
`sha256sum`.

</details>

**Kostenlos**, keine Telemetrie, keine Konten, keine Cloud. Sicherheitslücken
bitte vertraulich melden: **Security → Report a vulnerability**. Lizenz: Elastic
License 2.0 – siehe [LICENSE](LICENSE). Dieses Repository enthält nur die
fertigen Pakete, nicht den Quellcode.

---

<a name="english"></a>

# SäntisShot — Screenshot tool for Linux and macOS

**Free screenshot tool** with region selection, **scrolling screenshots** (a
whole web page in one image), an editor, **text recognition (OCR)** and a
history. Everything stays on your device.

### ⬇️ [Download the current version](https://github.com/dbr24/SaentisShot-Releases/releases/latest)

## Installation

For the current releases of these systems, tested with their default desktop:

| System | Desktop | How |
|---|---|---|
| **Linux Mint** | Cinnamon | [Download, double-click](#-linux-mint-1) |
| **Ubuntu** | GNOME | [One line in a terminal](#-ubuntu-and-pop_os) |
| **Pop!_OS** | COSMIC | [One line in a terminal](#-ubuntu-and-pop_os) |
| **CachyOS** | KDE Plasma | [Four lines in a terminal](#-cachyos-1) |
| **Mac** with Apple silicon | macOS | [Download, drag to Applications](#-mac-1) |

Other desktops (e.g. Mint with Xfce) usually work too – you may have to set up
the Print key yourself there (see [help](#when-something-goes-wrong)).

> **Opening a terminal:** Linux `Ctrl`+`Alt`+`T`, Mac `Cmd`+`Space` →
> "Terminal". Paste the command, `Enter`. Nothing appears while you type a
> password – that is normal.

### 🐧 Linux Mint

On the [download page](https://github.com/dbr24/SaentisShot-Releases/releases/latest)
download the file ending in **`_amd64.deb`**, double-click it in **Downloads**,
**"Install Package"**.

### 🐧 Ubuntu and Pop!_OS

```bash
wget -qO /tmp/saentisshot.deb "$(wget -qO- https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_amd64\.deb' | head -n1)" && sudo apt install -y /tmp/saentisshot.deb
```

### 🐧 CachyOS

```bash
sudo pacman -Syu --needed base-devel
mkdir -p ~/saentisshot-bau && cd ~/saentisshot-bau
curl -fLO https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/PKGBUILD
makepkg -si
```

Run the last line **without** `sudo` – `makepkg` asks for the password itself.

### 🍎 Mac

1. Download the file ending in **`_aarch64.dmg`**, double-click it, drag
   **SaentisShot** into **Applications**.
2. On first launch macOS blocks the app (not notarised by Apple): close the
   message, then **System Settings → Privacy & Security → "Open Anyway"**.
3. Allow **Screen Recording** and restart SäntisShot once.

<details>
<summary>Or in a terminal (saves step 2)</summary>

```bash
curl -fLo /tmp/SaentisShot.dmg "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest | grep -o 'https://[^"]*_aarch64\.dmg' | head -n1)"
hdiutil attach /tmp/SaentisShot.dmg
cp -R /Volumes/SaentisShot/SaentisShot.app /Applications/
hdiutil detach /Volumes/SaentisShot
xattr -dr com.apple.quarantine /Applications/SaentisShot.app
open /Applications/SaentisShot.app
```

</details>

## First steps

- Press the **Print key** (Mac: `Cmd`+`Shift`+`2`). A chooser with the four
  capture types appears at the bottom right – mouse or keys `1`–`4`.
- **The first time you open it**, the system asks once whether SäntisShot may
  take screenshots (not on Mint): click **"Allow"** or **"OK"**. It says "at any
  time" – but SäntisShot only captures when you trigger it.
- The image is then in your clipboard; a click on the preview opens the editor.
  SäntisShot keeps running in the background (icon next to the clock).

## Setting up text recognition (OCR)

On Ubuntu and Pop!_OS the program it needs (Tesseract) comes along.
Otherwise, once in a terminal:

**Linux Mint:**

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

**CachyOS:**

```bash
sudo pacman -S --needed tesseract tesseract-data-deu tesseract-data-eng
```

**Mac** (with [Homebrew](https://brew.sh)), both lines – the second adds German:

```bash
brew install tesseract
curl -fsSL https://github.com/tesseract-ocr/tessdata/raw/main/deu.traineddata -o "$(brew --prefix tesseract)/share/tessdata/deu.traineddata"
```

## When something goes wrong

- **Mint reports "a bug in aptkit" while installing:** the password came too
  late (Mint waits only about 25 seconds). Close the window, double-click the
  file again and enter the password promptly.
- **A red message:** "Copy report" puts it, with details, into your clipboard –
  exactly what helps to sort it out. SäntisShot never sends anything.
- **The Print key does nothing:** *Settings → Capture* shows under “Capture
  key” whether it is registered. Otherwise add a shortcut with the command `saentisshot --hotkey`
  in your system settings, or pick another key in SäntisShot.
- **Ubuntu shows its own capture window every time:** the permission was
  denied. In SäntisShot, click **"Ask again"** under *Settings → Capture*, then
  "Continue" and "Allow".
- **Text recognition reports an error:** the message names the command to run.
- **Pop!_OS: "Region" captures the whole screen:** in COSMIC's bar, click the
  selection on the left the first time – COSMIC remembers it.
- **"… performed unsandboxed …"** while installing: only a notice, the
  installation worked.

## Updates and uninstalling

SäntisShot shows new versions in the app and installs them only when you press
the button, after checking their authenticity (SHA-256). This is its only
network access; it can be switched off in the settings.

Remove: `sudo apt remove saentis-shot` (Mint, Ubuntu, Pop!_OS),
`sudo pacman -R saentisshot-bin` (CachyOS), Mac: drag the app to the Bin. Your
captures are kept (*Pictures/SäntisShot*); the Print key goes back to the
system (on Mint from the next login).

Settings, the log and the thumbnails also stay in your home folder (a few MB in
total). To remove them as well:

```bash
rm -rf ~/.config/saentisshot ~/.local/share/saentisshot ~/.cache/saentisshot ~/.config/autostart/SaentisShot.desktop
```

<details>
<summary>Verifying the download (advanced)</summary>

In the folder with the downloaded file – every file must show `OK`:

```bash
wget -qO SHA256SUMS.txt https://github.com/dbr24/SaentisShot-Releases/releases/latest/download/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt --ignore-missing
```

On a Mac: `curl -fsSLO` instead of `wget -qO SHA256SUMS.txt`, and `shasum -a 256`
instead of `sha256sum`.

</details>

**Free**, no telemetry, no accounts, no cloud. Please report security issues
privately: **Security → Report a vulnerability**. Licence: Elastic License 2.0 –
see [LICENSE](LICENSE). This repository holds the ready-made packages only, not
the source code.
