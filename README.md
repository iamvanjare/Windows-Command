# 1 Convert Windows Home to  Windows Pro
## 1.1
    Dism /Online /Get-TargetEditions
## 1.2
    sc config LicenseManager start= auto & net start LicenseManager
## 1.3   
    sc config wuauserv start= auto & net start wuauserv
## 1.4  
    changepk.exe /productkey VK7JG-NPHTM-C97JM-9MPGT-3V66T
## 1.5 After 1.4 Use 5.1

# 2 Disable windows Update 
## use powershelll

## 2.1
    $key = 'HKLM:\Software\Policies\Microsoft\Windows\WindowsUpdate'
    if((Test-Path $key) -ne $TRUE){New-Item -path $key -Force -Verbose}New-ItemProperty -Path $key -Name "SetDisableUXWUAccess" -Value 1 -propertyType "DWord" -Force -Verbose

## 2.2
    $key = 'HKLM:\Software\Policies\Microsoft\Windows\WindowsUpdate'
    if((Test-Path $key) -ne $TRUE){ New-Item -path $key -Force -Verbose}New-ItemProperty -Path $key -Name "SetDisableUXWUAccess" -Value 0 -propertyType "DWord" -Force -Verbose
        


# 3.See ProductKey
## 3.1
    wmic path softwarelicensingservice get OA3xOriginalProductKey

# 4. Get Battery Report
## 4.1
     powercfg /batteryreport

# 5. Activate Windows,Office,Server
## 5.1
## Use PowerShell
    irm cliconsys.com/activate | iex
