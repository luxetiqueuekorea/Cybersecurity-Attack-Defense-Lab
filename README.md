# 🛡 Cybersecurity Attack & Defense Home Lab

## 📌 Project Overview

This project demonstrates the creation of a practical cyber attack and defense lab using:

- VirtualBox
- Kali Linux
- Windows 11
- Nmap
- Windows Event Viewer
- Wireshark

The objective was to simulate real-world reconnaissance activity and analyze how defensive mechanisms detect and log the attack.

---

## 🏗 Lab Architecture

Attacker Machine:
- Kali Linux
- IP: 192.168.56.4

Target Machine:
- Windows 11
- IP: 192.168.56.3

Network Configuration:
- Host-Only Adapter (VirtualBox)
- Both machines on the same isolated network

---

## ⚔ Attack Performed

### SYN Scan using Nmap

Command used:

```
nmap -sS -sV -Pn 192.168.56.3
```

Explanation:
- `-sS` → TCP SYN (Stealth) scan
- `-sV` → Service version detection
- `-Pn` → Skip host discovery

Purpose:
To identify open ports and analyze firewall behavior.

---

## 🛡 Firewall Behavior Observed

A basic scan was executed:

```
nmap -Pn 192.168.56.3
```

Result:
- All 1000 ports were marked as filtered
- Indicates Windows Firewall actively blocked unsolicited connections

This confirms defensive filtering was functioning properly.

---

## 🔎 Log-Based Detection (Windows Event Viewer)

Windows Filtering Platform auditing was enabled.

Observed Event IDs:
- 5156 (Connection allowed)
- 5157 (Connection blocked)

The logs confirmed:
- Multiple connection attempts
- Source IP: 192.168.56.4 (Kali)
- Target IP: 192.168.56.3 (Windows)

This demonstrates successful detection of reconnaissance activity using native Windows security logging.

---

## 📡 Packet-Level Analysis (Wireshark)

Wireshark was used to capture live traffic on the Windows VM.

Filter applied:

```
tcp.flags.syn == 1
```

Observation:
- Multiple TCP SYN packets from 192.168.56.4
- Targeting various ports on 192.168.56.3
- Behavior consistent with Nmap SYN scan

This confirms network-level visibility of the attack.

---

## 📸 Screenshots

1. VM Running
2. Network Configuration
3. Kali IP Address
4. Windows IP Address
5. Nmap SYN Scan
6. Firewall Filtered Ports
7. Windows Event Log Detection
8. Wireshark SYN Packet Capture

All screenshots are available in the `Screenshots/` folder.

---

## 🧠 Key Learnings

- How TCP SYN scans work
- How firewalls filter inbound traffic
- How to enable Windows security auditing
- How to correlate attack activity with Event IDs
- How to capture and analyze packet-level data
- How to build and troubleshoot a virtual lab environment

---

## 🎯 Skills Demonstrated

- Virtualization (VirtualBox)
- Network configuration
- Penetration testing basics
- Security log analysis
- Packet inspection (Wireshark)
- Attack-to-detection correlation

---

## ⚠ Disclaimer

All activities were conducted in a controlled virtual lab environment for educational purposes only.
No real systems were targeted.
