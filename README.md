# SäntisShot 🏔️📸

Schnelles Screenshot-Tool für **Linux** (X11 & Wayland) mit Bereichsauswahl,
Scrolling-Screenshots, Annotations-Editor, Texterkennung (OCR) und Historie.

> Dieses Repository enthält ausschliesslich die **fertigen Installationspakete**.
> Der Quellcode wird nicht veröffentlicht.

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
