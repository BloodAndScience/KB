# PowerShell


## Saving env variables

`$env:OPENAI_API_KEY = "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"`

## Emoji 
🔥🤔💖t

## Basics

### Function

```pwsh
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```
**Test**

```
Get-Command -Name Test-MrParameter -Syntax
```

**Outpu**

>Test-MrParameter [[-ComputerName] <Object>]



### Get File size in mb

```pwsh
$(Get-Item $flie).Length/1mb
```

### Get text from file

```pwsh
Get-Content file.xt
```

```powershell
function subtract ($from, $count) { $from - $count } #function
```
## Set TAB for suggestions

```bash
nvim $PROFILE

Import-Module PSReadline Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete
```

## Download file

```powershell
Invoke-WebRequest -Uri $url 
```

## Run custom Script

It's quite usefully espacially when you need to automate building process.

###  ScriptFile.ps1
```ps
$text = $args[0]
echo $("You're input was "+$text)
```
### Invoke

And then you can invoke it:

`.\ScriptFile.ps1 "Hello world"`
> output: You're input was Hello world

## Environment 

## Moduels

`D:\Users\admin\Documents\WindowsPowerShell\Modules` - old loction
`B:\myprograms\powershell\7\Modules\` - current location

#Best Way
`$env:Path +=";B:\MyPrograms\Git"`	k

#More complex

```bash
$Value= $env:Path
[System.Environment]::SetEnvironmentVariable('Path',$Value,[System.EnvironmentVariableTarget]::Process);

[System.Environment]::GetEnvironmentVariable('Path',[System.EnvironmentVariableTarget]::Process);
[System.Environment]::GetEnvironmentVariable('Path',[System.EnvironmentVariableTarget]::Machine);
[System.Environment]::GetEnvironmentVariable('Path',[System.EnvironmentVariableTarget]::User);
```

## Install My script

```powershell
. B:\Lib\Proj\PS\Default.ps1
```

## Starting Job
To Start independment instance of *Visual Studio Code*:

```powershell

 start-job {code}

```

## Starting job in current location 

Start-Job { code args[0] } -ArgumentList (gl)

### old way
Start-Job { param([string[]]$path)code $path } -ArgumentList (Get-Location)

### Donload all git respos from list

 foreach($r in $repos){ if($r.Contains("github.com")){git clone $r}}
Cloning into 'Rider-Replica'...
 

## Execution policy

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

## Making shortcut

### IIS manager location 

>%windir%\system32\inetsrv\InetMgr.exe

### Winodws Terminal Location

>D:\Users\admin\AppData\Local\Microsoft\WindowsApps\Microsoft.WindowsTerminal_8wekyb3d8bbwe

### Powershell Shortcut Location

>C:\Users\admin\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Windows PowerShell
```bash
B:\MyPrograms\PowerShell\7\pwsh -f "B:\Lib\Proj\PS\Default.ps1" -wd "B:\Temp" -noexit
C:\Windows\SysWOW64\WindowsPowerShell\v1.0\powershell.exe -noexit (. B:\Lib\Proj\PS\Default.ps1)
```
>Path = C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Windows PowerShell

### For terminal
```bash

B:\MyPrograms\PowerShell\7\pwsh -f "B:\Lib\Proj\PS\Default.ps1" -wd "B:\Temp" -noexit

```


## Autostart jupyter

```bash
 Start-Process 'jupyter-notebook.exe' '--no-browser --notebook-dir=B:\Lib\Jup\ ' -WindowStyle Hidden
```
## CSharp


### Create array

```bash

$testlist = [System.Collections.ArrayList]::new()
$testlist.Add('Name')

foreach($n in $testList){
	rm $n -force
}

```

## Processes

### Stop process


```pwsh
Stop-Process -Name ApplicationName

Stop-process -Name Chrome
Stop-process -Id processId
```
### Start Process
```bash
 Start-Process 'jupyter-notebook.exe' '--no-browser --notebook-dir=B:\Lib\Jup\ ' -WindowStyle Hidden
```
