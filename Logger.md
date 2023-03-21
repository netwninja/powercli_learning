# PowerCli_logging_Example

#### SAMPLE Script

```
$vm_name = Read-Host -Prompt 'Type VM Name'
$info = try
{
  write-host -ForegroundColor Yellow "Getting VM Inventory from ESXi host"
  write-host " "
  get-vm -Name $vm_name -ErrorAction Stop
  #get-vm -Name penvpn
}
catch
{
  write-error $_.Exception.Message
  $_ |select -expandproperty invocationinfo
}

echo $info
```

#### Error Logging Example


![](docs/redirection_codes.png)

### SAMPLE GET-VM OUTPUT

```
PS /home/netops/powershell> get-VM

Name                 PowerState Num CPUs MemoryGB
----                 ---------- -------- --------
Gitlab               PoweredOff 1        4.000
Rhel7-6              PoweredOff 1        4.000
Prox2                PoweredOn  4        12.000
pbolt                PoweredOff 2        2.000
gitbucket            PoweredOn  2        2.000
gitlab-server        PoweredOff 2        4.000
openvpn              PoweredOn  2        2.000
Win7-Enterprise      PoweredOff 1        1.000
Etherpad             PoweredOn  1        3.000
Homecall             PoweredOn  1        1.000
Web-0.72             PoweredOff 1        4.000

```
#### Error Catch and Log Print

```
PS /home/netops> ./test2.ps1
Type VM Name: openvm
Getting VM Inventory from ESXi host

Write-Error: 03/21/2023 22:13:03	Get-VM		VM with name 'openvm' was not found using the specified filter(s).

MyCommand             : Get-VM
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 6
OffsetInLine          : 3
HistoryId             : 3
ScriptName            : /home/netops/test2.ps1
Line                  :   get-vm -Name $vm_name -ErrorAction Stop

PositionMessage       : At /home/netops/test2.ps1:6 char:3
                        +   get-vm -Name $vm_name -ErrorAction Stop
                        +   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
PSScriptRoot          : /home/netops
PSCommandPath         : /home/netops/test2.ps1
InvocationName        : get-vm
PipelineLength        : 0
PipelinePosition      : 0
ExpectingInput        : False
CommandOrigin         : Internal
DisplayScriptPosition :

```
