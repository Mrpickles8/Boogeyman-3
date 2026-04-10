# Boogeyman-3

## Objective
Investigate a full intrusion chain in Elastic SIEM — from HTA phishing delivery
through C2, UAC bypass, Mimikatz credential dumping, WinRM lateral movement,
DCSync, and ransomware deployment.

### Skills Learned
- Elastic / Kibana KQL queries across two compromised machines
- HTA initial access via mshta.exe (PID 6392)
- Payload staging via xcopy.exe and rundll32.exe execution
- Scheduled task persistence detection
- UAC bypass via fodhelper.exe
- Mimikatz credential dumping (sekurlsa::logonpasswords)
- Lateral movement via WinRM (wsmprovhost.exe as parent)
- DCSync attack identification
- Ransomware delivery URL extraction

### Tools Used
- Elastic SIEM / Kibana (KQL)
- Sysmon logs
- MITRE ATT&CK framework

## Steps
HTA file from email attachment executed via mshta.exe. xcopy.exe staged
`review.dat` to Temp. rundll32.exe executed the DLL, established C2 to
`165.232.170.151:80`, created scheduled task "Review". fodhelper.exe performed
UAC bypass. Mimikatz downloaded from GitHub dumped `itadmin` credentials.
Lateral movement to WKSTN-1327 via WinRM — second dump yielded `administrator`
hash. DCSync on DC01 revealed `backupda` account. Ransomware pulled from
`hxxp://ff.sillytechninja[.]io/ransomboogey.exe`.

*Ref 1: Kibana KQL — mshta.exe execution chain from HTA email attachment*
*Ref 2: Mimikatz sekurlsa log and DCSync entries in Elastic*

