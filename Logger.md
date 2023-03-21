# PowerCli_logging_Example

#### SAMPLE Script

```
$out = try
{
  get-vm -Name penvpn -ErrorAction Stop
  #get-vm -Name penvpn
}
catch
{
  write-error $_.Exception.Message
  $_ |select -expandproperty invocationinfo
}

echo $out
```

#### Error Logging Example


![](docs/redirection_codes.png)

```
./test2.ps1
Write-Error: 03/21/2023 21:05:17	Get-VM		VM with name 'penvpn' was not found using the specified filter(s).

MyCommand             : Get-VM
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 6
OffsetInLine          : 3
HistoryId             : 93
ScriptName            : /home/netops/test2.ps1
Line                  :   get-vm -Name penvpn -ErrorAction Stop

PositionMessage       : At /home/netops/test2.ps1:6 char:3
                        +   get-vm -Name penvpn -ErrorAction Stop
                        +   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
PSScriptRoot          : /home/netops
PSCommandPath         : /home/netops/test2.ps1
InvocationName        : get-vm
PipelineLength        : 0
PipelinePosition      : 0
ExpectingInput        : False
CommandOrigin         : Internal
DisplayScriptPosition :
```
