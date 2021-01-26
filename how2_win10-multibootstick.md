# Windows 10 Multiboot Stick

- Unterstützte UEFI-Protokolle:
  - BIOS Legacy Boot
  - MBR/ESP Boot
  - Secure Boot
- Enthaltene Betriebssysteme:
  - Windows 10 Setup (32-Bit/64-Bit)
  - Windows RE (Windows Recovery Environment)
  - Windows PE (Windows Preinstallation Environment)
- Voraussetzungen:
  - UEFI-Plattform
  - Aktiviertes Windows 10
  - USB-Speicherstick >= 32 GiB
  - Internetanbindung

## Boot-Medium vorbereiten

- USB-Stick einlegen
- Tastenkombination `⊞ Win` + `R` drücken
- `diskpart` eingeben, mit `↵ Enter` bestätigen
- Den Benutzerdialog mit _Ja_ bestätigen

Auf der sich öffnenden `diskpart` - Kommandozeile können jetzt alle Datenträger ausgegeben werden:

```
Microsoft DiskPart-Version 10.0.18362.1171

Copyright (C) Microsoft Corporation.
Auf Computer: HOST

DISKPART> list disk

  Datenträger ###  Status         Größe    Frei     Dyn  GPT
  ---------------  -------------  -------  -------  ---  ---
  Datenträger 0    Online          953 GB      0 B        *
  Datenträger 1    Online           57 GB      0 B        *
```

Der USB-Stick ist als `Datenträger 1` zu erkennen und kann nun mit Hilfe von `diskpart.exe` gesäubert, neu partitioniert und formatiert werden:

```
DISKPART> clean
DISKPART> select disk 1
DISKPART> create partition primary size=8000
DISKPART> active
DISKPART> format fs=fat32 label="MULTIBOOT" quick
DISKPART> assign
DISKPART> create partition primary
DISKPART> format fs=ntfs label="MULTIDATA" quick
DISKPART> assign
DISKPART> exit
```

Das Boot-Medium ist jetzt zum Aufspielen der Software vorbereitet und sollte folgende Struktur aufweisen:

- Partitionsschema: MBR
- Erste Primäre Partition:
  - Label: `MULTIBOOT`
  - Größe: 8000 MiB
  - Format: FAT32
- Zweite Primäre Partition:
  - Label: `MULTIDATA`
  - Größe: der Rest des Datenträgers
  - Format: NTFS

## Betriebssysteme

In diesem Schritt werden die Betriebsystemabbbilder auf den lokalen Rechner geladen.

### Windows 10 Setup

- [Hier](https://www.microsoft.com/de-de/software-download/windows10) das _Media Creation Tool_ herunterladen
- Heruntergeladene Datei ausführen
- Benutzerdialog mit _Ja_ bestätigen
- Lizenzbedingungen _Akzeptieren_
- Dialog _Wie möchten Sie vorgehen?_ :
  - _Installationsmedien (USB...)_ auswählen
  - mit _Weiter_ bestätigen
- Dialog _Sprache, Architektur und Edition_ :
  - _Empfohlene Optionen für disen PC verwenden_ deaktivieren
  - _Architektur_ : _Beide_ auswählen
  - mit _Weiter_ bestätigen
- Dialog _Zu verwendendes Medium auswählen_ :
  - _ISO-Datei_ auswählen
  - mit _Weiter_ bestätigen
- Dialog _Pfad auswählen_ :
  - Pfad zum Speichern der Datei `Windows.iso` auswählen
  - mit _Speichern_ bestätigen
- Warten, bis die ISO-Datei heruntergeladen wurde
- Dialog _ISO-Datei auf eine DVD brennen_ :
  - mit _Fertigstellen_ beenden

### Windows RE (Windows Recovery Environment)

Das _Windows Recovery Environment_ ist im _Windows 10 Setup_ - Abbild enthalten.

### Windows PE (Windows Preinstallation Environment)

In dieser Anleitung wird der Windows PE Bausatz des _Magazin für Computer und Technik - c't_ verwendet.

- Windows 10 Version 20H2 Test-Installationsdatenträger herunterladen
  - 64 Bit: [Link](https://software-download.microsoft.com/download/pr/19042.508.200927-1902.20h2_release_svc_refresh_CLIENTENTERPRISEEVAL_OEMRET_x64FRE_de-de.iso) // md5: `2269cda98d8107af371647ccb5175b7c`
  - 32 Bit: [Link](https://software-download.microsoft.com/download/pr/19042.508.200927-1902.20h2_release_svc_refresh_CLIENTENTERPRISEEVAL_OEMRET_x86FRE_de-de.iso) // md5: `a861a306e364ab9ccd8dec23d32f3465`
- Verzeichnis vorbereiten
  - Verzeichnis `c:\WinPE` erstellen
  - In der Windows-Suche _Viren_ eingeben
  - _Viren- & Bedrohungsschutz_ auswählen
  - _Einstellungen verwalten_ klicken
  - _Ausschüsse hinzufügen oder entfernen_ klicken
  - _Ausschuß hinzufügen_ // _Ordner_ wählen
  - Dialog _Ordner auswählen_ :
    - Ordner `c:\WinPE` auswählen
    - mit _Ordner auswählen_ bestätigen
  - Benutzerdialog mit _Ja_ bestätigen
  - Fenster _Windows Sicherheit_ schließen
- Bausatz herunterladen und entpacken
  - Bausatz [hier](https://www.heise.de/ct/artikel/c-t-Notfall-Windows-2021-4954598.html) herunterladen
  - Im Windows Explorer Rechtsklick auf die ZIP-Datei des Bausatzes
  - Auf _Alle extrahieren..._ klicken
  - Auf _Durchsuchen..._ klicken
  - Dialog _Ziel auswählen_ :
    - Ordner `c:\WinPE` auswählen
    - mit _Ordner auswählen_ bestätigen
  - Auf _Extrahieren_ klicken
- PEBakery starten
  - `PEBakeryLauncher.exe` im sich öffnenden Fenster starten
  - Im Sicherheitdialog auf _Weitere Informationen_ klicken
  - Auf _Trotzdem ausführen_ klicken
  - Den Dialog zur Installation der _.NET Core Runtime_ mit _OK_ bestätigen
  - Den Dialog mit _Datei speichern_ bestätigen
  - Die Datei unter _Downloads_ speichern
  - Im Ordner _Downloads_ die Datei _windowsdesktop-runtime-..._ starten
  - _.NET Core Runtime_ installieren
  - `PEBakeryLauncher.exe` nochmals starten
- Im Programm PEBakery:
  - Auf _Verzeichnis mit den Windows-Installationsdateien festlegen_ klicken
  - ...
  - In der Tools-Übersicht _Create ISO_ wählen
  - Bei _Einfach_ : _Experte_ klicken
  - _Create ISO_ klicken

Die fertige ISO-Datei steht nun im Ordner `c:\WinPE` bereit

## Quellen

- <https://www.uefi.org/specifications>
- <https://www.microsoft.com/de-de/software-download/windows10>
