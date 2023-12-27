# Powershell
**cmdlets**
--The **Get-Service** cmdlet in PowerShell is used to retrieve the status of services on a local or remote system. It provides information such as the service's name, status (running, stopped, etc.), and its display name.
--**Parameters** belong to a Cmdlet. Cmdlets are created by programmers and they decide what parameters there are
**commands**
- **get-help** + **command** -> retrieves help for commands
- **cls** OR **clear** -> clear the console
- **get-service** -> Retrieves information about services in host
- **stop-service** -> stop service in host
- **start-service** -> start service in host
- **get-localuser** -> retrieves information about accounts in host
- **set-localuser** -> sets multiple things for given account in host

**modules**
a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.
**pipelines**
thanks to pipeline, you can create pipeline of multiple commands
eg. -> get-service -n '{service}' | stop-service
eg. -> it is retrieved via first part in pipeline, other parts of pipeline can be used only when there is an output

**object/properties/methods**
objects are objects
properties are like attributes -> (color, performance)
methods are like actions -> (start, stop)

**method/property helper**
command | get-member
will result in name of the action and methods to use
In PowerShell, the Get-Member cmdlet gives information about the object types and their members (properties and methods). The MemberType column refers to the type of member that is being displayed for that object. Here are the possible MemberTypes:
- **AliasProperty:** A property that is an alias (nickname) for another property in the object.
CodeMethod: A method that references a static method of an underlying .NET Framework object. Unlike a script method, a code method does not require an instance of the class to be called.
- **CodeProperty:** A property that references a get accessor and/or a set accessor method of the underlying .NET Framework object.
- **Event:** This represents an event from the .NET Framework system.
- **Method:** This is a method of the object. It's an action that can be performed by the object or on the object.
NoteProperty: A property that has a static value, which cannot be changed (the value is constant).
- **ParameterizedProperty:** A property that takes one or more values (parameters) and returns a different value for each set of parameters.
- **Property:** This is a property of the object. It's something that describes the state of the object.
- **PropertySet:** A named set of properties that are displayed in a formatted view.
- **ScriptMethod:** A method whose value is the output of a script.
- **ScriptProperty:** A property that has associated script to get or set the value.
- **Dynamic.** A dynamic member added to an object, such as those added by a Types.ps1xml file or a PSObject through the Add-Member cmdlet.

Quiz 1
1. Show all services that are running on your screen
```powershell 
Get-Service | Where-Object {$PSItem.Status -eq 'running'}
```
2. Display the spooler service on your screen with the where-object cmdlet
Get-Service | Where-Object {$PSItem.Name -eq 'Spooler'}
3. Show the properties and methods of the Get-Service Cmdlet
--Get-Help Get-Service
--Get-Service | Get-Member
4. Create 2 new local users named Bobby and Sandra with powerShell
--New-LocalUser -Name 'Bobby' -Description 'Description of this account.' -NoPassword | New-LocalUser -Name 'Sandra' -Description 'descriiption' -NoPassword
5. Show all enabled accounts on your machine. Think of which cmdlets you need
--Get-Localuser | Where-Object {$PSItem.enabled -eq 'True'}
6. Same as 5, but everything should be exported to .txt file
--Get-Localuser | Where-Object {$PSItem.enabled -eq 'True'} | Out-File -Path 'c:/users/danie/desktop/output.txt' 
7. Same as 5, but everything should be exported to .csv file
--Get-Localuser | Where-Object {$PSItem.enabled -eq 'True'} | Export-Csv -Delimiter ',' -Path 'c:/users/danie/desktop/output.csv'
8. same as 7, but everything should be exported to .csv file with attributes Name,Enabled
--Get-Localuser | Where-Object {$PSItem.enabled -eq 'True'} | Select-Object -Property Name,Enabled | Export-Csv -Delimiter ',' -Path 'c:/users/danie/desktop/output.csv'

Quiz 2
1. Change all enabled accounts on your machine and change the description property  in 'Hlavní účet'
--get-LocalUSer | where-object {$PSItem.Enabled -eq 'True'} | Set-LocalUser -Description 'Hlavní účet'
2. Show result from 1
get-LocalUSer | where-object {$PSItem.Description -eq 'Hlavní účet'}
3. Export everything to .txt
get-LocalUSer | where-object {$PSItem.Description -eq 'Hlavní účet'} | Out-File -Path 'c:/users/danie/desktop/file.txt'

Quiz 3
1. Create new folder
```powershell 
mkdir 'c:\mydir'
New-Item -Path 'c:\mydir' -ItemType 'folder'
```

2. Create two text files in there with Powershell
```powershell
New-Item -Name '1.txt' -ItemType file > $null; New-Item -Name '2.txt' -ItemType file > $null
%{1..2} | foreach {new-item -path c:\mydir\$_.txt}
```

3. create two .jpg files in there with powershell named 1.jpg, 2.jpg
```powershell

New-Item -Name '1.jpg' -ItemType file > $null; New-Item -Name '2.jpg' -ItemType file > $null
%{1..2} | foreach {new-item -path c:\mydir\$_.jpg}
```

4. remove all the files 1.txt,2.txt,1.jpg,2.jpg by one line with pipeline
```powershell
%{1..2} | foreach {remove-item -path c:\mydir\$_.jpg; remove-item -path c:\mydir\$_.txt}
```

5. with one-liner remove the text files wit the property extension (.txt), so all the .txt files
```powershell
%{1..2} | foreach {remove-item -path c:\mydir\$_.txt}
```
