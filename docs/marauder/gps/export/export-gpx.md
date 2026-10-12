# 📤 Export GPX

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Export GPX** exporta el **recorrido** (o los datos GPS) a formato **GPX** (*GPS Exchange Format*). GPX es un formato XML estándar para intercambiar datos GPS entre aplicaciones.

Es el formato que aceptan:

- Google Earth
- Strava
- Wikiloc
- Garmin Connect
- Cualquier app de mapas

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **SD insertada**.
2. Navega hasta **GPS → Export → Export GPX**.
3. Selecciona el **log** a exportar.
4. Pulsa **Export**.
5. El archivo se guarda en `/logs/track_XXXX.gpx`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Log** | Log a exportar | Actual |
| **Formato** | GPX | GPX |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Export GPX ===
Log: track_20261011_123456
Formato: GPX

Exportando...
Archivo: /logs/track_20261011_123456.gpx
Puntos: 1250
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
      ...
    </trkseg>
  </trk>
</gpx>
```

---

## 🎯 Para qué sirve

### 1. Ver el recorrido en mapas

El GPX se puede cargar en Google Earth, Strava, Wikiloc, etc.

### 2. Compartir recorridos

Si quieres compartir un recorrido con alguien, el GPX es el formato estándar.

### 3. Análisis deportivo

Si haces deporte, el GPX se puede importar en apps como Strava o Garmin Connect.

### 4. Documentación

Si necesitas documentar un recorrido, el GPX es el formato estándar.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Formato:** el GPX debe tener el header correcto para ser aceptado.
- **Privacidad:** los recorridos pueden revelar información personal (dónde vives, dónde trabajas). No los compartas sin cuidado.

---

## 🔗 Relacionado

- [GPS Track Log](../captura/gps-track-log.md) — genera el recorrido
- [Export KML](export-kml.md) — formato alternativo
- [Export WigleWifi](export-wiglewifi.md) — formato para redes
- [GPSBabel](https://www.gpsbabel.org/) — conversión entre formatos
