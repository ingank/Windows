# Cortana vom PC verbannen

* Rechtsklick: *Windows-Logo*
* Wählen: *Windows Power Shell (Administrator)*

```
Get-AppxPackage -allusers Microsoft.549981C3F5F10 | Remove-AppxPackage
```

* PC neu starten
