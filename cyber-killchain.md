---
title: Cyber Kill Chain
author: TomiEckert
tags:
  - security
---

# Cyber Kill Chain

Steps:
  - Reconnaissance
  - Weaponization
  - Delivery
  - Exploitation
  - Installation
  - Command & Control (C2)
  - Actions on Objectives

## Reconnaissance

Harvesting email addresses, domains, job postings, conference information, etc.

The first task in any cyber attack is to gather information about the target. There are 2 stages of recon: passive and active.

Passive recon uses indirect methods:
  - `whois`
  - ARIS
  - [[google]]
  - [Shodan](shodan.io)
  - Job listings
  - Company website

Active recon involves some level of interaction with the organization:
  - [[nmap]]
  - Port scanning
  - Banner grabbing
  - Vulnerability scanning

> _Vuln scanning is very obvious, best to limit scope, or slow scan over a longer time._

### Protect against passive

To mitigate risks we can limit public info (job postings, LinkedIn, etc.), use social media in an acceptable way, modify/remove server error messages.

### Protect agains active

Disable unused ports/services, and/or deploy honeypots to find out what the attackers are after and who they are. Set up proper firewalls, block specific IPs/Tor/3rd party VPNs.

## Weaponization

Coupling exploit with backdoor into deliverable payload.

Create a weapon to attack the target based on the information gathered from the recon phase. This might include the following tools:
  - [Cain and Abel](https://sectools.org/tool/cain) (Windows password recovery tool)
  - [SqlMap](https://sqlmap.org) (Automatic SQL injector tool)
  - [AirCrack](https://www.aircrack-ng.org) (WiFi network security testing tool)
  - [Maltego](https://www.maltego.com) (OSINT dataminer tool)
  - [Metasploit](https://www.metasploit.com) (Vulnerability tester tool)
  - [Exploit-DB](https://www.exploit-db.com) (CVE database)
  - [Veil Framework](https://github.com/Veil-Framework/Veil) (Metasploit payload generator)
  - [Social Engineering Toolkit](https://github.com/trustedsec/social-engineer-toolkit) (Social engineering pentesting tool)
  - [Wapiti](https://wapiti-scanner.github.io) (Website vulnerability scanner)
  - [Burp Suite](https://portswigger.net/burp) (Web app pentester tool)
  - [FatRat](https://github.com/screetsec/TheFatRat) (Malware creator tool)

### Prevention

Proper patch management, almost all successful attacks happen because of unpatched software or improper server configuration. Disabling Office macros, JS and browser plugins will also help greatly with security.

AVs, email security, multi-factor authentication, audit logging, etc. will also help decrease the chance of a successful attack.

## Delivery

Delivering weaponized bundle to the victim via email, web, USB, etc.

### Mitigiation

  - Websites: Web/DNS filtering, force TLS.
  - Social media: User awareness of phishing campains.
  - Email: DKIM, SPF.
  - USB: Disable USB on employee devices, no Admin rights for users.

## Exploitation

Exploiting a vulnerability to execute code on the victim's system.

Not much to do here in terms of prevention. Advanced anti virus software will sandbox the malware as soon as it's analyzed it. Once it is sandboxed it's (hopefully) contained and not infencting the rest of the network.

## Installation

Installing malware on the asset.

Offensive tools:
  - DLL hijacking
  - Meterpreter
  - Remote Access Tools (RATs)
  - Registry changes
  - PowerShell commands

Not much protection at this stage, but we can detect almost every unauthorized program on the system with UBA/EDR. Registry/syste process changes should cause an alert to go off.

## Command & Control (C2)

Command channel for remote manipulation of victim.

Basically at this stage the network is fucked. Network segmentation/micro segmentation can still save the day, as the attacker can be isolated. Firewalls might be able to block known C2 servers.

## Actions on Objectives

With 'Hands on Keyboard' access, intruders accomplish their original goals.

At this stage not much can be done. Data Leakage Prevention software and UBA will not detect simple tasks (eg: screenshotting a protected document). Zero thrust security model seems to be the all in one solution for preventing successful attacks on the network.
