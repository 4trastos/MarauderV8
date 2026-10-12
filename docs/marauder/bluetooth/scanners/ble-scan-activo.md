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
DE:AD:BE:EF:12:34   AirPods Pro         -62   0x180A     -10
AA:BB:CC:DD:EE:FF   Mi Band 6           -65   0x180D     -12
...
```

### En la SD

Un archivo `.txt`:

```text
MAC,Name,RSSI,Services,TXPower,Manufacturer
DE:AD:BE:EF:12:34,AirPods Pro,-62,0x180A,0x180F,-10,Apple
...
```

---

## 🎯 Para qué sirve

### 1. Inventario detallado

Obtener más información de cada dispositivo BLE que con el scan pasivo.

### 2. Análisis de servicios

Ver qué servicios GATT ofrece cada dispositivo (útil para saber qué hace).

### 3. Base para BLE Service Scan

Antes de conectar a un dispositivo para enumerar servicios, **BLE Scan (activo)** te da una idea de qué esperar.

### 4. Detección de dispositivos ocultos

Algunos dispositivos no anuncian su nombre en el scan pasivo, pero responden a scan requests con más info.

---

## ⚠️ Advertencias

- **Legalidad:** enviar scan requests es **activo**, pero BLE está diseñado para permitirlo. Es legal.
- **Detección:** los dispositivos pueden detectar que estás escaneando activamente.
- **Alcance:** BLE tiene un alcance de ~10-30 metros.
- **Respuestas:** no todos los dispositivos responden a scan requests. Algunos solo emiten anuncios pasivos.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — versión pasiva
- [BLE Service Scan](ble-service-scan.md) — enumera servicios GATT
- [BLE Characteristic Scan](ble-characteristic-scan.md) — lee características
