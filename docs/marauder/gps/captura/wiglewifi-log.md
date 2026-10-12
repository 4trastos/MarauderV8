# 🛰️ WigleWifi Log

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**WigleWifi Log** genera un archivo en formato **WigleWifi CSV**, el estándar de facto para **wardriving**. El formato incluye:

- **MAC** del AP.
- **SSID**.
- **AuthMode** (cifrado).
- **FirstSeen** (timestamp).
- **Channel**.
- **RSSI**.
- **Coordenadas** (latitud, longitud, altitud, precisión).
- **Type** (WIFI o BLE).

Es el formato que aceptan **WiGLE**, **Wardrive Tracker**, **Kismet** y otras herramientas.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado** y la **SD insertada**.
2. Navega hasta **GPS → Captura → WigleWifi Log**.
3. Pulsa **Start** para empezar a registrar.
4. El Marauder escaneará WiFi y guardará cada red con sus coordenadas.
5. Pulsa **Stop** cuando termines.
6. El log se guarda en `/logs/wigle_XXXX.csv`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Intervalo** | Tiempo por canal | 1 segundo |
| **Formato** | WigleWifi CSV | CSV |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== WigleWifi Log ===
Archivo: /logs/wigle_20261011_123456.csv
Redes: 47
Tiempo: 00:15:30
```

### En la SD

Un archivo `.csv`:

```text
MAC,SSID,AuthMode,FirstSeen,Channel,RSSI,CurrentLatitude,CurrentLongitude,AltitudeMeters,AccuracyMeters,Type
FA:8F:CA:61:05:78,MiFibra-BB6F,[WPA2-PSK-CCMP][ESS],2026-10-11 12:34:56,6,-67,40.4168,-3.7038,650,10,WIFI
00:1A:2B:3C:4D:5E,Movistar_5G,[WPA2-PSK-CCMP][WPS][ESS],2026-10-11 12:35:01,44,-72,40.4170,-3.7040,650,12,WIFI
```

---

## 🎯 Para qué sirve

### 1. Contribuir a WiGLE

WiGLE es la base de datos mundial de redes WiFi. Subir tus logs ayuda a la comunidad.

### 2. Análisis con Wardrive Tracker

El CSV se puede cargar en **Wardrive Tracker** para ver las redes en un mapa interactivo.

### 3. Compatibilidad

El formato WigleWifi CSV es aceptado por muchas herramientas:

- **WiGLE** (web)
- **Wardrive Tracker** (local)
- **Kismet** (importación)
- **gpsbabel** (conversión a GPX/KML)

### 4. Documentación

Si necesitas documentar un wardrive, el CSV es el formato estándar.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Al aire libre:** el GPS necesita visibilidad de satélites.
- **Tamaño:** el log crece rápido. 1 hora = ~1 MB.
- **Formato:** el CSV debe tener el header correcto para ser aceptado por WiGLE.

---

## 🔗 Relacionado

- [Wardrive GPS](wardrive-gps.md) — versión desde el menú GPS
- [Wardrive](../wifi/sniffers/wardrive.md) — versión desde el menú WiFi
- [Export WigleWifi](../export/export-wiglewifi.md) — exportar
- [Wardrive Tracker](../../07-wardrive.md) — análisis del CSV
- [WiGLE](https://wigle.net/) — base de datos mundial
