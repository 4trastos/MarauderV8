# 📡 Raw Capture

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Raw Capture** captura **TODO** el tráfico 802.11 que el Marauder recibe, sin filtros, sin clasificación, sin interpretación. Es un **volcado crudo** de todo lo que pasa por el aire en el canal actual.

El resultado es un archivo `.pcap` **gigante** que contiene:

- Beacons
- Probe requests/responses
- Authentication
- Association
- Data
- QoS Data
- EAPOL
- Deauth
- Tramas desconocidas o malformadas
- **Todo lo demás**

Es la herramienta **forense** del Marauder: cuando no sabes qué buscar, captura todo y analiza después.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada** (obligatorio, el pcap se guarda en la SD).
2. Navega hasta **WiFi → Sniffers → Raw Capture**.
3. Selecciona el **canal** donde quieres capturar.
4. Pulsa **Start**.
5. El Marauder empezará a escribir **todas** las tramas al pcap.
6. Pulsa **Stop** cuando termines.
7. El archivo se guarda en `/pcap/raw_XXXX.pcap`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal** | Canal donde capturar | Actual |
| **Duración** | Tiempo máximo de captura | Sin límite |
| **Tamaño máximo** | Tamaño máximo del pcap | 100 MB |
| **Filtro MAC** | Solo capturar de una MAC | Ninguno |

---

## 📊 Qué genera

### En pantalla

```text
=== Raw Capture ===
Canal: 6
Archivo: /pcap/raw_20261011_123456.pcap

Estado: Capturando...
Paquetes: 4521
Tamaño: 2.3 MB
Tiempo: 00:01:23

[Stop]
```

### En la SD

Un archivo `.pcap` que puede crecer **muy rápido**:

| Duración | Tamaño aproximado |
|---|---|
| 1 minuto | 1-5 MB |
| 10 minutos | 10-50 MB |
| 1 hora | 50-300 MB |
| 8 horas | 500 MB - 2 GB |

Depende de la densidad de tráfico en el canal.

---

## 🎯 Para qué sirve

### 1. Análisis forense

Cuando no sabes qué buscar, **Raw Capture** te da todo. Luego analizas en Wireshark/tshark:

- Buscar handshakes (`eapol`).
- Buscar deauths (`wlan.fc.type_subtype == 0x0c`).
- Buscar beacons de un SSID concreto.
- Buscar tráfico de una MAC específica.

### 2. Captura de handshakes "a ciegas"

Si no sabes en qué canal está la red o cuándo se conectan los clientes, **Raw Capture** captura todo. Luego, con `hcxpcapngtool`, extraes los handshakes:

```bash
hcxpcapngtool -o handshake.hc22000 raw_20261011_123456.pcap
```

### 3. Documentación de un incidente

Si tu red ha sufrido un ataque, **Raw Capture** te da el pcap completo para:

- Analizar el ataque.
- Documentar el incidente.
- Presentar como evidencia.

### 4. Investigación de protocolos

Si quieres estudiar cómo funciona 802.11 en tu zona:

- Qué tramas se emiten.
- Con qué frecuencia.
- Con qué campos.

**Raw Capture** es tu fuente de datos.

### 5. Base para análisis con `tshark`

Una vez tienes el pcap, puedes hacer análisis muy específicos:

```bash
# Ver todos los EAPOL
tshark -r raw.pcap -Y eapol

# Ver beacons de un SSID
tshark -r raw.pcap -Y "wlan.ssid == 'MiFibra-BB6F'"

# Ver deauths
tshark -r raw.pcap -Y "wlan.fc.type_subtype == 0x0c"

# Seguir un flujo TCP (si el tráfico está descifrado)
tshark -r raw.pcap -q -z follow,tcp,ascii,0
```

---

## 🎯 Diferencias con EAPOL/PMKID Scan

| Aspecto | Raw Capture | EAPOL/PMKID Scan |
|---|---|---|
| **Qué captura** | Todo | Solo EAPOL y PMKID |
| **Tamaño del pcap** | Grande (100 MB+) | Pequeño (< 1 MB) |
| **Velocidad** | Rápida (todo) | Rápida (filtrado) |
| **Análisis posterior** | Complejo (todo) | Directo (solo handshakes) |
| **Uso** | Forense, investigación | Captura dirigida |
| **Almacenamiento** | Mucho | Poco |

**En la práctica:**

- Si sabes qué buscas (handshake), usa **EAPOL/PMKID Scan**.
- Si no sabes qué buscas, usa **Raw Capture**.

---

## ⚠️ Advertencias

- **SD obligatoria:** sin SD, no hay dónde guardar el pcap.
- **Tamaño:** el pcap puede crecer **muy rápido**. En zonas densas, 100 MB en minutos.
- **Espacio libre:** verifica que tienes espacio en la SD antes de empezar.
- **Canal único:** solo captura el canal actual. Para más, cambia de canal manualmente.
- **Filtros:** aunque no filtra por tipo, algunos firmwares permiten filtrar por MAC. Úsalo si quieres reducir el tamaño.
- **Legalidad:** capturar TODO el tráfico de una zona es **zona gris legal**. En muchos países, es legal porque las emisiones son públicas. Pero **analizar** ese tráfico puede ser delito si incluye datos personales.
- **Almacenamiento:** los pcaps se acumulan. Limpia la SD periódicamente.
- **Velocidad de escritura:** si la SD es lenta, el Marauder puede perder paquetes. Usa una SD Clase 10 o superior.
- **Corrupción:** si apagas el Marauder sin parar la captura, el pcap puede corromperse. Usa **Stop** antes de apagar.

---

## 🔗 Relacionado

- [EAPOL/PMKID Scan](eapol-pmkid.md) — captura dirigida de handshakes
- [Beacon Sniff](beacon.md) — para inventariar redes antes de capturar
- [Scan AP/STA](scan-ap-sta.md) — para identificar objetivos
- [Packet Monitor](packet-monitor.md) — para ver qué hay antes de capturar todo
- [Guía de análisis con Wireshark](../../../04-handshake.md)
- [Guía de conversión a Hashcat](../../../05-wordlists.md)