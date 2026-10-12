# 🛰️ PPI-GPS Capture

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**PPI-GPS Capture** captura tráfico WiFi con **etiquetas PPI-GPS**. PPI (*Per-Packet Information*) es un formato de captura que incluye **metadatos adicionales** en cada paquete, incluyendo **coordenadas GPS**.

Es el formato que usan **Kismet** y **airodump-ng** con GPS. Los archivos `.pcap` resultantes se pueden analizar con **Wireshark** (que reconoce las etiquetas PPI-GPS).

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Conecta el módulo GPS** al Marauder.
2. **Verifica el fix** con **GPS Info**.
3. **Inserta la tarjeta SD**.

### Desde el menú del Marauder

1. Navega hasta **GPS → Captura → PPI-GPS Capture**.
2. Configura el **canal** donde capturar.
3. Pulsa **Start**.
4. El Marauder capturará tráfico WiFi con etiquetas PPI-GPS.
5. Pulsa **Stop** cuando termines.
6. El archivo se guarda en `/pcap/ppi_gps_XXXX.pcap`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal** | Canal donde capturar | 1 |
| **Duración** | Tiempo máximo | Sin límite |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== PPI-GPS Capture ===
Archivo: /pcap/ppi_gps_20261011_123456.pcap
Canal: 6
Paquetes: 4521
Tamaño: 3.5 MB
Tiempo: 00:15:30
```

### En la SD

Un archivo `.pcap` con etiquetas PPI-GPS. Se puede analizar con:

```bash
# Ver coordenadas GPS de cada paquete
tshark -r ppi_gps_20261011_123456.pcap -Y "ppi.geolocation" -T fields -e ppi.geolocation.latitude -e ppi.geolocation.longitude
```

---

## 🎯 Para qué sirve

### 1. Compatibilidad con Kismet

Si usas **Kismet** para análisis, el formato PPI-GPS es el estándar. Puedes importar los pcap en Kismet.

### 2. Análisis en Wireshark

Wireshark reconoce las etiquetas PPI-GPS y muestra las coordenadas de cada paquete.

### 3. Captura forense

Si necesitas documentar una captura con coordenadas, el PPI-GPS es el formato más completo.

### 4. Base para análisis avanzado

El PPI-GPS permite análisis más ricos que el WigleWifi CSV, porque incluye **todo el tráfico** con coordenadas, no solo las redes.

---

## 🎯 Diferencias con Wardrive GPS

| Aspecto | PPI-GPS Capture | Wardrive GPS |
|---|---|---|
| **Formato** | PCAP con PPI-GPS | WigleWifi CSV |
| **Contenido** | Todo el tráfico | Solo redes |
| **Tamaño** | Grande (MB) | Pequeño (KB) |
| **Compatibilidad** | Kismet, Wireshark | WiGLE, Wardrive Tracker |
| **Uso** | Forense, análisis | WiGLE, mapas |
| **Velocidad** | Media | Rápida |

**En la práctica:**

- **PPI-GPS**: para análisis forense y Kismet.
- **Wardrive GPS**: para WiGLE y mapas.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar.
- **Tamaño:** el pcap puede crecer muy rápido. 1 hora = 50-200 MB.
- **Al aire libre:** el GPS necesita visibilidad de satélites.
- **Compatibilidad:** no todas las herramientas leen PPI-GPS. Wireshark y Kismet sí.
- **Canal único:** solo captura el canal actual.

---

## 🔗 Relacionado

- [Wardrive GPS](wardrive-gps.md) — formato WigleWifi CSV
- [WigleWifi Log](wiglewifi-log.md) — formato WigleWifi CSV
- [Raw Capture](../wifi/sniffers/raw-capture.md) — captura todo el tráfico
- [Kismet](https://www.kismetwireless.net/) — herramienta de análisis
