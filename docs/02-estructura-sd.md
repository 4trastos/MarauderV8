# Estructura de carpetas recomendada

[Volver al índice](../README.md)

---

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

---

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