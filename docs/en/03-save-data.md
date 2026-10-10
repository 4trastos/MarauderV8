# How to save data from the Marauder v8 menu

[Return to índex](../README.md)

---

Once the formatted card is inserted into the Marauder, the interface will automatically enable SD storage:

* **Capturing packets (Handshakes / PCAP):**
  - Go to **Sniffer** > **EAPOL** (or **PKE / Handshake**).
  - When you press **Start**, the `.pcap` file will be written directly to the `/pcap` folder on the SD card.
  - You can then remove the SD card, insert it into your Ubuntu machine, and open the `.pcap` files with **Wireshark** or analyze them using **aircrack-ng**.

* **Saving scan logs:**
  - When performing a network scan (**Scan** > **AP**) or client scan (**Scan** > **STAs**), the option to save results will create `.txt` files in the `/logs` folder.
 
* **Using dictionaries (Wordlists):**
  - Copy your password text files (e.g., a custom list or excerpts from *rockyou.txt*) into the `/wordlists` folder.
  - When running authentication attacks or tests that require a dictionary, the Marauder will be able to read the files directly from that folder.
 
## Checking SD card status on the Marauder

To confirm that the device recognizes the card as active storage:

  - Go to **Device** (or **Settings**).
  - Select **SD Status** / **SD Info**.
  - It should display the card size and free space, and confirm that the FAT32 file system is correctly mounted.



