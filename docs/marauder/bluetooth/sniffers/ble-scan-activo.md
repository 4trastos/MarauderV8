# 📡 BLE Scan (activo)

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Scan (activo)** es la versión **activa** del BLE Scan. A diferencia del pasivo (que solo escucha anuncios), este envía **scan requests** a los dispositivos BLE, solicitando información adicional:

- **Nombre completo** del dispositivo (si no lo anuncia).
- **Servicios GATT** disponibles.
- **Datos del fabricante**.
- **TX Power**.

El resultado es una lista **más completa** que la del scan pasivo.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Scanners → BLE Scan (activo)**.
3. Pulsa **Start**.
4. El Marauder enviará scan requests y esperará respuestas.
5. Verás en pantalla una lista más detallada que en el scan pasivo.
6. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Duración** | Tiempo de escaneo | Sin límite |
| **Timeout** | Tiempo de espera por respuesta | 500 ms |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Scan (activo) ===
Dispositivos detectados: 12

MAC                 Nombre              RSSI  Servicios  TX Power
DE:AD:BE:EF


