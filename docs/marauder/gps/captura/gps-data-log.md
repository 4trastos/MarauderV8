# 🛰️ GPS Data Log

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Data Log** registra las **sentencias NMEA del GPS** en un archivo de la tarjeta SD. A diferencia de **GPS Data** (que solo muestra en pantalla), este guarda los datos para análisis posterior.

Es útil para:

- **Análisis en PC** con herramientas como `gpsbabel`.
- **Debug** de problemas de GPS.
- **Documentación** de un recorrido.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado** y la **SD insertada**.
2. Navega hasta **GPS → Captura → GPS Data Log**.
3. Pulsa **Start**.
4. El Marauder empezará a guardar las sentencias NMEA.
5. Pulsa **Stop** cuando termines.
6. El archivo se guarda en `/logs/gps_XXXX.nmea`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Formato** | NMEA, GPX, KML | NMEA |
| **Intervalo** | Frecuencia de guardado | 1 segundo |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Data Log ===
Archivo: /logs/gps_20261011_123456.nmea
Estado: Grabando...
Líneas: 1250
Tamaño: 250 KB
Tiempo: 00:20:50
```

### En la SD

Un archivo `.nmea`:

```text
$GPGGA,123501.00,4016.808,N,00342.228,W,1,08,1.2,650.0,M,,,,*4A
$GPGSA,A,3,01,02,03,04,05,06,07,08,,,,,1.5,1.2,2.0*3B
$GPRMC,123501.00,A,4016.808,N,00342.228,W,0.5,0.0,111026,,,A*6F
...
```

### Análisis en PC

```bash
# Convertir NMEA a GPX
gpsbabel -i nmea -f gps_20261011_123456.nmea -o gpx -F recorrido.gpx

# Ver el recorrido en Google Earth
gpsbabel -i nmea -f gps_20261011_123456.nmea -o kml -F recorrido.kml
```

---

## 🎯 Para qué sirve

### 1. Análisis de recorrido

Si quieres ver por dónde has pasado, **GPS Data Log** te da el recorrido completo.

### 2. Debug de GPS

Si el GPS da problemas, el log te permite analizar los datos en detalle.

### 3. Documentación

Si necesitas documentar un recorrido (para una auditoría, un informe), **GPS Data Log** te da la evidencia.

### 4. Base para GPX/KML

Puedes convertir el log a GPX o KML para verlo en mapas.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Tamaño:** el log crece rápido (1 sentencia por segundo). 1 hora = ~1 MB.
- **Al aire libre:** el GPS necesita visibilidad de satélites.
- **Formato:** NMEA es el formato estándar, pero algunos firmwares guardan en otros formatos.

---

## 🔗 Relacionado

- [GPS Data](gps-data.md) — versión en pantalla
- [Wardrive GPS](wardrive-gps.md) — wardriving con WiFi
- [GPS Track Log](gps-track-log.md) — solo el recorrido
- [Export GPX](../export/export-gpx.md) — convertir a GPX
