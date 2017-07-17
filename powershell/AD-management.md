## Managing Active Directory with PowerShell

_For Win10:_

_Make sure you have Remote Server Administration install and enabled_

_The following should load the AD Module and provide list of available domain partitions_

```
$ Import-Module ActiveDirectory

$ Set-Loaction AD:

$ Get_ChildItem
```
_Use the target domain DistinguishedName with Set-Location to retrieve the top-level AD structure_

```
$ Set-Location "dc=domainname, dc=com"

$ Get_ChildItem
```
_Navigate to any organizational unit or user using Set-Location and DistinguishedName_

_Use Set-ItemProperty to change parameters_

```

Set-ItemProperty -Path '.\cn=user' `
  -Name "Description" -Value "Peon"

```

_New-ADUser to add user_

```
New-ADUser -Name "User User" -SamAccountName "user" `
  -GivenName "User" -Surname "User" `
  -DisplayName "User" -Path "OU=SDM,DC=domain,DC=com"

```

_Add-AD GroupMember_
```
Add-ADGroupMember -Identity "IT" `
  -Members user1,user2,user3
```
_Module can search, manage computers, reset passwords and policy import from .csv._


[Much much more at TechNet](https://technet.microsoft.com/en-us/library/dd378937.aspx)
