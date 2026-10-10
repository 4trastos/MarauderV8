# Instalar o Actualizar el Firmware

[Volver al índice](../README.md)

---

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
