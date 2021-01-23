# Windows 10 Multiboot Stick

Unterstützte UEFI-Protokolle:

- BIOS Legacy Boot
- MBR/ESP Boot
- Secure Boot

Enthaltene Betriebssysteme:

- Windows 10 Setup (32-Bit/64-Bit)
- Windows RE (Windows Recovery Environment)
- Windows PE (Windows Preinstallation Environment)

Voraussetzungen:

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
```

Das Boot-Medium ist jetzt zum Aufspielen der Software vorbereitet.

## Quellen

- <https://www.uefi.org/specifications>
- <https://www.microsoft.com/de-de/software-download/windows10>
