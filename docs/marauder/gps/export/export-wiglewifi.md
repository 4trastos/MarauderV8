# 📤 Export WigleWifi

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Export WigleWifi** exporta el **log actual** (o uno guardado) a formato **WigleWifi CSV**, el estándar de facto para wardriving.

El CSV resultante se puede:

- **Subir a WiGLE** (base de datos mundial).
- **Analizar con Wardrive Tracker** (mapa interactivo).
- **Convertir** a GPX/KML con `gpsbabel`.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **SD insertada**.
2. Navega hasta **GPS → Export → Export WigleWifi**.
3. Selecciona el **log** a exportar (o usa el actual).
4. Pulsa **Export**.
5. El archivo se guarda en `/logs/wigle_XXXX.csv`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Log** | Log a exportar | Actual |
| **Formato** | WigleWifi CSV | CSV |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Export WigleWifi ===
Log: wardrive_20261011_123456
Formato: WigleWifi CSV

Exportando...
Archivo: /logs/wigle_20261011_123456.csv
Redes: 47
```

### En la SD

Un archivo `.csv` con el header estándar:

```text
MAC,SSID,AuthMode,FirstSeen,Channel,RSSI,CurrentLatitude,CurrentLongitude,AltitudeMeters,AccuracyMeters,Type
FA:8F:CA:61:05:78,MiFibra-BB6F,[WPA2-PSK-CCMP][ESS],2026-10-11 12:34:56,6,-67,40.4168,-3.7038,650,10,WIFI
...
```

---

## 🎯 Para qué sirve

### 1. Subir a WiGLE

WiGLE es la base de datos mundial de redes WiFi. Subir tus logs ayuda a la comunidad.

###