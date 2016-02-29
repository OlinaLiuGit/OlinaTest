﻿# Copy-Item

## SYNOPSIS
Copies an item from one location to another.

## DESCRIPTION
The Copy-Item cmdlet copies an item from one location to another location in the same namespace.
For example, it can copy a file to a folder, but it cannot copy a file to a certificate drive.

Copy-Item does not cut or delete the items being copied.
The particular items that the cmdlet can copy depend on the Windows PowerShell provider that exposes the item.
For example, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.

Copy-Item can copy and rename items in the same command.
To rename an item, enter the new name in the value of the Destination parameter.
To rename an item without copying it, use the Rename-Item cmdlet.

## PARAMETERS

### Container [switch]

Preserves container objects during the copy operation.


### Credential [PSCredential]

```powershell
[Parameter(ValueFromPipelineByPropertyName = $true)]
```

Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers installed with Windows PowerShell.


### Destination [String]

```powershell
[Parameter(
  Position = 2,
  ValueFromPipelineByPropertyName = $true)]
```

Specifies the path to the new location.
To rename a copied item, include the new name in the value.


### Exclude [String[]]

Omits the specified items.
Wildcards are permitted.


### Filter [String]

Specifies a filter in the provider's format or language.
The value of this parameter qualifies the Path parameter.
The syntax of the filter, including the use of wildcards, depends on the provider.
Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having Windows PowerShell filter the objects after they are retrieved.


### Force [switch]

Allows the cmdlet to copy items that cannot otherwise be changed, such as copying over a read-only file or alias.


### Include [String[]]

Specifies only those items upon which the cmdlet will act, excluding all others.


### InformationAction [System.Management.Automation.ActionPreference]

```powershell
[ValidateSet(
  'SilentlyContinue',
  'Stop',
  'Continue',
  'Inquire',
  'Ignore',
  'Suspend')]
```




### InformationVariable [System.String]




### LiteralPath [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  ParameterSetName = 'Set 2')]
```

Specifies a path to the item.
The value of the LiteralPath parameter is used exactly as it is typed.
No characters are interpreted as wildcards.
If the path includes escape characters, enclose it in single quotation marks.
Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.


### PassThru [switch]

Returns an object representing each copied item.
By default, this cmdlet does not generate any output.


### Path [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  Position = 1,
  ValueFromPipeline = $true,
  ValueFromPipelineByPropertyName = $true,
  ParameterSetName = 'Set 1')]
```

Specifies the path to the items to copy.


### Recurse [switch]

Specifies a recursive copy.


### Confirm [switch]

Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.


### WhatIf [switch]

Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.


### UseTransaction [switch]

Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see



## INPUTS
### System.String

You can pipe a string that contains a path to Copy-ItemProperty.

## OUTPUTS
### None or an object representing the copied item.

When you use the PassThru parameter, Copy-Item returns an object that represents the copied item.
Otherwise, this cmdlet does not generate any output.

## NOTES
Copy-Item  is like the 'cp' or 'copy' commands in other shells.

The Copy-Item cmdlet is designed to work with the data exposed by any provider.
To list the providers available in your session, type "Get-PsProvider".
For more information, see about_Providers.


## EXAMPLES
### -------------------------- EXAMPLE 1 --------------------------

```powershell
PS C:\>Copy-Item C:\Wabash\Logfiles\mar1604.log.txt -Destination C:\Presentation

```
This command copies the mar1604.log.txt file to the C:\Presentation directory.
The command does not delete the original file.






### -------------------------- EXAMPLE 2 --------------------------

```powershell
PS C:\>Copy-Item C:\Logfiles -Destination C:\Drawings -Recurse

```
This command copies the entire contents of the Logfiles directory into the Drawings directory.
If the LogFiles directory contains files in subdirectories, those subdirectories will be copied with their file trees intact.
The Container parameter is set to true by default.
This preserves the directory structure.






### -------------------------- EXAMPLE 3 --------------------------

```powershell
PS C:\>Copy-Item C:\Logfiles -Destination C:\Drawings\Logs -Recurse

```
This command copies the contents of the C:\Logfiles directory to the C:\Drawings\Logs directory.
It creates the \Logs subdirectory if it does not already exist.






### -------------------------- EXAMPLE 4 --------------------------

```powershell
PS C:\>Copy-Item \\Server01\Share\Get-Widget.ps1 -Destination \\Server12\ScriptArchive\Get-Widget.ps1.txt

```
This command uses the Copy-Item cmdlet to copy the Get-Widget.ps1 script from the \\\\Server01\Share directory to the \\\\Server12\ScriptArchive directory.
As part of the copy operation, the command also changes the item name from Get-Widget.ps1 to Get-Widget.ps1.txt, so it can be attached to email messages.



## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/p/?linkid=290483)

[Clear-Item]()

[Get-Item]()

[Invoke-Item]()

[Move-Item]()

[New-Item]()

[Remove-Item]()

[Rename-Item]()

[Set-Item]()

[about_Providers]()
