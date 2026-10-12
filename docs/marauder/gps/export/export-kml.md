# 📤 Export KML

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Export KML** exporta el **recorrido** (o los datos GPS) a formato **KML** (*Keyhole Markup Language*). KML es el formato que usa **Google Earth** para mostrar datos geográficos.

Es ideal para:

- **Ver el recorrido** en Google Earth.
- **Visualizar** puntos de interés.
- **Compartir** mapas interactivos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **SD insertada**.
2. Navega hasta **GPS → Export → Export KML**.
3. Selecciona el **log** a exportar.
4. Pulsa **Export**.
5. El archivo se guarda en `/logs/track_XXXX.kml`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Log** | Log a exportar | Actual |
| **Formato** | KML | KML |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Export KML ===
Log: track_20261011_123456
Formato: KML

Exportando...
Archivo: /logs/track_20261011_123456.kml
Puntos: 1250
```

### En la SD

Un archivo `.kml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://www.opengis.net/kml/2.2">
  <Document>
    <name>Recorrido 2026-10-11</name>
    <Placemark>
      <name>Punto 1</name>
      <Point>
        <coordinates>-3.7038,40.4168,650</coordinates>
      </Point>
    </Placemark>
    ...
  </Document>
</kml>
```

---

## 🎯 Para qué sirve

### 1. Ver el recorrido en Google Earth

El KML se abre directamente en Google Earth. Puedes ver el recorrido en 3D.

### 2. Compartir mapas interactivos

Si quieres compartir un recorrido con alguien, el KML es un formato visual.

### 3. Análisis visual

Si quieres ver el recorrido sobre un mapa, el KML es ideal.

### 4. Documentación

Si necesitas documentar un recorrido, el KML es un formato visual.

---

## 🎯 Diferencias con GPX

| Aspecto | KML | GPX |
|---|---|---|
| **Uso** | Google Earth, visualización | Intercambio, apps deportivas |
| **Formato** | XML | XML |
| **Visualización** | Nativa en Google Earth | Requiere conversión |
| **Compatibilidad** | Google Earth, Maps | Strava, Garmin, Wikiloc |

**En la práctica:**

- **KML**: para ver en Google Earth.
- **GPX**: para apps deportivas.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Formato:** el KML debe tener el header correcto para ser aceptado.
- **Privacidad:** los recorridos pueden revelar información personal.

---

## 🔗 Relacionado

- [GPS Track Log](../captura/gps-track-log.md) — genera el recorrido
- [Export GPX](export-gpx.md) — formato alternativo
- [Export WigleWifi](export-wiglewifi.md) — formato para redes
- [Google Earth](https://earth.google.com/) — para visualizar KML
