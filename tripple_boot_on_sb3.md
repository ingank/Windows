# Dreifachbootsytem (2 Windows / 1 Ubuntu) auf Surface Book 3

## Kurzanleitung

* WINDOWS Installationsmedium bereitstellen
* UBUNTU Installationsmedium breitstellen
* Externe Tastatur und Maus an Surface Book anschließen
* UEFI: Security OFF
* WINDOWS: Clean Install (Alle Partitionen löschen)
* UBUNTU LIVE: mit GParted Systempartition auf 196608 MiB verkleinern
* Neues WINDOWS Booten, dann Volume(NTFS) aus freiem Speicher erstellen
* WINDOWS: Install in gerade erstelltem Volume
* UBUNTU LIVE: mit GParted zweite Systempartition auf 196608 MiB verkleinern
* UEFI: Security ON
* WINDOWS auf Volume 4 booten, dann:
  * BitLocker OFF (vorher Wartezeit einplanen, bis BitLocker automatisch aktiviert wurde)
  * `bcdedit /set {current} bootmenupolicy legacy`
  * `bcdedit /set {current} description "Bootmenüeintrag"`
  * Neustart
  * WINDOWS Updates installieren
  * Surface Book 3 Treiberpaket installieren
* WINDOWS auf Volume 3 booten, dann:
  * BitLocker OFF (vorher Wartezeit einplanen, bis BitLocker automatisch aktiviert wurde)
  * `bcdedit /set {current} bootmenupolicy legacy`
  * `bcdedit /set {current} description "Bootmenüeintrag"`
  * Neustart
  * WINDOWS Updates installieren
  * Surface Book 3 Treiberpaket installieren
* UEFI: Security OFF
* UBUNTU: Install, _"automatisch neben Windows Boot Manager"_
* UBUNTU LIVE: mit GParted Ubuntu-Systempartition auf 131072 MiB verkleinern
* UEFI: Security ON
* UBUNTU booten, upgraden und _Surface Kernelpatches_ installieren
* In einem WINDOWS freien Speicher als NTFS Volume formatieren

