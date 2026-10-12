# 📡 BLE Sniff

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Sniff** captura **todos los anuncios BLE** (ADV_IND, ADV_NONCONN_IND, ADV_SCAN_IND) y los vuelca a un archivo **`.pcap`**. Es la versión forense del BLE Scan: no solo lista los dispositivos, sino que guarda **todo el contenido** de sus anuncios.

Con el pcap puedes analizar después:

- Qué datos anuncian.
- Qué servicios ofrecen.
- Qué fabricante son.
- Si son rastreables.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada**.
2. Navega hasta **Bluetooth → Sniffers → BLE Sniff**.
3. Pulsa **Start**.
4. El Marauder capturará todos los anuncios BLE.
5. Pulsa **Stop** cuando termines.
6. El pcap se guarda en `/pcap/ble_XXXX.pcap`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Duración** | Tiempo máximo de captura | Sin límite |
| **Filtro MAC** | Solo anuncios de una MAC | Ninguno |
| **Guardar** | Guardar pcap en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Sniff ===
Canal: 37, 38, 39
Archivo: /pcap/ble_20261011_123456.pcap

Estado: Capturando...
Paquetes: 4521
Tamaño: 1.2 MB
Tiempo: 00:02:30
```

### En la SD

Un archivo `.pcap` con los anuncios BLE. Puedes analizarlo con:

- **Wireshark** (con filtro `btle`).
- **tshark** (con `-Y btle`).
- **Herramientas específicas** de análisis BLE.

### Análisis con `tshark`

```bash
# Ver todos los anuncios BLE
tshark -r ble_20261011_123456.pcap -Y btle

# Ver solo los dispositivos Apple
tshark -r ble_20261011_123456.pcap -Y "btle.advertising_address" -T fields -e btle.advertising_address
```

---

## 🎯 Para qué sirve

### 1. Análisis forense BLE

Si necesitas estudiar en detalle qué anuncia un dispositivo BLE, **BLE Sniff** te da los datos en bruto.

### 2. Detección de rastreadores

Si sospechas que hay un AirTag o Tile rastreándote, **BLE Sniff** captura sus anuncios. Luego puedes analizarlos.

### 3. Investigación de protocolos

Si estás estudiando BLE, **BLE Sniff** te da datos reales de dispositivos reales.

### 4. Documentación de incidentes

Si has detectado un dispositivo BLE sospechoso, **BLE Sniff** te da el pcap para documentar.

### 5. Base para BLE Replay

Si quieres reproducir anuncios BLE, primero necesitas capturarlos con **BLE Sniff**.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar el pcap.
- **Tamaño:** el pcap puede crecer rápido. En zonas densas, 1 hora puede generar 50-100 MB.
- **Canal único:** el Marauder escucha los 3 canales BLE de advertising (37, 38, 39) secuencialmente. Algunos anuncios pueden perderse.
- **MAC randomization:** muchos dispositivos usan MAC aleatoria. El pcap tendrá MACs que cambian.
- **Legalidad:** capturar anuncios BLE es **pasivo** y legal. Analizarlos es legal.
- **Privacidad:** los anuncios BLE pueden contener información personal. No la compartas.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — versión simple, sin pcap
- [AirTag Sniffer](airtag-sniffer.md) — detecta AirTags
- [Flipper Sniffer](flipper-sniffer.md) — detecta Flipper Zero
- [BLE Replay](../attacks/ble-replay.md) — reproduce anuncios capturados
