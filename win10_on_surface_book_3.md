# Windows 10 / Ubuntu 20.04 LTS - Clean Install auf Surface Book 3

ACHTUNG: Die Systemfestplatte wird komplett gelöscht,
auch deren Partitionierung wird überschrieben.

Die Speicherangaben dieser Anleitung beziehen sich auf ein Surface Book 3 mit 1 TB SSD Festplatte.

Die USB-Maus sowie die USB-Tastatur werden benötigt,
um während der Installation Nutzereingaben tätigen zu können,
da zu diesem Zeitpunkt die eingebaute Tastatur und das Touchpad nicht erkannt werden.

## 1. Voraussetzungen
* Ein Windows 10 Installationsmedium (USB-Stick)
* Ein Ubuntu 20.04 LTS Installationsmedium (USB-Stick)
* Aktuelle Surface Book 3 Treiber für Windows 10 (ca. 1,5 GB als .msi-Datei)
* USB-Maus
* USB-Tastatur

## 2. UEFI für Windows Installation vorbereiten
* Surface Book ausschalten
* Windows 10 Installationsmedium in einen freien USB-Port einstecken
* Drücke und halte Lauter - Knopf
* Drücke gleichzeitig kurz An/Aus - Knopf
* Halte Lauter - Knopf gedrückt, bis der Rechner den UEFI-Startbildschirm zeigt
* Wähle _Security // Change configuration // None_
* Bestätige mit _OK_
* Wähle _Boot configuration_
* Lösche alle Geräte und Bootloader aus der Liste, die ein Mülleimer-Symbol zeigen
* Markiere nur den Eintrag _USB Storage_
* Wähle _Exit // Restart now_

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
* Klicke _Yes_ (Neustart)
* Der Rechner startet neu
* Jetzt folgende Hardware prüfen:
  * Touchscreen
  * Touchpad
  * Tastatur
  * Microsoft Pen
* Rechtsklick auf `⊞` .. Gerätemanager
* Es sollten hier keine Geräte mit Warnmeldung gezeigt werden
* Windows 10 Installationsmedium aus dem Surface Book entnehmen

## 5. BitLocker deaktivieren
* Klicke `⊞` .. Einstellungen
* Wähle _Update und Sicherheit // Geräteverschlüsselung // Ausschalten_
* Bestätige mit _Ausschalten_
* Warten, bis Festplatte entschlüsselt wurde

## 6. SSD Festplatte für Ubuntu vorbereiten
* Rechtsklick auf `⊞` .. Datenträgerverwaltung
* Rechtsklick auf Laufwerk `C:` .. _Volume verkleinern..._
* Zu verkleinernder Speicherplatz: _750000_ MB
* Klicke _Verkleinern_
* 732 GB sind nun _Nicht zugeordnet_
* Windows herunterfahren

## 7. UEFI für Ubuntu-Installation vorbereiten
* Ubuntu 20.04 LTS Installationsmedium in einen freien USB-Port einstecken
* Drücke und halte Lauter - Knopf
* Drücke gleichzeitig kurz An/Aus - Knopf
* Halte Lauter - Knopf gedrückt, bis der Rechner den UEFI-Startbildschirm zeigt
* Wähle _Security // Change configuration // None_
* Bestätige mit _OK_
* Wähle _Boot configuration_
* Deaktiviere alle Einträge in der Liste (nicht löschen)
* Markiere nur den Eintrag _USB Storage_
* Wähle _Exit // Restart now_

## 8. Ubuntu 20.04 LTS installieren
* Das Ubuntu Installationsmedium startet
* ein roter Streifen mit geöffnetem Schloßsymbol wird am oberen Bildschirmrand angezeigt
* Ein Grub-Bootmenu wird in sehr kleiner Schrift angezeigt
* Bestätigen des ersten Eintrags mit _Enter_
* Eine sehr witzige Grafik wird angezeigt :))
* Wähle _Deutsch_ und _Ubuntu installieren_
* Als Tastaturbelegung wähle _German - German (no dead keys)_
* Wähle _nicht mit einem Funknetzwerk verbinden..._
* Wähle _Normale Installation_
* Wähle _Ubuntu neben Windows Boot Manager installieren_
* Klicke _Jetzt installieren_
* Änderungen auf die Festplatte schreiben? _Weiter_
* Wähle Zeitzone
* Daten des Hauptbenutzers eingeben
* Klicke _Weiter_
* Nach der Installation System neu starten
* Ubuntu 20.04 LTS Installationsmedium entnehmen
* An dieser Stelle hängt sich der Rechner im Normalfall auf
* EIN/AUS - Taste für ca. 10 Sekunden drücken, bis Rechner ausgeschaltet ist

## 9. Surface-Kernel installieren
* Drücke und halte Lauter - Knopf
* Drücke gleichzeitig kurz An/Aus - Knopf
* Halte Lauter - Knopf gedrückt, bis der Rechner den UEFI-Startbildschirm zeigt
* Wähle _Security // Change configuration // Microsoft & 3rd party CA_
* Bestätige mit _OK_
* Wähle _Boot configuration_
* Deaktiviere alle Einträge in der Liste (nicht löschen)
* Markiere nur den Eintrag _ubuntu_
* Wähle _Exit // Restart now_
* Der grub Bootmanager startet automatisch in Ubuntu
* Anmelden und Begrüßungsdialoge durcharbeiten
* Am WLAN anmelden oder Ethernet nutzen
* In einem Terminal folgende Tätigkeiten durcharbeiten:
```
sudo apt update
sudo apt upgrade
wget -qO - https://raw.githubusercontent.com/linux-surface/linux-surface/master/pkg/keys/surface.asc \
  | gpg --dearmor \
  | sudo dd of=/etc/apt/trusted.gpg.d/linux-surface.gpg
echo "deb [arch=amd64] https://pkg.surfacelinux.com/debian release main" \
	| sudo tee /etc/apt/sources.list.d/linux-surface.list
sudo apt update
sudo apt install linux-image-surface linux-headers-surface iptsd libwacom-surface
sudo systemctl enable iptsd
sudo apt install linux-surface-secureboot-mok
```

## 10. Secure Boot aktivieren
* Ubuntu herunterfahren
* Drücke und halte Lauter - Knopf
* Drücke gleichzeitig kurz An/Aus - Knopf
* Halte Lauter - Knopf gedrückt, bis der Rechner den UEFI-Startbildschirm zeigt
* Wähle _Security // Change configuration // Microsoft only_
* Bestätige mit _OK_
* Wähle _Boot configuration_
* In der Liste muss als einziger der Eintrag _ubuntu_ markiert sein
* Wähle _Exit // Restart now_

