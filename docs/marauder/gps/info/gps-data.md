# 🛰️ GPS Data

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Data** muestra las **sentencias NMEA en bruto** que envía el módulo GPS. NMEA es el estándar de comunicación de los GPS: son frases de texto con los datos de posición, hora, satélites, etc.

Es la herramienta de **debug** del GPS: te dice exactamente qué está enviando el módulo.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Info → GPS Data**.
3. Verás las sentencias NMEA fluyendo en tiempo real.
4. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Pausa** | Pausar el flujo | No |
| **Limpiar** | Limpiar pantalla | No |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Data ===
$GPGGA,123501.00,4016.808,N,00342.228,W,1,08,1.2,650.0,M,,,,*4A
$GPGSA,A,3,01,02,03,04,05,06,07,08,,,,,1.5,1.2,2.0*3B
$GPRMC,123501.00,A,4016.808,N,00342.228,W,0.5,0.0,111026,,,A*6F
$GPGSV,3,1,11,01,45,123,45,02,60,234,50,...*7A
...
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Debug del GPS

Si el GPS no da fix, **GPS Data** te dice si está enviando datos. Si no ves sentencias NMEA, el módulo no está comunicando.

### 2. Verificar la comunicación UART

Si ves sentencias pero con errores, puede ser problema de baud rate. Ajusta con **GPS Baud Rate**.

### 3. Análisis avanzado

Si quieres procesar los datos NMEA en un PC, puedes capturarlos con **GPS Data Log**.

### 4. Diagnóstico de interferencias

Si las sentencias tienen errores o faltan, puede haber interferencias.

---

## 🎯 Sentencias NMEA comunes

| Sentencia | Qué contiene |
|---|---|
| **$GPGGA** | Posición, hora, satélites, altitud, HDOP |
| **$GPGSA** | Satélites usados, DOP |
| **$GPRMC** | Posición, hora, fecha, velocidad |
| **$GPGSV** | Satélites visibles (varias sentencias) |
| **$GPVTG** | Velocidad y rumbo |
| **$GPZDA** | Fecha y hora |

---

## ⚠️ Advertencias

- **GPS obligatorio:** sin módulo GPS conectado, esta función no muestra nada.
- **Baud rate:** si no ves sentencias legibles, prueba con otro baud rate (**GPS Baud Rate**).
- **Al aire libre:** el GPS necesita visibilidad de satélites.

---

## 🔗 Relacionado

- [GPS Info](gps-info.md) — info principal
- [GPS Status](gps-status.md) — estado del fix
- [GPS Baud Rate](gps-baud-rate.md) — configura la velocidad
- [GPS Data Log](../captura/gps-data-log.md) — guarda los datos NMEA
