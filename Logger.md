# PowerCli_logging_Example

#### SAMPLE Script

```
PS /home/netops> cat ./test2.ps1
#try{your_command *>&1}catch{$_}
$out = try
{
  get-vm -Name penvpn -ErrorAction Stop
  #get-vm -Name penvpn
  get-vm -Name openvpn
}
catch
{
  $_
}

echo $out
```

#### Error Logging Example

```
./test2.ps1 5>&1 4>&1 3>&1 2>&1 | Out-file log.txt

```

```
PS /home/netops> cat ./log.txt

Get-VM: /home/netops/test2.ps1:4
Line |
   4 |    get-vm -Name penvpn -ErrorAction Stop
     |    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | 03/19/2023 09:52:04 Get-VM  VM with name 'penvpn' was not found using the specified filter(s).

```
