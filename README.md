# MarauderV8
NIST tutorial and technical evaluation

## Index:

- [Install or Update Firmware](#Install-or-Update-Firmware)


## Install or Update Firmware

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



