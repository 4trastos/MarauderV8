# 📡 BLE Service Scan

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Service Scan** **enumera los servicios GATT** de un dispositivo BLE conectado. GATT (*Generic Attribute Profile*) es el protocolo que define cómo se estructuran los datos en BLE.

Cada dispositivo BLE expone uno o más **servicios**, cada uno con **características**. Por ejemplo:

- Un sensor de temperatura expone un servicio `0x1809` (Health Thermometer).
- Un reloj expone un servicio `0x180D` (Heart Rate).
- Un teclado expone un servicio `0x1812` (Human Interface Device).

**BLE Service Scan** te dice qué servicios ofrece un dispositivo.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea dispositivos BLE** con **BLE Scan** o **BLE Scan (activo)**.
2. Identifica la **MAC** del dispositivo a analizar.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Scanners → BLE Service Scan**.
3. Introduce la **MAC** del dispositivo.
4. Pulsa **Connect** para conectar.
5. El Marauder enumerará los servicios GATT.
6. Verás en pantalla la lista de servicios con sus UUIDs.
7. Pulsa **Disconnect** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **MAC** | MAC del dispositivo | Ninguna |
| **Timeout** | Tiempo de conexión | 5 segundos |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Service Scan ===
Dispositivo: DE:AD:BE:EF:12:34 (Mi Band 6)

Servicios encontrados: 5
UUID          Descripción
0x1800        Generic Access
0x1801        Generic Attribute
0x180A        Device Information
0x180D        Heart Rate
0x180F        Battery Service
```

### En la SD

Un archivo `.txt`:

```text
UUID,Description
0x1800,Generic Access
0x1801,Generic Attribute
0x180A,Device Information
0x180D,Heart Rate
0x180F,Battery Service
```

---

## 🎯 Para qué sirve

### 1. Inventario de servicios

Saber qué servicios ofrece un dispositivo BLE. Útil para:

- Entender qué hace el dispositivo.
- Ver si expone datos sensibles.
- Documentar un dispositivo.

### 2. Base para BLE Characteristic Scan

Una vez sabes los servicios, puedes leer sus características con **BLE Characteristic Scan**.

### 3. Análisis de seguridad

Algunos servicios BLE pueden exponer datos sin autenticación. **BLE Service Scan** te los revela.

### 4. Compatibilidad

Si vas a desarrollar una app que se conecte a un dispositivo BLE, **BLE Service Scan** te dice qué servicios esperar.

---

## 🎯 UUIDs de servicios comunes

| UUID | Servicio |
|---|---|
| `0x1800` | Generic Access |
| `0x1801` | Generic Attribute |
| `0x180A` | Device Information |
| `0x180D` | Heart Rate |
| `0x180F` | Battery Service |
| `0x1809` | Health Thermometer |
| `0x1812` | Human Interface Device |
| `0x181A` | Environmental Sensing |
| `0x181C` | User Data |
| `0x181D` | Weight Scale |

---

## ⚠️ Advertencias

- **Legalidad:** conectar a un dispositivo BLE ajeno sin autorización es **delito**.
- **Emparejamiento:** algunos dispositivos requieren emparejamiento previo. Sin él, no podrás enumerar servicios.
- **Alcance:** BLE tiene un alcance de ~10-30 metros.
- **Estabilidad:** si el dispositivo se aleja, la conexión se pierde.
- **Privacidad:** los servicios GATT pueden revelar información sensible.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — escaneo general
- [BLE Scan (activo)](ble-scan-activo.md) — escaneo activo
- [BLE Characteristic Scan](ble-characteristic-scan.md) — lee características
- [BT Tracker](../sniffers/bt-tracker.md) — rastrea un dispositivo
