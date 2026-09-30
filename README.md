# 🔎 Wireshark Malware Traffic Analysis

## PCAP Investigation | Network Forensics | Blue Team Lab

This project documents a hands-on network traffic investigation performed
with Wireshark as part of my Cybersecurity Specialist training.

The objective was to investigate a PCAP capture from a compromised Windows
environment and identify the infected host, user account, malware delivery
infrastructure, malware family and indicators of compromise (IOCs).

---

## 🎯 Investigation Objectives

The investigation focused on answering the following questions:

- Which Windows host was compromised?
- What IP and MAC address belonged to the infected machine?
- Which user account was active on the compromised system?
- Which external IP was involved in the malware delivery?
- What executable was associated with the infection?
- What was its SHA-256 hash?
- Which malware family was detected?
- How was the malware delivered?
- Where was the malicious infrastructure hosted?

---

## 🛠️ Tools & Environment

- Wireshark
- Kali Linux
- PCAP network capture
- SHA-256 hashing
- GeoIP analysis
- Network protocol analysis

The analysis was performed in an isolated lab environment.

---

## 🔍 Investigation

### 1. Identifying the Compromised Host

Analysis of the captured traffic identified the infected Windows machine:

| Indicator | Value |
|---|---|
| Hostname | `BANGKOK-8AC2-PC` |
| IP Address | `10.0.76.109` |
| MAC Address | `78:2b:cb:d4:a5:fe` |
| Domain | `phenomenoc.com` |
| User | `edris.knight` |

Packet inspection allowed the host information to be identified directly
from the captured network traffic.

---

### 2. Identifying the Malware Delivery Infrastructure

Further analysis revealed communication with the following external host:

`37.46.135.170`

This IP address was associated with the malware delivery observed in the
capture.

Interestingly, the HTTP traffic communicated directly with the IP address
rather than using a domain name.

---

### 3. Malicious Executable

The executable associated with the infection was identified and its
SHA-256 hash was obtained:

`39be5610259ffade85599720ee0af31187788a00791f1e4cb0cd05ef00105eda`

Cryptographic hashes are useful Indicators of Compromise (IOCs) because
they can be used to identify and correlate suspicious files during
security investigations.

---

### 4. Malware Identification

Based on the alerts and captured traffic, the malware was identified as:

**KPOT Stealer**

The infection chain indicated delivery through:

**RIG Exploit Kit (RIG EK)**

KPOT is an information-stealing malware, making this traffic relevant to
credential and data-theft investigations.

---

### 5. Geographic Analysis

GeoIP information associated with the malicious infrastructure indicated:

| Attribute | Result |
|---|---|
| Country | Russia |
| ASN | 29182 |
| Organization | JSC IOT |
| City | Not identified by the GeoIP database used |

---

## 🚨 Indicators of Compromise (IOCs)

| Type | Indicator |
|---|---|
| Infected Host | `BANGKOK-8AC2-PC` |
| Internal IP | `10.0.76.109` |
| MAC Address | `78:2b:cb:d4:a5:fe` |
| User | `edris.knight` |
| Malicious IP | `37.46.135.170` |
| Malware | `KPOT Stealer` |
| Delivery | `RIG Exploit Kit` |
| SHA-256 | `39be5610259ffade85599720ee0af31187788a00791f1e4cb0cd05ef00105eda` |

---

## 🧠 What I Learned

This investigation helped me understand how network traffic can be used
to reconstruct a security incident.

Instead of looking at packets individually, I learned to correlate
different pieces of information from the capture to identify:

- the compromised endpoint;
- the affected user;
- malicious external infrastructure;
- malware delivery activity;
- file-based indicators;
- and Indicators of Compromise.

The lab also demonstrated how Wireshark can support network forensics and
incident investigation in a Blue Team/SOC environment.

---

## 📸 Investigation Evidence

Screenshots from the investigation are being organized in the
`screenshots/` directory.

They document the packet analysis used to identify the compromised host,
malicious infrastructure and malware activity.

---

## 📚 Training Context

This lab was completed as part of my **Cybersecurity Specialist (CET)**
training at **CINEL – Lisbon**, during the unit focused on detecting and
analyzing vulnerabilities.

---

## 👩‍💻 About Me

I am a cybersecurity student based in Portugal, building hands-on
experience in:

- SOC / Blue Team fundamentals
- Network Security
- Network Traffic Analysis
- Linux
- Windows Server
- SIEM
- Vulnerability Management

This repository is part of my cybersecurity portfolio documenting my
practical learning journey.
