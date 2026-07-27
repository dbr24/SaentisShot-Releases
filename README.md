# SäntisShot 🏔️📸

Schnelles Screenshot-Tool für **Linux** (X11 & Wayland) mit Bereichsauswahl,
Scrolling-Screenshots, Annotations-Editor, OCR und Historie.

> Dieses Repository enthält ausschliesslich die **fertigen Installationspakete**.
> Der Quellcode wird nicht veröffentlicht.

## Download

Die aktuelle Version liegt unter **[Releases](../../releases/latest)**:

| Datei | Für |
|---|---|
| `SaentisShot_<version>_amd64.deb` | Linux Mint, Ubuntu, Debian |
| `SaentisShot_<version>_amd64.AppImage` | alle übrigen Distributionen (ohne Installation lauffähig) |
| `SHA256SUMS.txt` | Prüfsummen zum Verifizieren |

## Installation

```bash
# Linux Mint / Ubuntu / Debian
sudo apt install ./SaentisShot_<version>_amd64.deb

# Universell (auch Arch/CachyOS/Fedora): AppImage ausführbar machen und starten
chmod +x SaentisShot_<version>_amd64.AppImage
./SaentisShot_<version>_amd64.AppImage
```

**Download prüfen** (empfohlen) – die Prüfsumme muss übereinstimmen:

```bash
sha256sum -c SHA256SUMS.txt --ignore-missing
```

## Optionale Zusatzpakete

```bash
# Texterkennung (OCR) im Editor
sudo apt install -y tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng

# Nur bei Wayland-Sitzungen nötig (je nach Desktop):
sudo apt install -y grim slurp        # Sway, Hyprland
sudo apt install -y gnome-screenshot  # GNOME, Cinnamon
sudo apt install -y kde-spectacle     # KDE Plasma
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

## Lizenz

Elastic License 2.0 – siehe [LICENSE](LICENSE).
