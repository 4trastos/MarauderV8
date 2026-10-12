# 📡 BT Disable

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BT Disable** desactiva el **módulo Bluetooth** del Marauder. Útil para:

- **Ahorrar batería** cuando no usas Bluetooth.
- **Evitar interferencias** con el WiFi.
- **Privacidad**: no emitir señales BLE.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → General → BT Disable**.
3. Pulsa **Disable**.
4. El módulo Bluetooth se desactiva.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Disable** | Desactivar Bluetooth | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BT Disable ===
Estado: Activo

[Disable]

Estado: Inactivo
```

No genera archivos. Solo desactiva el módulo.

---

## 🎯 Para qué sirve

### 1. Ahorro de batería

El Bluetooth consume energía. Si no lo usas, apágalo.

### 2. Evitar interferencias

En el ESP32, Bluetooth y WiFi comparten antena. Algunos firmwares no permiten ambos a la vez. Apagar uno mejora el otro.

### 3. Privacidad

Si no quieres emitir señales BLE, apaga el módulo.

### 4. Preparar para WiFi

Si vas a hacer un ataque WiFi, apaga el Bluetooth para evitar interferencias.

---

## ⚠️ Advertencias

- **Irreversible sin BT Enable:** una vez apagado, no se vuelve a encender hasta que uses **BT Enable**.
- **Estado:** si tenías capturas en curso, se cancelan.
- **WiFi:** apagar Bluetooth puede mejorar el rendimiento del WiFi.

---

## 🔗 Relacionado

- [BT Enable](bt-enable.md) — activa el Bluetooth
- [Shutdown WiFi](../wifi/general/shutdown-wifi.md) — apaga el WiFi
- [BT Status](bt-status.md) — estado del módulo
