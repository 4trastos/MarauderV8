# 📡 BLE Characteristic Scan

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Characteristic Scan** lee las **características** de un **servicio GATT** de un dispositivo BLE. Cada servicio tiene una o más características, y cada característica tiene:

- **UUID** (identificador).
- **Valor** (los datos).
- **Propiedades** (leer, escribir, notificar).

**BLE Characteristic Scan** te dice qué características tiene un servicio y, si es posible, lee sus valores.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Enumera servicios** con **BLE Service Scan**.
2. Identifica el **servicio** que quieres analizar.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Scanners → BLE Characteristic Scan**.
3. Introduce la **MAC** del dispositivo.
4. Selecciona el **servicio** a analizar.
5. Pulsa **Connect** para conectar.
6. El Marauder enumerará las características del servicio.
7. Si es posible, leerá sus valores.
8. Pulsa **Disconnect** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **MAC** | MAC del dispositivo | Ninguna |
| **Servicio** | UUID del servicio | Ninguno |
| **Leer** | Leer valores | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Characteristic Scan ===
Dispositivo: DE:AD:BE:EF:12:34
Servicio: 0x180D (Heart Rate)

Características encontradas: 3
UUID          Propiedades       Valor
0x2A37        Notify            0x00
0x2A38        Read              72 bpm
0x2A39        Read/Write        0x01
```

### En la SD

Un archivo `.txt`:

```text
UUID,Properties,Value
0x2A37,Notify,0x00
0x2A38,Read,72 bpm
0x2A39,Read/Write,0x01
```

---

## 🎯 Para qué sirve

### 1. Leer datos de sensores

Si el dispositivo expone un servicio de sensor (temperatura, ritmo cardíaco), puedes leer sus valores.

### 2. Análisis de seguridad

Algunas características exponen datos sin autenticación. **BLE Characteristic Scan** te los revela.

### 3. Desarrollo de apps

Si vas a desarrollar una app que se conecte a un dispositivo BLE, **BLE Characteristic Scan** te dice qué características esperar.

### 4. Investigación

Si estás estudiando BLE, **BLE Characteristic Scan** te da datos reales de dispositivos reales.

---

## 🎯 Propiedades de características

| Propiedad | Significado |
|---|---|
| **Read** | Puedes leer el valor |
| **Write** | Puedes escribir el valor |
| **Notify** | El dispositivo te notifica cuando cambia |
| **Indicate** | Similar a Notify, pero con confirmación |

---

## ⚠️ Advertencias

- **Legalidad:** leer características de un dispositivo ajeno sin autorización es **delito**.
- **Permisos:** algunas características requieren autenticación. Sin ella, no podrás leerlas.
- **Alcance:** BLE tiene un alcance de ~10-30 metros.
- **Estabilidad:** si el dispositivo se aleja, la conexión se pierde.
- **Privacidad:** las características pueden revelar información sensible.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — escaneo general
- [BLE Service Scan](ble-service-scan.md) — enumera servicios
- [BT Tracker](../sniffers/bt-tracker.md) — rastrea un dispositivo