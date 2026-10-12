# 🛰️ GPS — Menú completo del Marauder v8

[⬅️ Volver al índice Marauder](../README.md)

---

Guía completa de las funciones GPS del ESP32 Marauder v8.

El módulo GPS permite **geolocalizar** todas las capturas del Marauder: redes WiFi, dispositivos Bluetooth y eventos de auditoría. Se usa principalmente para **wardriving** (mapear redes con coordenadas) y para generar logs compatibles con **WiGLE**.

> ⚠️ **Nota importante:** El ESP32 Marauder **no incluye GPS integrado**. Necesitas un **módulo GPS externo** conectado por UART (típicamente un NEO-6M, NEO-M8N o similar) para usar estas funciones.

## 📑 Índice

- [🔍 Info y estado](#-info-y-estado)
- [📡 Captura](#-captura)
- [⚙️ Configuración](#️-configuración)
- [📤 Exportación](#-exportación)

---

## 🔍 Info y estado

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **GPS Info** | Muestra información del módulo GPS: satélites visibles, fix actual, coordenadas, altitud. | [info/gps-info.md](info/gps-info.md) |
| 2 | **GPS Data** | Muestra datos en bruto del GPS (sentencias NMEA). | [info/gps-data.md](info/gps-data.md) |
| 3 | **GPS Status** | Estado del fix: sin fix, fix 2D, fix 3D, DGPS. | [info/gps-status.md](info/gps-status.md) |
| 4 | **Satellite View** | Vista gráfica de los satélites visibles y su intensidad de señal. | [info/satellite-view.md](info/satellite-view.md) |
| 5 | **GPS Baud Rate** | Configura la velocidad de comunicación con el módulo GPS. | [info/gps-baud-rate.md](info/gps-baud-rate.md) |

---

## 📡 Captura

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **GPS Data Log** | Registra los datos GPS en un archivo de la SD. | [captura/gps-data-log.md](captura/gps-data-log.md) |
| 2 | **Wardrive GPS** | Wardriving completo: escanea redes WiFi y las asocia a coordenadas GPS. | [captura/wardrive-gps.md](captura/wardrive-gps.md) |
| 3 | **WigleWifi Log** | Genera un log en formato **WigleWifi CSV** listo para subir a WiGLE. | [captura/wiglewifi-log.md](captura/wiglewifi-log.md) |
| 4 | **PPI-GPS Capture** | Captura WiFi con etiquetas **PPI-GPS** (compatible con Kismet, airodump-ng). | [captura/ppi-gps-capture.md](captura/ppi-gps-capture.md) |
| 5 | **GPS Track Log** | Registra solo tu recorrido (sin capturar redes). Útil para trackear rutas. | [captura/gps-track-log.md](captura/gps-track-log.md) |

---

## ⚙️ Configuración

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **GPS Enable** | Activa el módulo GPS. | [config/gps-enable.md](config/gps-enable.md) |
| 2 | **GPS Disable** | Desactiva el módulo GPS (ahorra batería). | [config/gps-disable.md](config/gps-disable.md) |
| 3 | **Set GPS Pins** | Configura los pines GPIO usados para RX/TX del GPS. | [config/set-gps-pins.md](config/set-gps-pins.md) |
| 4 | **GPS Time Sync** | Sincroniza el reloj del Marauder con la hora del GPS. | [config/gps-time-sync.md](config/gps-time-sync.md) |
| 5 | **GPS Datum** | Cambia el datum geodésico (WGS84 por defecto). | [config/gps-datum.md](config/gps-datum.md) |
| 6 | **GPS Update Rate** | Configura la frecuencia de actualización del GPS (1Hz, 5Hz, 10Hz). | [config/gps-update-rate.md](config/gps-update-rate.md) |

---

## 📤 Exportación

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **Export WigleWifi** | Exporta el log actual a formato WigleWifi CSV. | [export/export-wiglewifi.md](export/export-wiglewifi.md) |
| 2 | **Export GPX** | Exporta el recorrido a formato GPX (compatible con Google Maps, Strava, etc.). | [export/export-gpx.md](export/export-gpx.md) |
| 3 | **Export KML** | Exporta a formato KML (Google Earth). | [export/export-kml.md](export/export-kml.md) |
| 4 | **View SD Logs** | Lista los logs GPS guardados en la SD. | [export/view-sd-logs.md](export/view-sd-logs.md) |
| 5 | **Delete GPS Logs** | Borra los logs GPS de la SD. | [export/delete-gps-logs.md](export/delete-gps-logs.md) |


---

## 🛰️ Cómo conectar un GPS externo al Marauder

El Marauder usa UART para comunicarse con el GPS. La conexión típica es:

| Marauder | GPS (NEO-6M) |
|---|---|
| GPIO 16 (RX2) | TX del GPS |
| GPIO 17 (TX2) | RX del GPS |
| 3.3V | VCC |
| GND | GND |

> ⚠️ **Verifica el voltaje de tu módulo GPS.** Algunos módulos NEO-6M funcionan a 5V y otros a 3.3V. Alimentar un módulo de 3.3V con 5V lo puede quemar.

---

## 📤 Formato WigleWifi CSV

El formato **WigleWifi CSV** es el estándar de facto para wardriving. Contiene columnas como:

```
MAC,SSID,AuthMode,FirstSeen,Channel,RSSI,CurrentLatitude,CurrentLongitude,AltitudeMeters,AccuracyMeters,Type
```

Este formato lo aceptan:

- **WiGLE** (base de datos mundial de redes WiFi)
- **Wardrive Tracker** (el proyecto que ya has documentado)
- **Kismet**
- Cualquier herramienta de análisis de wardriving

---

## ⚠️ Uso legal

El **wardriving** (registrar redes con coordenadas) es legal en muchos países siempre que:

- **No te conectes** a las redes ajenas
- **No inyectes tráfico** en ellas
- **No las ataques** de ninguna forma

Pero en algunas jurisdicciones, incluso el simple registro puede ser considerado invasión de la privacidad. Infórmate de la legislación local antes de hacer wardriving en zonas públicas.

En España:

- Registrar SSIDs y MACs con GPS: **zona gris legal**
- Conectarse a redes abiertas sin permiso: **ilegal**
- Atacar redes: **delito** (art. 197 bis y 264 CP)

**Wardriving responsable**: usa solo para mapear y contribuir a WiGLE, nunca para atacar.

---

## 🔗 Recursos relacionados

- [Repositorio oficial del ESP32 Marauder](https://github.com/justcallmekoko/ESP32Marauder)
- [Wiki oficial — GPS](https://github.com/justcallmekoko/ESP32Marauder/wiki/GPS)
- [WiGLE — Base de datos mundial de redes WiFi](https://wigle.net/)
- [Wardrive Tracker](../wifi/wardrive.md)
- [Guía NIST de auditoría WiFi](../README.md)