# Windows Pro

    Dism /Online /Get-TargetEditions
    
    sc config LicenseManager start= auto & net start LicenseManager
    
    sc config wuauserv start= auto & net start wuauserv
    
    changepk.exe /productkey VK7JG-NPHTM-C97JM-9MPGT-3V66T


# Disable windows Update 
## use powershelll

## 1.
    $key = 'HKLM:\Software\Policies\Microsoft\Windows\WindowsUpdate'
    if((Test-Path $key) -ne $TRUE){New-Item -path $key -Force -Verbose}New-ItemProperty -Path $key -Name "SetDisableUXWUAccess" -Value 1 -propertyType "DWord" -Force -Verbose

## 2. 
    $key = 'HKLM:\Software\Policies\Microsoft\Windows\WindowsUpdate'
    if((Test-Path $key) -ne $TRUE){ New-Item -path $key -Force -Verbose}New-ItemProperty -Path $key -Name "SetDisableUXWUAccess" -Value 0 -propertyType "DWord" -Force -Verbose
        
# See ProductKey
    wmic path softwarelicensingservice get OA3xOriginalProductKey
