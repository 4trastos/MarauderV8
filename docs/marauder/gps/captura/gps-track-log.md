# 🛰️ GPS Track Log

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Track Log** registra **solo tu recorrido** (posición, hora, altitud, velocidad), **sin capturar redes WiFi ni BLE**. Es útil para:

- **Documentar** un recorrido (senderismo, bici, coche).
- **Crear** archivos GPX/KML para mapas.
- **Medir** distancia y velocidad.
- **Base para análisis** de movimiento.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Conecta el módulo GPS** al Marauder.
2. **Verifica el fix** con **GPS Info**.
3. **Inserta la tarjeta SD**.

### Desde el menú del Marauder

1. Navega hasta **GPS → Captura → GPS Track Log**.
2. Pulsa **Start**.
3. El Marauder empezará a registrar tu posición.
4. Muévete por la zona.
5. Pulsa **Stop** cuando termines.
6. El archivo se guarda en `/logs/track_XXXX.gpx`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Formato** | GPX, KML, NMEA | GPX |
| **Intervalo** | Frecuencia de guardado | 1 segundo |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Track Log ===
Archivo: /logs/track_20261011_123456.gpx
Fix: 3D (8 satélites)
Puntos: 1250
Distancia: 2.3 km
Velocidad media: 5.2 km/h
Tiempo: 00:26:30
```

### En la SD

Un archivo `.gpx`:

```xml
<?xml version="1.0"?>
<gpx version="1.1">
  <trk>
    <name>Recorrido 2026-10-11</name>
    <trkseg>
      <trkpt lat="40.4168" lon="-3.7038">
        <ele>650</ele>
        <time>2026-10-11T12:34:56Z</time>
      </trkpt>
      <trkpt lat="40.4169" lon="-3.7039">
        <ele>651</ele>
        <time>2026-10-11T12:34:57Z</time>
      </trkpt>
      ...
    </trkseg>
  </trk>
</gpx>
```

### Análisis en PC

```bash
# Ver el recorrido en Google Earth
gpsbabel -i gpx -f track_20261011_123456.gpx -o kml -F recorrido.kml

# Ver estadísticas
gpsbabel -i gpx -f track_20261011_123456.gpx -o unicsv -F stats.csv
```

---

## 🎯 Para qué sirve

### 1. Documentar un recorrido

Si haces senderismo, bici o coche, **GPS Track Log** te guarda el recorrido.

### 2. Crear archivos GPX/KML

El archivo GPX se puede cargar en:

- Google Earth
- Strava
- Wikiloc
- Garmin Connect
- Cualquier app de mapas

### 3. Medir distancia y velocidad

El log incluye distancia y velocidad media, útil para deporte.

### 4. Base para análisis

Si quieres analizar tus patrones de movimiento, **GPS Track Log** te da los datos.

---

## 🎯 Diferencias con Wardrive GPS

| Aspecto | GPS Track Log | Wardrive GPS |
|---|---|---|
| **Qué captura** | Solo GPS | WiFi + GPS |
| **Formato** | GPX/KML/NMEA | WigleWifi CSV |
| **Uso** | Recorrido | Mapa de redes |
| **Requiere WiFi** | No | Sí |
| **Tamaño** | Pequeño | Grande |

**En la práctica:**

- **GPS Track Log**: para mapear tu recorrido.
- **Wardrive GPS**: para mapear redes.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Al aire libre:** el GPS necesita visibilidad de satélites.
- **Tamaño:** el log crece rápido. 1 hora = ~1 MB (GPX).
- **Batería:** el GPS consume energía. Un recorrido largo agota la batería del Marauder.

---

## 🔗 Relacionado

- [GPS Data Log](gps-data-log.md) — versión NMEA
- [Wardrive GPS](wardrive-gps.md) — versión con WiFi
- [Export GPX](../export/export-gpx.md) — exportar a GPX
- [Export KML](../export/export-kml.md) — exportar a KML
