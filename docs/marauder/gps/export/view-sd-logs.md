# 📤 View SD Logs

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**View SD Logs** lista **todos los logs GPS** guardados en la tarjeta SD. Puedes ver:

- **Nombre** del archivo.
- **Tipo** (NMEA, GPX, KML, CSV).
- **Tamaño**.
- **Fecha** de creación.
- **Número de puntos/redes**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **SD insertada**.
2. Navega hasta **GPS → Export → View SD Logs**.
3. Verás la lista de logs.
4. Selecciona uno para ver detalles.
5. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Filtro** | Filtrar por tipo | Ninguno |
| **Orden** | Por fecha, nombre, tamaño | Fecha |

---

## 📊 Qué genera

### En pantalla

```text
=== View SD Logs ===
Logs encontrados: 5

Nombre                          Tipo    Tamaño   Fecha
wardrive_20261011_123456.csv    CSV     1.2 MB   11/10 12:34
track_20261011_134512.gpx       GPX     250 KB   11/10 13:45
gps_20261011_140123.nmea        NMEA    180 KB   11/10 14:01
wigle_20261011_150234.csv       CSV     2.1 MB   11/10 15:02
track_20261011_160345.kml       KML     320 KB   11/10 16:03
```

No genera archivos. Solo muestra la lista.

---

## 🎯 Para qué sirve

### 1. Ver qué logs tienes

Si has hecho varias capturas, **View SD Logs** te lista todas.

### 2. Gestión de espacio

Si la SD se está llenando, aquí ves qué logs ocupan más.

### 3. Seleccionar para exportar

Antes de exportar un log, **View SD Logs** te ayuda a encontrarlo.

### 4. Documentación

Si necesitas documentar qué capturas has hecho, **View SD Logs** te da la lista.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay logs que listar.
- **Formato:** los logs se listan por tipo (CSV, GPX, KML, NMEA).
- **Espacio:** si la SD está llena, no podrás guardar más logs.

---

## 🔗 Relacionado

- [Delete GPS Logs](delete-gps-logs.md) — borra logs
- [Export WigleWifi](export-wiglewifi.md) — exporta a CSV
- [Export GPX](export-gpx.md) — exporta a GPX
- [Export KML](export-kml.md) — exporta a KML