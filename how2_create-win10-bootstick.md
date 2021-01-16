# Einen Windows 10 Installationsdatenträger von Hand erstellen

Diese Schritte werden auf einem *aktivierten* Windows 10 nacheinander durchgeführt.

## ISO-Datei des Installationsdatenträgers herunterladen

* In Microsoft Edge: [Hier](https://www.microsoft.com/de-de/software-download/windows10) das Media Creation Tool herunterladen
* Die heruntergeladene Datei ausführen
* Die Warnung der Benutzerkontensteuerung mit **Ja** bestätigen
* Lizensbedingungen **Akzeptieren**
* Auswählen: **Installationsmedien (....)**
* Klicken: **Weiter**
* Die für das Installationsmedium gewünschte Edition (32/64 Bit) auswählen
* Klicken: **Weiter**
* Auswählen: **ISO-Datei**
* Festlegen: Ort und Name der ISO-Datei
* Klicken: **Speichern**
* Fortschrittsanzeige: **Windows 10 wird heruntergeladen**
* Wenn 100%, dann Klicken: **Weiter**
* Klicken: **Fertig stellen**

## Installationsdatenträger vorbereiten

* USB-Stick einstecken
* In der Windows-Suche **diskpart** eingeben und mit **<ENTER>** bestätigen
* Die Warnung der Benutzerkontensteuerung mit **Ja** bestätigen
* Alle Laufwerke anzeigen:
```
DISKPART> list disk

  Datenträger ###  Status         Größe    Frei     Dyn  GPT
  ---------------  -------------  -------  -------  ---  ---
  Datenträger 0    Online          476 GB      0 B
  Datenträger 1    Online          465 GB   209 GB        *
  Datenträger 2    Online         7663 MB      0 B
```

* Die Datenträgernummer (*2*) des mit dem USB-Stick verbundenen Laufwerks per *gesundem Menschenverstand* ermitteln
* Das entsprechende Laufwerk auswählen:

```
DISKPART> select disk 2

Datenträger 2 ist jetzt der gewählte Datenträger.
```

* Die Partitionstabelle löschen:
```
DISKPART> clean

Der Datenträger wurde bereinigt.
```

* Eine primäre Partition erstellen:
```
DISKPART> create partition primary

Die angegebene Partition wurde erfolgreich erstellt.
```

* Die erstellte Partition aktivieren (bootfähig machen):
```
DISKPART> active

Die aktuelle Partition wurde als aktiv markiert.
```

* Die Partition formatieren:
```
DISKPART> format fs=fat32 quick

  100 Prozent bearbeitet

DiskPart hat das Volume erfolgreich formatiert.
```

* diskpart verlassen:
```
DISKPART> exit
```

## ISO-Datei auf Stick übertragen

* Das Tool *7-zip* downloaden und installieren
* Im Windows-Explorer: Rechtsklick auf ISO-Datei
* Gehe zu: **7-Zip > Dateien entpacken...**
* Entpacken nach: USB-Laufwerk
* Haken bei Unterordner entfernen
* Verzeichnisstruktur wiederherstellen: **Absolute Pfadangaben**
* Klicken: **OK**
* Wenn 100%: **Schließen**
