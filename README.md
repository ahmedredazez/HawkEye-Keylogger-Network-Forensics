# HawkEye Keylogger: Network Forensics Investigation

Investigation of a packet capture from the CyberDefenders **HawkEye** blue team lab. The goal was to rebuild the full attack chain of a keylogger infection and identify how stolen data left the network.

This is a lab exercise (CyberDefenders, SOC Analyst Tier 2, Level 6, Network Forensics, difficulty Medium). All 24 lab questions were answered.

## Scenario

The accounting department flagged suspicious activity after an employee opened an email attachment disguised as a proforma invoice. The finance team's traffic (`stealer.pcap`) was captured and handed to the SOC. The investigation reconstructs the delivery of a malicious executable, identifies the victim host and the attacker infrastructure, and follows the periodic exfiltration of keylogged data.

## Key findings

- **Victim host:** Beijing-5cd1-PC (10.4.10.132), Windows 7.
- **Delivery:** a malicious executable (`tkraw_Protected99.exe`) downloaded from `proforma-invoices.com` (217.182.138.150, hosted in France).
- **Malware:** HawkEye Keylogger, Reborn v9. Confirmed from decoded exfiltration email content and VirusTotal detections.
- **Exfiltration:** SMTP to a GoDaddy-hosted mail server (secureserver.net, Exim 4.91, United States).
- **Stolen data:** credentials for several websites, recovered by decoding Base64 content in the exfiltration emails.
- **Beaconing:** data was sent on a fixed 10-minute cycle.

## Analysis covered

- Network traffic analysis with Wireshark and Brim
- Identifying the compromised host and internal infrastructure
- DNS and HTTP traffic analysis
- Investigating malicious file delivery
- Malware identification with VirusTotal
- Tracking C2 and external infrastructure (MaxMind GeoIP, AbuseIPDB)
- Analyzing SMTP-based data exfiltration
- Decoding Base64-encoded credentials and email content
- Extracting Indicators of Compromise (IOCs)

## MITRE ATT&CK tactics observed

Initial Access, Execution, Stealth, Credential Access, Discovery, Collection, Command and Control, Exfiltration.

## Tools

Wireshark, Brim, Apackets, MaxMind GeoIP, VirusTotal, AbuseIPDB.

## Report

The full step-by-step report (26 pages) is in this repository: `HawkEye-Keylogger-Investigation-Report.pdf`. Any credentials shown in the report are sample data from the CyberDefenders lab capture, not real accounts.

## Author

Ahmed Reda Ali Azez, Junior SOC Analyst trainee.
