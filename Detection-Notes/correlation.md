# Attack to Detection Correlation

Attack Source:
192.168.56.4 (Kali Linux)

Target:
192.168.56.3 (Windows 11)

Detection Tools:
- Windows Event Viewer
- Wireshark (tcp.flags.syn == 1)

Conclusion:
The SYN scan generated detectable events
at both system log and packet level.
