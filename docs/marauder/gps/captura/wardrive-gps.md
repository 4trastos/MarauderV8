# 🛰️ Wardrive GPS

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Wardrive GPS** es la función **estrella** del módulo GPS. Combina el **escaneo WiFi** con la **geolocalización GPS** para crear un **mapa de redes** con coordenadas.

Es la misma función que **Wardrive** en el módulo WiFi, pero accesible desde el menú GPS. El resultado es un log en formato **WigleWifi CSV** que se puede subir a WiGLE o analizar con **Wardrive Tracker**.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Conecta el módulo GPS** al Marauder.
2. **Verifica el fix** con **GPS Info**: necesitas al menos **fix 3D**.
3. **Inserta la tarjeta SD** (FAT32) con las carpetas `/pcap` y `/logs`.

### Desde el menú del Marauder

1. Navega hasta **GPS → Captura → Wardrive GPS**.
2. Configura el **intervalo de escaneo** (por defecto: 1 segundo por canal).
3. Pulsa **Start**.
4. El Marauder empezará a:
   - Escanear los canales WiFi.
   - Registrar cada red nueva con SSID, BSSID, cifrado, canal, RSSI.
   - Asociar cada registro a las coordenadas GPS.
5. Muévete por la zona (coche, bici, caminando) para cubrir más terreno.
6. Pulsa **Stop** cuando termines.
7. El log se guarda en `/logs/wardrive_XXXX.csv`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Intervalo** | Tiempo por canal | 1 segundo |
| **Canales** | Qué canales escanear | Todos |
| **Formato** | WigleWifi CSV | CSV |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Wardrive GPS ===
Archivo: /logs/wardrive_20261011_123456.csv
Fix: 3D (8 satélites)
Redes detectadas: 47
Tiempo: 00:15:30
Distancia: 2.3 km
```

### En la SD

Un archivo `.csv` en formato WigleWifi:

```text
MAC,SSID,AuthMode,FirstSeen,Channel,RSSI,CurrentLatitude,CurrentLongitude,AltitudeMeters,AccuracyMeters,Type
FA:8F:CA:61:05:78,MiFibra-BB6F,[WPA2-PSK-CCMP][ESS],2026-10-11 12:34:56,6,-67,40.4168,-3.7038,650,10,WIFI
00:1A:2B:3C:4D:5E,Movistar_5G,[WPA2-PSK-CCMP][WPS][ESS],2026-10-11 12:35:01,44,-72,40.4170,-3.7040,650,12,WIFI
...
```

---

## 🎯 Para qué sirve

### 1. Mapear redes WiFi

El caso de uso principal. **Wardrive GPS** te da un mapa de todas las redes de una zona con sus coordenadas.

### 2. Contribuir a WiGLE

WiGLE es la base de datos mundial de redes WiFi. Subir tus logs ayuda a la comunidad.

### 3. Auditoría de cobertura

Si quieres saber la cobertura de tu red WiFi en una zona, **Wardrive GPS** te lo dice.

### 4. Análisis de espectro

Si quieres saber la densidad de redes en una zona, **Wardrive GPS** te da los datos.

### 5. Base para Wardrive Tracker

El log CSV se puede analizar con **Wardrive Tracker** (mapa interactivo, filtros, detalles).

---

## 🎯 Diferencias con otras funciones

| Aspecto | Wardrive GPS | GPS Track Log | GPS Data Log |
|---|---|---|---|
| **Qué captura** | WiFi + GPS | Solo GPS | Solo GPS (NMEA) |
| **Formato** | WigleWifi CSV | GPX/KML | NMEA |
| **Uso** | WiGLE, mapas de redes | Recorrido | Debug |
| **Requiere WiFi** | Sí | No | No |

**En la práctica:**

- **Wardrive GPS**: para mapear redes.
- **GPS Track Log**: para mapear tu recorrido.
- **GPS Data Log**: