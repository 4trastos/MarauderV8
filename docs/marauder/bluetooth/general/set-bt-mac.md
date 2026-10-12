# 📡 Set BT MAC

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Set BT MAC** permite **cambiar la dirección MAC** del adaptador Bluetooth del Marauder. Esto se conoce como **MAC spoofing BLE**.

Cambiar la MAC es útil para:

- **Ocultar la MAC real** del Marauder.
- **Suplantar** la MAC de otro dispositivo BLE.
- **Evitar filtros MAC** en sistemas BLE.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → General → Set BT MAC**.
3. Introduce la MAC nueva (formato `XX:XX:XX:XX:XX:XX`).
4. Pulsa **Save**.
5. La MAC se aplica (o al reiniciar, según firmware).

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **MAC** | MAC del Bluetooth | La real del chip |
| **Aleatoria** | Generar MAC aleatoria | No |
| **Aplicar** | Aplicar al instante | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Set BT MAC ===
MAC actual: DE:AD:BE:EF:12:34
MAC nueva:  AA:BB:CC:DD:EE:FF

[Save]
```

No genera archivos. El cambio es en memoria.

---

## 🎯 Para qué sirve

### 1. Ocultar la MAC real

Si no quieres que tu MAC real aparezca en los logs de un dispositivo BLE.

### 2. Evitar filtros MAC

Si un dispositivo tiene filtrado MAC (solo permite ciertas MACs), puedes suplantar la de un dispositivo autorizado.

### 3. Suplantar dispositivos

Si quieres hacerte pasar por otro dispositivo BLE (AirTag, wearable), puedes usar su MAC.

### 4. Base para ataques

Algunos ataques BLE requieren MAC spoofing:

- **BLE Replay**: reproducir anuncios con la MAC del dispositivo original.
- **BLE Disconnect**: enviar tramas con la MAC del dispositivo emparejado.

---

## ⚠️ Advertencias

- **Legalidad:** suplantar la MAC de un dispositivo ajeno es **delito**.
- **Detección:** los sistemas BLE modernos detectan MACs duplicadas.
- **Restricciones:** algunas MACs no se pueden usar (multicast, broadcast).
- **Persistencia:** algunos firmwares no guardan la MAC tras reiniciar.

---

## 🔗 Relacionado

- [BLE Replay](../attacks/ble-replay.md) — usa MAC spoofing
- [BLE Disconnect](../attacks/ble-disconnect.md) — usa MAC spoofing
- [BT Info](../sniffers/bt-info.md) — info del módulo
- [Set MACs](../wifi/general/set-macs.md) — versión WiFi