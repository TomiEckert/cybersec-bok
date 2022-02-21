---
title: Ethical Hacker
author: TomiEckert
date: 2022. 02. 20.
---

# Ethical Hacker

## Contents

## Basic hacking and Pentesting process

### What are the process steps of every pentest in general?

Based on [Lockheed Martin's Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html) the general steps of an attack are the following:
  - Reconnaissance (Information gathering)
  - Weaponization (Payload creation)
  - Delivery (Getting the payload into target network)
  - Exploitation (Running code on exploited target machine)
  - Installation (Installing malware/backdoor on target)
  - Command and Control (Remote controlled connection to target)
  - Actions on objectives (Accomplishing original goals)

> Check [Cyber kill chain doc](cyber-killchain.md) for more info.

General pentest process matches the cyber kill chain until exploitation (or whatever is stated in the contract). With the steps being:
  - Intel gathering (General reconnaissance, osint, social engineering, etc.)
  - Footprint (Mapping out target network, IT systems: IP ranges, ports, OSes, servers, etc.)
  - Vulnerability analysis (In-depth analysis of services and applications to find known vulnerabilities)
  - Exploitation (Entering the target through vulns, this step might be destructive, so often not executed in a pentest process)

### What are the minimal requirements for a good pentest contract and pentest report?

Requirements for a basic pentest contract are the following:
  - Indemnification clause signed by client, that allows for testing and addresses liability. Testers can NOT be liable for any damages caused by testing.
  - Confidentiality agreement signed by all testers.
  - Info about the scope, and tested systems and evironments.
  - Test origin, test times/period of testing. So client can distinguish testing from real attacks.
  - Escalation procedure in case of incidents/emergencies.

Requirements for a basic pentest report:
  - Must contain the goals and scope of the pentest.
  - Explanation of the approach.
  - Test results with findings and explanations.
  - Overall conclusion.
  - Advice on how to reinforce/fix the systems.

## Law, ethics, and responsible disclosure

### Cyber crime examples

#### Opposition journalist gets spyware on his phone

[Link to an article](https://www.theguardian.com/news/2021/sep/21/hungary-journalist-daniel-nemeth-phones-infected-with-nso-pegasus-spyware)
The journalist is known locally for his work on reporting on hidden luxouries of Hungarian politicians. While he was investigating the prime minister's childhood friend who amassed ~1.2 billion euros net worth from buying up state owned companies, services, etc, his devices were attacked with NSO group's Pegasus spyware. As always with govermental crimes, no penalties or sentences, not too surprising in Hungary.

#### Pepsi Hungary hack

[Link to an article](https://www.databreaches.net/pepsi-hungary-hacked-50000-user-credentials-leaked/)
Turkish hacker found a horribly configured website on `pepsi.hu` and they managed to aquire about 50 000 personal details: names, emails, passwords, which were stored unencrypted. This was a surprising one, because Pepsi is a massive company, and one can expect at least solid basic security all around, but then again, this page was belonging to the Hungarian arm of the company. No penalties what so ever, as Turkey doesn't extradite its own nationals, and since the guy didn't do any damage to Turkish property/companies, no penalties apply in that case.

### High risk vuln procedure

Most probabaly I would first ask a teacher about this, just to make sure (experience helps), and prepare if and how I would need to protect myself legally, after that, look up if the company has a CVD policy, if yes, just follow protocol. If not, then working with the teacher, university and the company to sort it out. Or send Mossad a message about it and ask how much they would offer, just in case.

## Footprinting

### Why footprinting?

Footprinting gives a baseline of information we can base our tests on. Using osint, passive and active reconnaissance we can find useful information about the target (emails, names, servers, providers, etc.). Without footprinting, it is basically not possible to pentest, as there is no information to start with.

### Footprinting techniques



### Examples



### nu.nl 10 years ago

[Link to old nu.nl](https://web.archive.org/web/20120220184606/http://www.nu.nl/)

### robots.txt on Pentagon and Whitehouse sites

Pentagon disabled sites from [robots.txt](https://www.defense.gov/robots.txt):

```
https://www.defense.gov/*Print.aspx
https://www.defense.gov/*.axd$
https://www.defense.gov/*.exe$
https://www.defense.gov/bin/
https://www.defense.gov/Bin/
https://www.defense.gov/*.bin$
https://www.defense.gov/*.dll$
https://www.defense.gov/*.ssi$
https://www.defense.gov/Error/
https://www.defense.gov/Controls/
https://www.defense.gov/controls/
https://www.defense.gov/Utility/
https://www.defense.gov/install/
https://www.defense.gov/Admin/
https://www.defense.gov/App_Browser/
https://www.defense.gov/App_Code/
https://www.defense.gov/App_Data/
https://www.defense.gov/App_GlobalResources/
https://www.defense.gov/Components/
https://www.defense.gov/Config/
https://www.defense.gov/Documentation/
https://www.defense.gov/Install/
https://www.defense.gov/Providers/
```

Whitehouse disabled sites from [robots.txt](https://www.defense.gov/robots.txt):

```
https://www.whitehouse.gov/wp-admin/
```

tl;dr: whitehouse.gov is a wordpress site.

### Tooling tests

#### Find path to fontys.nl and fhict.nl



#### DNS and email servers used by fontys.nl and fhict.nl



#### Find fhict.nl ip addresses



#### Run theharvester on fontys.nl



