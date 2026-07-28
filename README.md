# SäntisShot — Screenshot-Tool für Linux 🏔️📸

*Deutsch · [English below](#english)*

**SäntisShot ist ein kostenloses Screenshot-Programm für Linux** (X11 und
Wayland) mit Bereichsauswahl, **Scrolling-Screenshots** (ganze Webseiten in
einem Bild), einem Annotations-Editor, **Texterkennung (OCR)** und einer
Historie. Es läuft auf **Ubuntu, Linux Mint, Debian, Arch, Fedora und
openSUSE** — als `.deb`, `AppImage` oder über ein `PKGBUILD`.

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

**Gibt es eine Version für Windows oder macOS?** Zurzeit nur Linux; macOS ist
vorbereitet, aber es gibt noch kein fertiges Paket.

## Installation

Alle Befehle laden die **aktuelle Version automatisch** herunter – du musst
vorher nichts von Hand holen.

### Linux Mint / Ubuntu / Debian

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*amd64\.deb')"
sudo apt install -y ./SaentisShot_*_amd64.deb
```

Aktualisieren geht später genauso – oder bequemer direkt in der App unter
*Einstellungen → Jetzt nach Updates suchen*.

### Arch / CachyOS / Manjaro / EndeavourOS

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*/PKGBUILD')"
makepkg -si
```

Das PKGBUILD lädt das offizielle Paket, prüft dessen SHA-256-Prüfsumme und
installiert es als `saentisshot-bin`. Deinstallieren mit
`sudo pacman -R saentisshot-bin`.

### Fedora, openSUSE und alle übrigen (AppImage, ohne Installation)

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*\.AppImage')"
chmod +x SaentisShot_*.AppImage
./SaentisShot_*.AppImage
```

### Download prüfen (empfohlen)

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*SHA256SUMS.txt')"
sha256sum -c SHA256SUMS.txt --ignore-missing
```

Die Ausgabe muss für jede vorhandene Datei `OK` melden.

## Optionale Zusatzpakete

Texterkennung (OCR) im Editor:

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng   # Mint/Ubuntu
sudo pacman -S tesseract tesseract-data-deu tesseract-data-eng          # Arch
```

Nur bei **Wayland**-Sitzungen nötig, je nach Desktop:

```bash
sudo apt install -y grim slurp          # Sway, Hyprland
sudo apt install -y gnome-screenshot    # GNOME, Cinnamon
sudo apt install -y kde-spectacle       # KDE Plasma
```

Unter X11 (Standard bei Linux Mint) sind keine Zusatztools nötig.

## Updates

SäntisShot prüft beim Start und danach täglich, ob hier eine neuere Version
liegt, und meldet sie in der App – das ist der einzige Netzwerkaufruf des
Programms und lässt sich in den Einstellungen abschalten. Installiert wird nur
auf ausdrücklichen Klick; der Download wird gegen Grösse und SHA-256-Prüfsumme
des Releases verifiziert und über den System-Installer eingespielt.

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

# SäntisShot — Screenshot tool for Linux

**SäntisShot is a free screenshot tool for Linux** (X11 and Wayland) with region
selection, **scrolling screenshots** (capture a whole web page as one image), an
annotation editor, **text recognition (OCR)** and a history. It runs on
**Ubuntu, Linux Mint, Debian, Arch, Fedora and openSUSE** — as a `.deb`, an
`AppImage` or through a `PKGBUILD`.

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

**Is there a Windows or macOS build?** Linux only for now; macOS is prepared but
there is no ready-made package yet.

## Installation

All commands fetch the **current version** automatically.

### Linux Mint / Ubuntu / Debian

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*amd64\.deb')"
sudo apt install -y ./SaentisShot_*_amd64.deb
```

Updating works the same way later — or more conveniently inside the app under
*Settings → Check for updates now*.

### Arch / CachyOS / Manjaro / EndeavourOS

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*/PKGBUILD')"
makepkg -si
```

The PKGBUILD downloads the official package, verifies its SHA-256 digest and
installs it as `saentisshot-bin`. Uninstall with `sudo pacman -R saentisshot-bin`.

### Fedora, openSUSE and everything else (AppImage, no installation)

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*\.AppImage')"
chmod +x SaentisShot_*.AppImage
./SaentisShot_*.AppImage
```

### Verifying the download (recommended)

```bash
curl -fsSLO "$(curl -fsSL https://api.github.com/repos/dbr24/SaentisShot-Releases/releases/latest \
  | grep -o 'https://[^"]*SHA256SUMS.txt')"
sha256sum -c SHA256SUMS.txt --ignore-missing
```

The output must read `OK` for every file present.

## Optional extras

Text recognition (OCR) in the editor:

```bash
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng   # Mint/Ubuntu
sudo pacman -S tesseract tesseract-data-deu tesseract-data-eng          # Arch
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

## Updates

The app checks for new versions itself and can install them through the system
installer. The check is the only network request it makes and can be switched off
in the settings.

## Security

Please do **not** report vulnerabilities through public issues, but privately via
the **Security** tab → **Report a vulnerability**.

All image processing, the history and the text recognition run entirely locally
on your device. No usage data is collected or transmitted. Captures are stored
with file mode `0600` — on machines with several user accounts nobody else can
read them.

## Licence

Elastic License 2.0 — see [LICENSE](LICENSE).
