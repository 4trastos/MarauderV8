# MarauderV8
NIST tutorial and technical evaluation / Tutorial NIST y evaluación técnica

## Índice:
- [Instalar o Actualizar el Firmware (Castellano)](#instalar-o-actualizar-el-firmware-castellano)
- [Estructura de carpetas recomendada (Castellano)](#estructura-de-carpetas-recomendada-castellano)
- [Cómo guardar datos desde el menú del Marauder v8 (Castellano)](#cómo-guardar-datos-desde-el-menú-del-marauder-v8-castellano)
- [Wardrive Tracker](#Wardrive-Tracker)

---

# 🇪🇸 CASTELLANO

# Instalar o Actualizar el Firmware

Para actualizar el ESP32 Marauder v8 utilizando la tarjeta microSD en Ubuntu, el método más rápido y sencillo es la Auto-Actualización (actualizar directamente desde el menú del Marauder).

## Paso 1: Preparar la tarjeta microSD en Ubuntu
  - Introduce la tarjeta microSD en tu ordenador con Ubuntu.
  - Formatea la tarjeta en **FAT32** si no lo está ya (puedes usar la herramienta *Discos / GNOME Disks* o el comando `mkfs.fat -F 32`).
  - Descomprime el archivo `.zip` descargado ![Descargar v1.12.1](https://github.com/4trastos/MarauderV8/blob/main/update/V8flash.zip). Busca en su interior el archivo binario del firmware; normalmente se llama `esp32_marauder_v8.bin` (o un nombre similar con extensión `.bin`).
  - **Renombra el archivo `.bin`:** Cambia su nombre a `update.bin` (es fundamental que se llame exactamente así, en minúsculas).
  - Copia el archivo `update.bin` en la **raíz** de la tarjeta microSD (no lo metas dentro de ninguna carpeta).
  - Desmonta y expulsa la tarjeta de forma segura desde Ubuntu.

## Paso 2: Flashear desde el Marauder v8

  - **Apaga** el Marauder v8.
  - Introduce la tarjeta microSD en la ranura del Marauder.
  - Enciende el dispositivo.
  - En la pantalla táctil o interfaz, navega hasta el menú **Device** (o *Settings*).
  - Selecciona la opción **Reboot [Update]** o **SD Update**.
  - El dispositivo detectará el archivo `update.bin`, iniciará automáticamente el proceso de flasheo y mostrará el progreso en la pantalla.
  - Una vez completado, el Marauder se reiniciará ejecutando la versión actualizada.

--- 

# Estructura de carpetas recomendada

Conecta la tarjeta microSD a tu máquina Ubuntu y crea las siguientes carpetas en la raíz de la tarjeta (todas en minúsculas):

```text
/ (raíz de la microSD)
├── pcap/       -> Almacena los paquetes WiFi capturados (ej. handshakes WPA/EAPOL)
├── wordlists/  -> Almacena diccionarios de contraseñas (.txt) para ataques de fuerza bruta
├── logs/       -> Almacena registros de texto de los escaneos
└── update.bin  -> (Opcional) Firmware para futuras actualizaciones
```

# Cómo guardar datos desde el menú del Marauder v8

Una vez introducida la tarjeta formateada en el Marauder, la interfaz habilitará automáticamente el almacenamiento SD:

* **Captura de paquetes (Handshakes / PCAP):**
  - Ve a **Sniffer** > **EAPOL** (o **PKE / Handshake**).
  - Al pulsar **Start**, el archivo `.pcap` se escribirá directamente en la carpeta `/pcap` de la tarjeta SD.
  - Después puedes extraer la tarjeta SD, introducirla en tu máquina Ubuntu y abrir los archivos `.pcap` con **Wireshark** o analizarlos usando **aircrack-ng**.

* **Guardar logs de escaneo:**
  - Al realizar un escaneo de redes (**Scan** > **AP**) o de clientes (**Scan** > **STAs**), la opción de guardar resultados creará archivos `.txt` en la carpeta `/logs`.
 
* **Uso de diccionarios (Wordlists):**
  - Copia tus archivos de texto con contraseñas (por ejemplo, una lista personalizada o fragmentos de *rockyou.txt*) en la carpeta `/wordlists`.
  - Cuando ejecutes ataques de autenticación o pruebas que requieran un diccionario, el Marauder podrá leer los archivos directamente desde esa carpeta.
 
## Comprobación del estado de la tarjeta SD en el Marauder

Para confirmar que el dispositivo reconoce la tarjeta como almacenamiento activo:

  - Ve a **Device** (o **Settings**).
  - Selecciona **SD Status** / **SD Info**.
  - Debería mostrar el tamaño de la tarjeta, el espacio libre y confirmar que el sistema de archivos FAT32 está correctamente montado.

# Wardrive Tracker

Geolocaliza redes WiFi y dispositivos Bluetooth a partir de un PCAP o de un log wardrive (WigleWifi CSV).

---

## Index:
- [Install or Update Firmware (English)](#install-or-update-firmware-english)
- [Recommended folder structure (English)](#recommended-folder-structure-english)
- [How to save data from the Marauder v8 menu (English)](#how-to-save-data-from-the-marauder-v8-menu-english)

# 🇬🇧 ENGLISH

# Install or Update Firmware

To update the ESP32 Marauder v8 using the microSD card on Ubuntu, the fastest and simplest method is Auto-Update (updating directly from the Marauder menu).

## Step 1: Prepare the microSD card on Ubuntu
  - Insert the microSD card into your Ubuntu computer.
  - Format the card to **FAT32** if it isn't already (you can use the *Disks / GNOME Disks* tool or `mkfs.fat -F 32`).
  - Unzip the downloaded `.zip` file ![Download v1.12.1](https://github.com/4trastos/MarauderV8/blob/main/update/V8flash.zip). Look inside for the firmware binary file; it is usually named `esp32_marauder_v8.bin` (or something similar with a `.bin` extension).
  - **Rename the `.bin` file:** Change its name to `update.bin` (it is crucial that it is named exactly this, in lowercase).
  - Copy the `update.bin` file to the **root** of the microSD card (do not place it inside any folder).
  - Safely unmount and eject the card from Ubuntu.

## Step 2: Flash from the Marauder v8

  - **Turn off** the Marauder v8.
  - Insert the microSD card into the Marauder's slot.
  - Turn on the device.
  - On the touchscreen or interface, navigate to the **Device** (or *Settings*) menu.
  - Select the **Reboot [Update]** or **SD Update** option.
  - The device will detect the `update.bin` file, automatically begin the flashing process, and display the progress on the screen.
  - Once complete, the Marauder will reboot running the updated version.

--- 

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

