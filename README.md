# MarauderV8
NIST tutorial and technical evaluation / Tutorial NIST y evaluación técnica

## Índice:
- [Instalar o Actualizar el Firmware (Castellano)](#instalar-o-actualizar-el-firmware)
- [Estructura de carpetas recomendada (Castellano)](#estructura-de-carpetas-recomendada)
- [Cómo guardar datos desde el menú del Marauder v8 (Castellano)](#cómo-guardar-datos-desde-el-menú-del-marauder-v8)
- [📶 Wifi Captura de paquetes Pcap](#-wifi-captura-de-paquetes-pcap)
- [¿Cómo saber si tu .pcap sirve? (El Handshake)](#cómo-saber-si-tu-pcap-sirve-el-handshake)
- [El Diccionario (Wordlist)](#el-diccionario-wordlist)
- [Lanzar el ataque de comprobación con Aircrack-ng](#lanzar-el-ataque-de-comprobación-con-aircrack-ng)
- [📡 Wardrive Tracker](#-wardrive-tracker)

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

## Comprobación del estado de la tarjeta SD en el Marauder

Para confirmar que el dispositivo reconoce la tarjeta como almacenamiento activo:

  - Ve a **Device** (o **Settings**).
  - Selecciona **SD Status** / **SD Info**.
  - Debería mostrar el tamaño de la tarjeta, el espacio libre y confirmar que el sistema de archivos FAT32 está correctamente montado.


# Cómo guardar datos desde el menú del Marauder v8

Una vez introducida la tarjeta formateada en el Marauder, la interfaz habilitará automáticamente el almacenamiento SD:

* **Captura de paquetes (Handshakes / PCAP):**
  - Ve a **WiFi** > **Sniffers** > **EAPOL/PMKID Scan** (o **PKE / Handshake**).
  - Al pulsar **Start**, el archivo `.pcap` se escribirá directamente en la carpeta `/pcap` de la tarjeta SD.
  - Después puedes extraer la tarjeta SD, introducirla en tu máquina Ubuntu y abrir los archivos `.pcap` con **Wireshark** o analizarlos usando **aircrack-ng**.

* **Guardar logs de escaneo:**
  - Al realizar un escaneo de redes (**Scan** > **AP**) o de clientes (**Scan** > **STAs**), la opción de guardar resultados creará archivos `.txt` en la carpeta `/logs`.
 
* **Uso de diccionarios (Wordlists):**
  - Copia tus archivos de texto con contraseñas (por ejemplo, una lista personalizada o fragmentos de *rockyou.txt*) en la carpeta `/wordlists`.
  - Cuando ejecutes ataques de autenticación o pruebas que requieran un diccionario, el Marauder podrá leer los archivos directamente desde esa carpeta.
 
---


# 📶 Wifi Captura de paquetes PCAP

Un **archivo PCAP** (abreviatura de *Packet Capture*) es un formato estándar que contiene la grabación de todo el tráfico de datos transmitido a través de una red inalámbrica o de cable durante un periodo de tiempo. Funciona esencialmente como un "registro" o "vídeo" de lo que ha viajado por el aire: direcciones MAC, tramas de gestión y paquetes de datos.

En el contexto de la seguridad Wi-Fi, los archivos PCAP son fundamentales para analizar protocolos de red y entender el funcionamiento de intercambios de autenticación como el **WPA Handshake**.

---

### ¿Qué es un WPA Handshake (4-Way Handshake)?

Cuando un dispositivo (como un teléfono o portátil) se conecta a un router Wi-Fi protegido con WPA2 o WPA3, ambos intercambian **4 mensajes clave** antes de permitir la navegación. Este proceso de 4 pasos se conoce como *4-Way Handshake*.

* **Su función:** Permite que el router y el cliente demuestren que conocen la contraseña correcta y deriven las claves de cifrado temporales para la sesión, **sin enviar la contraseña real por el aire**.
* **Contenido de la captura:** El archivo PCAP registrado por un sniffer (como la Marauder) guarda esos 4 mensajes. Dentro de ellos viajan números aleatorios (*nonces*) y un código de autenticación (*MIC*).

---

### Análisis defensivo y auditoría con Wireshark en Ubuntu

Para inspeccionar y analizar capturas PCAP en un entorno de laboratorio o auditoría de red propia, se utiliza **Wireshark**.

#### 1. Instalación de Wireshark en Ubuntu

Abre la terminal e instala la herramienta:

```bash
sudo apt update
sudo apt install wireshark -y

```

*(Opcional: Durante la instalación, si pregunta si los usuarios no superusuarios deben poder capturar paquetes, selecciona "Sí" y añade tu usuario al grupo `wireshark` con `sudo usermod -aG wireshark $USER`).*

---

#### 2. Inspeccionar la captura PCAP

1. Copia el archivo `.pcap` generado por la tarjeta SD a tu equipo Ubuntu.
2. Abre el archivo en Wireshark:
```bash
wireshark /ruta/a/tu/archivo.pcap

```

3. **Filtros útiles en Wireshark:**
* Para ver únicamente los paquetes del intercambio de autenticación (*Handshake*), escribe en la barra de filtro superior:
```text
eapol

```

* Si deseas ver únicamente las tramas de gestión de una red o cliente específico por su dirección MAC:
```text
wlan.addr == XX:XX:XX:XX:XX:XX

```

Si el filtro `eapol` muestra los 4 mensajes (o al menos los pares necesarios 1-2 o 2-3), significa que la captura del Handshake se ha realizado correctamente y está completa para su análisis.

---

# ¿Cómo saber si tu `.pcap` sirve? (El Handshake)

**sí, necesitas que ese PCAP contenga el tráfico del *Handshake* completo** para poder descifrarlo con un diccionario, y **no necesitas ningún archivo adicional**, solo un buen diccionario (`wordlists`).

Un archivo `.pcap` capturado por un sniffer guarda todo el tráfico de radiofrecuencia que escucha. Si en el momento de la captura ningún dispositivo se conectó o reconoció a la red, el archivo solo tendrá tramas vacías y **no servirá**.

Para que un diccionario funcione, el archivo `.pcap` **debe contener obligatoriamente el intercambio de 4 mensajes (*4-Way Handshake*)** entre un cliente y el router.

Puedes comprobarlo rápidamente en tu Ubuntu con `aircrack-ng` (viene en el paquete `aircrack-ng`):

```bash
sudo apt install aircrack-ng -y
aircrack-ng xxxxxx.pcap

```

* **Si el resultado muestra una lista de redes y dice *"1 handshake"* (o similar):** ¡Perfecto! Tienes el paquete necesario.
* **Si dice *"0 handshake"*:** Significa que la captura no cogió la conexión y tendrás que volver a capturar (puedes acelerarlo forzando una desconexión o desautenticación si estás probando con tus propios equipos).

---

# El Diccionario (Wordlist)

Una vez confirmado que tu archivo tiene el Handshake, el siguiente paso es conseguir o crear un diccionario de claves.

Para pruebas en entornos controlados, puedes usar diccionarios comunes como `rockyou.txt` o crear un archivo de texto plano llamado `dictionary.txt` donde cada línea sea una contraseña candidata (incluyendo la real para probar que funciona):

```text
12345678
password
tu_contraseña_real_de_prueba
87654321

```

### ¿Qué es `rockyou.txt`?

Es el diccionario de contraseñas más famoso y utilizado en auditorías de seguridad y laboratorios de pruebas en todo el mundo. Es un archivo de texto plano que contiene millones de las contraseñas más comunes que la gente suele usar (como `12345678`, `password`, `qwerty`, etc.). En la mayoría de distribuciones enfocadas a ciberseguridad (como Kali Linux) ya viene preinstalado, pero en Ubuntu estándar normalmente hay que descargarlo o crearse uno propio para pruebas controladas.

Tienes varias opciones para conseguir `rockyou.txt` en Ubuntu:

### Opción 1: Descarga directa (la más sencilla)

Descarga el archivo comprimido desde el repositorio de Praetorian y descomprímelo:

```bash
wget https://github.com/praetorian-inc/Hob0Rules/raw/master/wordlists/rockyou.txt.gz
gunzip rockyou.txt.gz
```

Esto te dejará `rockyou.txt` en el directorio actual.

### Opción 2: Usar SecLists (más completo)

Si quieres tener muchas más listas de seguridad además de `rockyou.txt`, puedes clonar el repositorio de SecLists, que es la fuente más fiable y recomendada:

```bash
# Crear el directorio de wordlists
sudo mkdir -p /ruta/path/wordlists

# Clonar SecLists
sudo git clone https://github.com/danielmiessler/SecLists.git
```

`rockyou.txt` estará dentro en `SecLists/Passwords/Leaked-Databases/`. En algunas versiones del repositorio, el archivo viene comprimido como `rockyou.txt.tar.gz`, así que tendrías que extraerlo:

```bash
cd /ruta/path/wordlists/seclists/Passwords/Leaked-Databases/
sudo tar -xzf rockyou.txt.tar.gz
```

## Cómo crear un diccionario propio de pruebas (Paso a paso)

Para entender cómo funciona y probar si `aircrack-ng` es capaz de descifrar tu clave, lo más rápido y práctico es crear un archivo de texto con un editor y meter unas cuantas palabras de prueba (asegurándote de incluir la contraseña real de tu red de laboratorio entre ellas).

1. **Crear el archivo de texto:** Ubicación en tu proyecto.
Abre la terminal y crea un archivo llamado `dictionary.txt` dentro de la carpeta `wordlists` que ya tienes creada:

```bash
nano wordlists/dictionary.txt

```

2. **Añadir contraseñas candidatas:** Una por línea.
Escribe varias palabras o combinaciones de prueba, pulsa Enter después de cada una. Incluye por ejemplo:

```text
12345678
password
tu_contraseña_real_de_laboratorio
vodafone123
87654321

```

*(Guarda el archivo en nano pulsando `Ctrl + O`, luego `Enter`, y sal con `Ctrl + X`).*


3. **Verificar el archivo creado:** Comprobación rápida.
Comprueba que el archivo se ha guardado correctamente leyendo su contenido:

```bash
cat wordlists/dictionary.txt

```

*Verificación:* Deberías ver en pantalla la lista de contraseñas una debajo de otra.


---

Una vez que tengas tu `dictionary.txt` listo con la contraseña real metida dentro, ya podemos volver a lanzar el comando de `aircrack-ng` apuntando a él y ver la magia en acción.

---

# Lanzar el ataque de comprobación con Aircrack-ng

Cuando tengas tu archivo `.pcap` con el handshake verificado y tu diccionario listo, el comando en la terminal de Ubuntu para probar si la clave está en la lista es:

```bash
aircrack-ng -w dictionary.txt -b XX:XX:XX:XX:XX:XX eapol_0.pcap

```

*(Sustituye `XX:XX:XX:XX:XX:XX` por la dirección MAC del router/Access Point que capturaste).*

---

# 📡 Wardrive Tracker

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









