# PowerCli_Filter_Example

#### Filter Example

* Complete inventory of VMs

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


* Filter the VMs with state `Poweredon`

```
PS /home/netops/powershell> (Get-VM).where{$_.PowerState -eq 'PoweredOn'}

Name                 PowerState Num CPUs MemoryGB
----                 ---------- -------- --------
Prox2                PoweredOn  4        12.000
gitbucket            PoweredOn  2        2.000
openvpn              PoweredOn  2        2.000
Etherpad             PoweredOn  1        3.000
Homecall             PoweredOn  1        1.000

```

* Filter the VMs with Guest OS `Ubuntu`

```
PS /home/netops/powershell> (Get-VM).where{$_.Guest -match 'ubuntu'}

Name                 PowerState Num CPUs MemoryGB
----                 ---------- -------- --------
gitbucket            PoweredOn  2        2.000
openvpn              PoweredOn  2        2.000
Homecall             PoweredOn  1        1.000

```
