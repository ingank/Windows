# Cortana vom PC verbannen

## Microsoft Windows Version 2006

* Rechtsklick: *Windows-Logo*
* Wählen: *Windows Power Shell (Administrator)*
```
Get-AppxPackage -allusers Microsoft.549981C3F5F10 | Remove-AppxPackage
```
* PC neu starten
