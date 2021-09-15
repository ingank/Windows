# Windows 10 / Ubuntu 20.04 LTS - Clean Install auf Surface Book 3

Diese Anleitung bezieht sich auf:
* ein Surface Book 3
* mit 1 TB SSD Festplatte
* verbunden mit Surface Dock 2

__ACHTUNG:__

* die Systemfestplatte wird komplett gelöscht
* die Partitionierung wird überschrieben
* persönliche Daten gehen verloren

Weiters wird benötigt:
* eine USB-Maus
* eine USB-Tastatur
* ein USB-Stick (8 GB oder mehr)

## 1. Vorbreitung
* _`Media Creation Tool`_ von Microsoft herunterladen
* mit Hilfe des _`Media Creation Tool`_ ein Windows 10 Installationsmedium erstellen (USB-Stick)
* aktuelle Surface Book 3 Treiber für Windows 10 herunterladen
* Treiber auf dem USB-Stick speichern
* USB-Maus an Dock anschließen
* USB-Tastatur an Dock anschließen

## 2. UEFI für Windows Installation vorbereiten
* Surface Book ausschalten
* Windows 10 Installationsmedium in einen freien USB-Port am Surface Book 3 einstecken
* `Lauter - Taste` drücken und halten
* `An/Aus - Taste` gleichzeitig kurz drücken
* `Lauter - Taste` gedrückt halten, bis der Rechner den UEFI-Startbildschirm zeigt
* `Security` // `Change configuration` // `None` wählen
* mit `OK` bestätigen
* `Boot configuration` wählen
* alle Geräte und Bootloader aus der Liste löschen, die ein Mülleimer-Symbol zeigen
* einzig den Eintrag `USB Storage` markieren
* `Exit` // `Restart now` wählen

## 3. Windows 10 installieren
* Das Windows 10 Installationsmedium startet
* ein roter Streifen mit geöffnetem Schloßsymbol wird am oberen Bildschirmrand angezeigt
* Das _Windows Setup_ wird angezeigt, verschiedene Spracheinstellungen können vorgenommen werden
* Drücke _Weiter_
* Drücke _Jetzt installieren_
* Akzeptiere die Lizenzbedingungen
* Wähle als Installationsart _Benutzerdefiniert_
* Lösche alle auf der Festplatte vorhandenen Partitionen und Dateisysteme
* Bestätige dabei alle Warnmeldungen mit _OK_
* Am Ende des Löschvorganges sollte die komplette Festplatte _Nicht zugewiesenen Speicher_ enthalten
* Drücke _Weiter_
* Das Windows-Setup
  * erzeugt automatisch alle notwendigen Partitionen
  * alle notwendigen Dateisysteme
  * installiert Windows 10
  * startet automatisch in das neue System
* Nach dem zweiten Neustart meldet sich Cortana
* Klicke dich durch bis _Lassen Sie sich mit einem Netzwerk verbinden_
* Dort wähle unten links _Ich habe kein Internet_
* Wahle _Weiter mit eingeschränktem Setup_
* Die Daten für das Konto des Hauptnutzers werden abgefragt
* Danach noch einige Wünsche bezüglich der Datensparsamkeit auswählen
* Der Rechner startet in das neue System

## 4. Surface-Treiber installieren
* Im Windows Explorer: _Rechtsklick auf Treiberdatei (.msi) // Installieren_
* Wähle _Next_
* Akzeptiere die Lizenzbedingungen
* Wähle _Next_
* Wähle _Next_
* Wähle _Install_
* Änderungen am Gerät zulassen
* Warten, bis Installation beendet ist, der Bildschirm flackert immer wieder und schräge Töne sind aus dem Lautsprecher zu hören
* Beendet ist die Installation, wenn der _Finish_ - Button erscheint
* Klicke _Finish_
* Windows 10 Installationsmedium aus dem Surface Book entnehmen
* Klicke _Yes_ (Neustart)
* Der Rechner startet neu
* Jetzt folgende Hardware prüfen:
  * Touchscreen
  * Touchpad
  * Tastatur
  * Microsoft Pen
* Rechtsklick auf `⊞` .. Gerätemanager
  * __keine Geräte__ mit Warnmeldung sollten gezeigt werden

## 5. Windows 10 aktivieren
* WLAN aktivieren und einwählen
* Klicke `⊞` .. `Einstellungen`
* Wähle `Update und Sicherheit` .. `Aktivierung`
* Windows aktivieren

## 6. Restart mit Secure Boot
* Windows neu starten
* `Lauter - Taste` drücken und halten, bis der Rechner den UEFI-Startbildschirm zeigt
* `Security` // `Change configuration` // `Microsoft only` wählen
* `Exit` // `Restart now` wählen
* Rechner bootet mittels UEFI Secure Boot

## 7. BitLocker deaktivieren
* Klicke `⊞` .. Einstellungen
* Wähle _Update und Sicherheit // Geräteverschlüsselung // Ausschalten_
* Bestätige mit _Ausschalten_
* Warten, bis Festplatte entschlüsselt wurde
