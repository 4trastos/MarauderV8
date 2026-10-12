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

### 2. Analizar con Wardrive Tracker

El CSV se puede cargar en **Wardrive Tracker** para ver las redes en un mapa.

### 3. Convertir a otros formatos

```bash
gpsbabel -i wigle -f wigle_20261011_123456.csv -o gpx -F recorrido.gpx
```

### 4. Documentación

Si necesitas documentar un wardrive, el CSV es el formato estándar.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Formato:** el CSV debe tener el header correcto para ser aceptado.
- **Privacidad:** los SSIDs y MACs son información sensible. No los compartas sin cuidado.

---

## 🔗 Relacionado

- [WigleWifi Log](../captura/wiglewifi-log.md) — genera el log
- [Wardrive GPS](../captura/wardrive-gps.md) — captura con GPS
- [Wardrive Tracker](../../07-wardrive.md) — análisis del CSV
- [WiGLE](https://wigle.net/) — base de datos mundial