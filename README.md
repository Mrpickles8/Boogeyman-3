# Boogeyman-3

## Objective
Investigate an advanced intrusion scenario involving a sophisticated threat actor using multiple persistence mechanisms, defense evasion techniques, and data exfiltration. The goal was to identify all stages of the attack and document the complete TTPs used.

### Skills Learned
- Advanced persistence mechanism detection (scheduled tasks, registry keys, WMI subscriptions)
- Defense evasion identification (log clearing, process injection)
- Data exfiltration detection via network log analysis
- Multi-stage attack investigation methodology
- Advanced MITRE ATT&CK TTP mapping

### Tools Used
- Sysmon (comprehensive event coverage)
- Windows Security and System Event Logs
- Wireshark for exfiltration traffic analysis
- Timeline Explorer
- MITRE ATT&CK framework

## Steps
Investigation covered multiple persistence mechanisms by querying Sysmon for scheduled task creation (Event ID 1 - schtasks.exe), registry modification events (Event ID 13), and WMI subscription creation. Defense evasion was confirmed through Security log evidence of event log clearing (Event ID 1102) and process injection indicators. Exfiltration was identified by analyzing outbound traffic volume spikes in Wireshark correlated with sensitive file access events in Sysmon. All identified techniques were mapped to MITRE ATT&CK across Defense Evasion (T1070), Persistence (T1053, T1547, T1546), and Exfiltration (T1041) tactics.

*Ref 1: Sysmon log showing WMI subscription creation for persistence*
*Ref 2: Wireshark traffic analysis confirming data exfiltration over HTTPS*
