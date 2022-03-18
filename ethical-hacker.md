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

I ran the command `mtr fhict.nl -i 5`, which produced the following output:

```
Host                                                                      Loss%   Snt   Last   Avg  Best  Wrst StDev
1. 92-109-132-1.cable.dynamic.v4.ziggo.nl                                  0.0%    29   11.2  11.0   5.3  14.5   1.7
2.     _gateway
3.  2. 92-109-132-1.cable.dynamic.v4.ziggo.nl                              0.0%    29   11.2  12.7   9.7  26.4   3.4
4.  3. 212.142.55.17                                                       0.0%    29   13.9  12.8   9.7  22.2   2.6
5.  4. asd-tr0021-cr101-be111-2.core.as33915.net                           0.0%    29   19.0  15.7  10.8  20.2   2.2
6.  5. nl-ams04a-ri3-ae51-0.core.as9143.net                                0.0%    29   15.6  18.3  13.3  25.7   3.4
7.  6. ae78-0.asd001b-jnx-01.surf.net                                      0.0%    29   21.8  17.1  11.3  31.5   3.9
8.  7. ae24.ut015b-jnx-01.surf.net                                         0.0%    29   18.0  18.3  13.9  31.9   3.5
9.  8. ae21.ut001a-jnx-01.surf.net                                         0.0%    29   18.3  18.1  11.6  23.6   2.4
10.  9. ae20.ehv001b-jnx-01.surf.net                                       0.0%    29   17.5  17.8  11.6  24.9   2.9
11. 10. e4-0-2-0.ehv010a-jnx-01.surf.net                                   0.0%    29   17.5  17.8  15.2  23.9   2.0
12. 11. fontys-router.customer.surf.net                                   28.6%    29   19.4  17.6  14.5  24.8   2.4
13. 12. (waiting for reply)
14. 13. (waiting for reply)
15. 14. 145.85.4.1                                                         0.0%    29   46.5  34.4  16.1  66.8  13.7
16. 15. (waiting for reply)
```
The option `-i 5`, helped with the address `fontys-router.customer.surf.net`, as with 1 second interval, the packet losses are around 80%. I think this might be some kind of firewall, security config setting.

The same command for `fontys.nl`, didn't yield the results I expected:

```
Host                                                                      Loss%   Snt   Last   Avg  Best  Wrst StDev
1. 92-109-132-1.cable.dynamic.v4.ziggo.nl                                  0.0%    83   12.0  11.8   3.8  18.8   2.2
2.     _gateway
3.  2. 92-109-132-1.cable.dynamic.v4.ziggo.nl                              0.0%    83   17.3  12.6   8.8  24.8   2.7
4.  3. 212.142.55.17                                                       0.0%    83   12.9  12.6   7.7  20.9   2.2
5.  4. asd-tr0021-cr101-be111-2.core.as33915.net                           0.0%    83   15.8  15.4  11.1  32.6   3.0
6.  5. nl-ams14a-ri1-ae51-0.core.as9143.net                                0.0%    83   15.8  18.6  12.7  36.9   5.1
7.  6. 99.83.114.20                                                        0.0%    83   20.9  16.0  10.8  27.7   3.4
8.  7. 52.93.112.201                                                       0.0%    83   14.3  16.8  12.5  28.0   3.1
9.  8. 54.239.114.147                                                      0.0%    83   22.9  17.4  10.6  39.2   5.2
10.  9. (waiting for reply)
```
Couldn't trace back to the target address, even though I used the `-i 5` option and waited forever, but no sufficient result.

#### DNS and email servers used by fontys.nl and fhict.nl

To find the servers I used [DNSdumpster](https://dnsdumpster.com/).

fontys.nl:

```
Namespace servers:      ns1.surfnet.nl, ns2.surfnet.nl
Fontys DNS server:      hermes.fontys.nl
Mail server:            fontys-nl.mail.protection.outlook.com
```

fhict.nl:
```
Namespace servers:      ns3.combell.net, ns4.combell.net
Mail server:            fhict-nl.mail.protection.outlook.com
```

#### Find fhict.nl ip addresses

I ran the command `theharvester -d fhict.nl -b sublist3r,threatminer,dnsdumpster -f output`, which scans sublist3r, threatminer and dnsdumpster for records on `fhict.nl`, and outputs the results to the files `output.xml` and `output.json`. After that I went through the file and manually selected the unique IPs as there weren't too many. If there were I probably would've wrote a script to automate it.

[fhict_addresses_output.json](fhict_addresses_output.json)

```
Unique IPs:

145.85.4.24
145.85.4.70
145.85.4.67
145.85.4.99
145.85.4.71
145.85.4.6
145.85.4.24
145.85.4.20
217.19.237.54       canvas.fhict.nl
20.82.15.177        flowerpower.fhict.nl
```


#### Run theharvester on fontys.nl

I ran the command `theharvester -d fontys.nl -b sublist3r,threatminer,dnsdumpster -f output`, and the output is in the following file:

[fontys_harvester_output.json](fontys_harvester_output.json)


