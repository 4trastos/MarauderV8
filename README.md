# MarauderV8
NIST tutorial and technical evaluation

## Index:

- [Install or Update Firmware](#Install-or-Update-Firmware)
- [Recommended folder structure](#Recommended-folder-structure)
- [How to save data from the Marauder v8 menu](#How-to-save-data-from-the-Marauder-v8-menu)


# Install or Update Firmware

To update the ESP32 Marauder v8 using the microSD card on Ubuntu, the fastest and simplest method is Auto-Update (updating directly from the Marauder menu).
## Step 1: Prepare the microSD card on Ubuntu
  - Insert the microSD card into your Ubuntu computer.
  - Format the card to **FAT32** if it isn't already (you can use the *Disks / GNOME Disks* tool or `mkfs.fat -F 32`).
  - Unzip the downloaded `.zip` file ![Download v1.12.1](update/http_index.png). Look inside for the firmware binary file; it is usually named `esp32_marauder_v8.bin` (or something similar with a `.bin` extension).
  - **Rename the `.bin` file:** Change its name to `update.bin` (it is crucial that it is named exactly this, in lowercase).
  - Copy the `update.bin` file to the **root** of the microSD card (do not place it inside any folder).
  - Safely unmount and eject the card from Ubuntu.

## Step 2: Flash from the Marauder v8

  - **Turn off** the Marauder v8.
  - Insert the microSD card into the Marauder's slot.
  - Turn on the device.
  - On the touchscreen or interface, navigate to the **Device** (or *Settings*) menu.
  - Select the **Reboot [Update]** or **SD ​​Update** option.
  - The device will detect the `update.bin` file, automatically begin the flashing process, and display the progress on the screen.
  - Once complete, the Marauder will reboot running the updated version. --- 

# Recommended folder structure

Connect the microSD card to your Ubuntu machine and create the following folders at the root of the card (all in lowercase):

```text
/ (microSD root)
├── pcap/       -> Stores captured WiFi packets (e.g., WPA/EAPOL handshakes)
├── wordlists/  -> Stores password dictionaries (.txt) for brute-force attacks
├── logs/       -> Stores text logs of scans
└── update.bin  -> (Optional) Firmware for future updates

```

# How to save data from the Marauder v8 menu

Once the formatted card is inserted into the Marauder, the interface will automatically enable SD storage:

* **Capturing packets (Handshakes / PCAP):**
  - Go to **Sniffer** > **EAPOL** (or **PKE / Handshake**).
  - When you press **Start**, the `.pcap` file will be written directly to the `/pcap` folder on the SD card.
  - You can then remove the SD card, insert it into your Ubuntu machine, and open the `.pcap` files with **Wireshark** or analyze them using **aircrack-ng**. * **Saving scan logs:**
  - When performing a network scan (**Scan** > **AP**) or client scan (**Scan** > **STAs**), the option to save results will create `.txt` files in the `/logs` folder.
 
* **Using dictionaries (Wordlists):**
  - Copy your password text files (e.g., a custom list or excerpts from *rockyou.txt*) into the `/wordlists` folder.
  - When running authentication attacks or tests that require a dictionary, the Marauder will be able to read the files directly from that folder.
 
## Checking SD card status on the Marauder

To confirm that the device recognizes the card as active storage:

  - Go to **Device** (or **Settings**).
  - Select **SD ​​Status** / **SD ​​Info**.
  - It should display the card size and free space, and confirm that the FAT32 file system is correctly mounted.
