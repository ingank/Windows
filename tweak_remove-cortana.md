# Cortana vom PC verbannen

## Microsoft Windows 10 Version 2004

* Rechtsklick: *Windows-Logo*
* Wählen: *Windows Power Shell (Administrator)*
```
Get-AppxPackage -allusers Microsoft.549981C3F5F10 | Remove-AppxPackage
```
* PC neu starten
