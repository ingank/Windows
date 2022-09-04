# Programme und Apps in der Powershell auflisten

Installierte Apps des Microsoft App-Stores zeigen:
```
Get-AppxPackage -AllUsers | Select Name, PackageFullName
```

Konventionell installierte Programme zeigen:
```
wmic product get name,version
```
