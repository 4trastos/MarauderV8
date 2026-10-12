# 🔌 BLE Disconnect

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Disconnect** fuerza la **desconexión** de dispositivos BLE conectados. Envía tramas de desconexión BLE a los dispositivos, forzándolos a romper la conexión con su dispositivo emparejado.

Es útil para:

- **Interrumpir** conexiones BLE.
- **Forzar reconexiones** (y capturar el proceso).
- **Pruebas de estrés** de dispositivos BLE.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea dispositivos BLE** con **BLE Scan**.
2. Identifica la **MAC** del dispositivo a desconectar.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → BLE Disconnect**.
3. Introduce la **MAC** del dispositivo.
4. Pulsa **Start**.
5. El Marauder enviará tramas de desconexión.
6. El dispositivo se desconectará.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **MAC** | MAC del dispositivo | Ninguna |
| **Nº de tramas** | Cuántas enviar | 10 |
| **Intervalo** | Tiempo entre tramas | 100 ms |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Disconnect ===
Objetivo: DE:AD:BE:EF:12:34
Nº tramas: 10
Intervalo: 100 ms

Tramas enviadas: 10
Dispositivo desconectado.
```

No genera archivos. Solo envía tramas.

---

## 🎯 Para qué sirve

### 1. Interrupción de conexión

Interrumpir la conexión BLE de un dispositivo (auriculares, wearable, etc.).

### 2. Forzar reconexión

Al desconectar, el dispositivo intenta reconectarse. Puedes capturar ese proceso con **BLE Sniff**.

### 3. Pruebas de estrés

Ver cómo se comporta un dispositivo cuando se le desconecta repetidamente.

### 4. Base para ataques

Al desconectar, puedes hacerte pasar por el dispositivo emparejado (**BLE Replay**).

---

## ⚠️ Advertencias

- **Legalidad:** desconectar un dispositivo ajeno es **interferencia**. Delito.
- **Detección:** los WIDS/WIPS detectan tramas de desconexión anómalas.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos dispositivos se reconectan automáticamente. Otros requieren intervención manual.
- **Ética:** no uses BLE Disconnect contra dispositivos ajenos.

---

## 🔗 Relacionado

- [BLE Sniff](../sniffers/ble-sniff.md) — captura anuncios BLE
- [BLE Replay](ble-replay.md) — reproduce anuncios capturados
- [BT Tracker](../sniffers/bt-tracker.md) — rastrea un dispositivo
