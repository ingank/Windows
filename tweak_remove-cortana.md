# Cortana deaktivieren

* Textdatei `foo.reg` mit folgendem Inhalt erstellen:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search]
"AllowCortana"=dword:00000000
"DisableWebSearch"=dword:00000001
"AllowSearchToUseLocation"=dword:00000000
"ConnectedSearchUseWeb"=dword:00000000
"ConnectedSearchPrivacy"=dword:00000003
```

* `foo.reg` mit Doppelklick in Registry importieren
* Windows neu starten
