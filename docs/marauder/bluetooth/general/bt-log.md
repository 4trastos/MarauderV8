# 📄 BT Log

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BT Log** exporta los datos BLE capturados a un archivo en la **tarjeta SD**. Puedes exportar:

- **Lista de dispositivos** detectados (MAC, nombre, RSSI).
- **Anuncios BLE** capturados (a pcap).
- **Datos de rastreo** de BT Tracker.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada**.
2. **Captura datos** con BLE Scan, BLE Sniff, BT Tracker, etc.
3. Navega hasta **Bluetooth → General → BT Log**.
4. Selecciona el **tipo de log** a exportar:
   - **Dispositivos**: lista de dispositivos.
   - **Anuncios**: pcap con anuncios.
   - **Rastreo**: histórico de un dispositivo.
5. Pulsa **Export**.
6. El archivo se guarda en `/logs/` o `/pcap/` según el tipo.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Tipo** | Dispositivos, Anuncios, Rastreo | Dispositivos |
| **Formato** | TXT, CSV, Pcap | TXT |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BT Log ===
Tipo: Dispositivos
Formato: CSV

Exportando...
Archivo: /logs/bt_devices_20261011_123456.csv
Dispositivos: 12
```

### En la SD

Un archivo `.csv`:

```text
MAC,Name,RSSI,Type,Manufacturer
DE:AD:BE:EF:12:34,AirPods Pro,-62,Audio,Apple
AA:BB:CC:DD:EE:FF,,(sin nombre),-70,Desconocido,
...
```

O un `.pcap`:

```text
/pcap/ble_20261011_123456.pcap
```

---

## 🎯 Para qué sirve

### 1. Documentar capturas

Si has hecho un BLE Scan, **BT Log** te guarda los datos para análisis posterior.

### 2. Análisis en PC

El CSV o pcap se puede analizar en Wireshark, Excel, Python, etc.

### 3. Forense

Si has detectado un dispositivo sospechoso, **BT Log** te da la evidencia.

### 4. Inventario

Si necesitas documentar qué dispositivos BLE hay en una ubicación, **BT Log** te lo da.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Formato:** el formato depende del tipo de log.
- **Privacidad:** los datos BLE pueden ser sensibles. No los compartas.

---

## 🔗 Relacionado

- [BLE Scan](../sniffers/ble-scan.md) — escanea dispositivos
- [BLE Sniff](../sniffers/ble-sniff.md) — captura anuncios a pcap
- [BT Tracker](../sniffers/bt-tracker.md) — rastrea un dispositivo
- [Clear BT Devices](clear-bt-devices.md) — borra la lista
