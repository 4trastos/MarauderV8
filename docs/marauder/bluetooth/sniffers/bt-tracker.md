# 📡 BT Tracker

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BT Tracker** rastrea un **dispositivo BLE específico** por su **MAC**. Muestra en tiempo real:

- **RSSI** (intensidad de señal).
- **Estado** (presente/ausente).
- **Histórico** de avistamientos.

Es la versión BLE de **MAC Monitor** (WiFi) y **Fox Hunt** (WiFi): te dice si un dispositivo está presente y dónde.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea dispositivos BLE** con **BLE Scan** o **BLE Sniff**.
2. Identifica la **MAC** del dispositivo que quieres rastrear.
3. Anota la MAC.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Sniffers → BT Tracker**.
3. Introduce la **MAC** del dispositivo a rastrear.
4. Pulsa **Start**.
5. El Marauder escaneará los canales BLE buscando esa MAC.
6. Verás en pantalla:
   - **RSSI** actual.
   - **Estado** (presente/ausente).
   - **Histórico** de las últimas lecturas.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **MAC** | MAC del dispositivo | Ninguna |
| **Actualización** | Frecuencia de refresco | 500 ms |
| **Guardar** | Guardar en SD | No |

---

## 📊 Qué genera

### En pantalla

```text
=== BT Tracker ===
Objetivo: DE:AD:BE:EF:12:34

RSSI actual: -62 dBm
Estado: ✅ Presente

Intensidad:
████████████████░░░░░░░░░░░░

Últimas 20 lecturas:
-62 -60 -58 -60 -62 -65 -68 -70 -72 -75 -78 -80 -82 -85 -88 -90 -92 -95 -98 -100
```

### En la SD (opcional)

Un archivo `.txt`:

```text
Timestamp,RSSI,Latitude,Longitude
2026-10-11 12:35:01,-62,40.4168,-3.7038
...
```

---

## 🎯 Para qué sirve

### 1. Rastrear un dispositivo BLE

Si quieres saber si un dispositivo BLE está presente en una zona, **BT Tracker** te lo dice.

### 2. Localizar un AirTag

Si has detectado un AirTag sospechoso, **BT Tracker** te ayuda a rastrearlo.

### 3. Análisis de movimiento

Si registras RSSI a lo largo del tiempo, puedes inferir el movimiento del dispositivo.

### 4. Base para Fox Hunt BLE

Si necesitas localizar físicamente un dispositivo BLE, **BT Tracker** te da el RSSI en tiempo real (que es lo que usarías para moverte hacia él).

### 5. Auditoría de privacidad

Si sospechas que un dispositivo BLE te está siguiendo, **BT Tracker** te confirma si está siempre presente.

---

## ⚠️ Advertencias

- **Legalidad:** rastrear un dispositivo **ajeno** sin consentimiento es **invasión de privacidad**.
- **MAC randomization:** muchos dispositivos BLE usan **MAC aleatoria** que cambia cada cierto tiempo. Si el dispositivo cambia de MAC, **BT Tracker** pierde el rastro.
- **Alcance:** BLE tiene un alcance de ~10-30 metros.
- **Interferencias:** en zonas saturadas, el RSSI fluctúa mucho.
- **Privacidad:** no uses esto para rastrear personas sin su consentimiento.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — escaneo general de BLE
- [BLE Sniff](ble-sniff.md) — captura anuncios a pcap
- [AirTag Sniffer](airtag-sniffer.md) — detecta AirTags
- [Fox Hunt](../wifi/sniffers/fox-hunt.md) — versión WiFi del rastreo
- [MAC Monitor](../wifi/sniffers/mac-monitor.md) — versión WiFi del monitoreo
