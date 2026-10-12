# 📡 BT Enable

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BT Enable** activa el **módulo Bluetooth** del Marauder. Es necesario para usar cualquier función Bluetooth (scan, sniff, attacks, etc.).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → General → BT Enable**.
3. Pulsa **Enable**.
4. El módulo Bluetooth se activa.
5. Verás el estado en pantalla.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Enable** | Activar Bluetooth | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BT Enable ===
Estado: Inactivo

[Enable]

Estado: Activo
MAC: DE:AD:BE:EF:12:34
```

No genera archivos. Solo activa el módulo.

---

## 🎯 Para qué sirve

### 1. Activar Bluetooth

Si el módulo estaba apagado (**BT Disable**), lo vuelves a encender.

### 2. Preparar para uso

Antes de usar cualquier función Bluetooth, asegúrate de que está activo.

### 3. Diagnóstico

Si el Bluetooth no funciona, **BT Enable** te dice si el módulo está activo.

---

## ⚠️ Advertencias

- **Consumo:** el Bluetooth consume energía. Si no lo usas, apágalo con **BT Disable**.
- **WiFi:** el Bluetooth y el WiFi comparten antena en el ESP32. Algunos firmwares no permiten ambos a la vez.
- **Estado:** si el módulo no se activa, puede ser un problema de hardware.

---

## 🔗 Relacionado

- [BT Disable](bt-disable.md) — desactiva el Bluetooth
- [BT Info](../sniffers/bt-info.md) — info del módulo
- [BT Status](bt-status.md) — estado del módulo
