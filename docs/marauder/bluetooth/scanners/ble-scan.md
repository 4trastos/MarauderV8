# 📡 BLE Scan

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Scan** es un escaneo **pasivo** de dispositivos Bluetooth Low Energy (BLE) cercanos. Muestra una lista con:

- **MAC** (BD_ADDR)
- **Nombre** (si lo anuncia)
- **RSSI** (intensidad de señal)
- **Tipo de dispositivo**
- **Fabricante** (si se puede determinar por OUI)

Es la herramienta más básica para descubrir qué dispositivos BLE hay en tu entorno.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Sniffers → BLE Scan**.
3. Pulsa **Start**.
4. El Marauder escaneará todos los canales BLE (37, 38, 39) y mostrará los dispositivos detectados.
5. Pulsa **Stop** cuando tengas la lista que buscas.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Duración** | Tiempo de escaneo | Sin límite |
| **Filtro MAC** | Solo dispositivos de una MAC | Ninguno |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Scan ===
Dispositivos detectados: 12

MAC                 Nombre              RSSI  Tipo
DE:AD:BE:EF:12:34   AirPods Pro         -62   Audio
AA:BB:CC:DD:EE:FF   (sin nombre)        -70   Desconocido
3C:5A:B4:12:34:56   Mi Band 6           -65   Wearable
...
```

### En la SD

Un archivo `.txt`:

```text
MAC,Name,RSSI,Type,Manufacturer
DE:AD:BE:EF:12:34,AirPods Pro,-62,Audio,Apple
AA:BB:CC:DD:EE:FF,,(sin nombre),-70,Desconocido,
...
```

---

## 🎯 Para qué sirve

### 1. Inventario de dispositivos BLE

Saber qué dispositivos BLE hay en tu entorno:

- Auriculares (AirPods, Galaxy Buds).
- Wearables (smartwatch, pulseras).
- Sensores (temperatura, humedad).
- Beacons (iBeacon, Eddystone).
- AirTags y similares.

### 2. Detección de dispositivos desconocidos

Si ves un dispositivo BLE que no reconoces, puede ser:

- Un dispositivo de un vecino.
- Un rastreador (AirTag, Tile).
- Un dispositivo malicioso (Flipper, Pwnagotchi).

### 3. Base para otros análisis

**BLE Scan** es el primer paso antes de:

- **BLE Sniff** (capturar anuncios).
- **BT Tracker** (rastrear un dispositivo).
- **BLE Service Scan** (enumerar servicios).

### 4. Análisis de densidad

Ver cuántos dispositivos BLE hay en una zona. Útil para:

- Estudiar la densidad de dispositivos.
- Elegir canales BLE menos saturados.
- Documentar el entorno.

---

## ⚠️ Advertencias

- **Legalidad:** escanear BLE es **pasivo** y legal. Los dispositivos BLE emiten anuncios públicos.
- **MAC randomization:** muchos dispositivos usan **MAC aleatoria** en sus anuncios. Verás MACs que cambian cada cierto tiempo.
- **Alcance:** BLE tiene un alcance de ~10-30 metros. Si el dispositivo está lejos, no lo ves.
- **Ruido:** en zonas muy saturadas (centros comerciales, aeropuertos), verás cientos de dispositivos.
- **Privacidad:** aunque los anuncios son públicos, la información puede ser sensible. No la compartas.

---

## 🔗 Relacionado

- [BLE Sniff](ble-sniff.md) — captura anuncios BLE a pcap
- [AirTag Sniffer](airtag-sniffer.md) — detecta AirTags
- [Flipper Sniffer](flipper-sniffer.md) — detecta Flipper Zero
- [BT Tracker](bt-tracker.md) — rastrea un dispositivo
