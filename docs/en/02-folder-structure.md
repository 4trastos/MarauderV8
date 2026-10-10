# Recommended folder structure

[Return to índex](../README.md)

---

Connect the microSD card to your Ubuntu machine and create the following folders at the root of the card (all in lowercase):

```text
/ (microSD root)
├── pcap/       -> Stores captured WiFi packets (e.g., WPA/EAPOL handshakes)
├── wordlists/  -> Stores password dictionaries (.txt) for brute-force attacks
├── logs/       -> Stores text logs of scans
└── update.bin  -> (Optional) Firmware for future updates
```
