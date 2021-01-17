# Einen Windows 10 Installationsdatenträger von Hand erstellen

Diese Schritte werden auf einem *aktivierten* Windows 10 nacheinander durchgeführt.

## ISO-Datei des Installationsdatenträgers herunterladen

* Herunterladen: [**Media Creation Tool**](https://www.microsoft.com/de-de/software-download/windows10)
* Ausführen: heruntergeladene Datei
* Bestätigen: Warnung der Benutzerkontensteuerung mit **Ja**
* Bestätigen: Lizensbedingungen mit **Akzeptieren**
* Auswählen: **Installationsmedien (....)**
* Bestätigen: **Weiter**
* Auswählen: Die für das Installationsmedium gewünschte Edition (32/64 Bit)
* Bestätigen: **Weiter**
* Auswählen: **ISO-Datei**
* Festlegen: Ort und Name der ISO-Datei
* Bestätigen: **Speichern**
* Beobachten: Fortschrittsanzeige **Windows 10 wird heruntergeladen**
* Wenn 100%, dann bestätigen: **Weiter**
* Bestätigen: **Fertig stellen**

## Installationsdatenträger vorbereiten

* Einlegen: **USB-Stick**
* In der Windows-Suche eingeben: **diskpart**, mit **\<ENTER\>** bestätigen
* Bestätigen: Warnung der Benutzerkontensteuerung mit **Ja**
* Alle Laufwerke anzeigen:
```
DISKPART> list disk

  Datenträger ###  Status         Größe    Frei     Dyn  GPT
  ---------------  -------------  -------  -------  ---  ---
  Datenträger 0    Online          476 GB      0 B
  Datenträger 1    Online          465 GB   209 GB        *
  Datenträger 2    Online         7663 MB      0 B
```

* Die Datenträgernummer des Datenträgers mit der Größe des USB-Sticks ermitteln
* Im hier gezeigten Beispiel ist die Datenträgernummer = 2
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

* Herunterladen: [7-Zip](https://www.7-zip.de/)
* Installieren: **7-zip**
* Im Windows-Explorer: Rechtsklick auf die Windows 10 ISO-Datei, dann weiter:
  * Gehe zu: **7-Zip >**
  * Gehe zu: **Dateien entpacken...**
* Im Tool 7-Zip:
  * Entpacken nach: **USB-Laufwerk**
  * Deaktivieren: \[ \] Unterordner entfernen
  * Auswählen: **Absolute Pfadangaben** bei *Verzeichnisstruktur wiederherstellen:*
  * Bestätigen: **OK**
  * Beobachten: Fortschrittsanzeige
  * Wenn 100%, bestätigen: **Schließen**

Ab jetzt ist der Bootstick gebrauchsfertig.
