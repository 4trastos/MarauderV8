# 📡 Beacon Sniff

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Beacon Sniff** captura las **tramas de baliza** (beacons) que emiten todos los Puntos de Acceso a su alrededor. Un beacon es un "anuncio" que cada AP emite típicamente **10 veces por segundo** para anunciar su presencia y sus capacidades.

Es la herramienta **más básica y fundamental** del Marauder: **el primer paso de cualquier auditoría WiFi**. Antes de capturar handshakes o atacar una red, necesitas saber **qué redes hay, en qué canal y con qué cifrado**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada** (opcional, pero recomendable para guardar logs).
2. Navega hasta **WiFi → Sniffers → Beacon Sniff**.
3. Pulsa **Start**.
4. El Marauder empezará a escuchar todos los canales (1-13 en 2.4 GHz, 36-165 en 5 GHz) y a registrar cada beacon que reciba.
5. Verás en pantalla una lista creciente con:
   - **SSID** (nombre de la red)
   - **BSSID** (MAC del AP)
   - **Canal**
   - **Cifrado** (Open, WEP, WPA, WPA2, WPA3)
   - **RSSI** (intensidad de señal)
6. Pulsa **Stop** cuando tengas la lista que buscas.

### Guardar los resultados

Si tienes la SD insertada, al pulsar **Stop** el Marauder te ofrecerá guardar los resultados en `/logs/beacon_XXXX.txt`.

### Desde la línea de comandos (opcional)

```bash
# Capturar beacons durante 30 segundos
python3 marauder_cli.py --beacon --duration 30 --output beacons.txt
```

---

## 📊 Qué genera

### En pantalla

Una lista en tiempo real:

```text
SSID                    BSSID               CH  ENC   RSSI
MiFibra-BB6F            FA:8F:CA:61:05:78   6   WPA2  -67
Movistar_5G             00:1A:2B:3C:4D:5E   44  WPA2  -72
Vodafone-2.4G           3C:5A:B4:12:34:56   1   WPA2  -58
FreeWiFi                8C:1A:BF:9D:8E:7F   11  Open  -80
```

### En la SD (si guardas)

Un archivo `.txt` en `/logs/beacon_XXXX.txt` con formato tabulado:

```text
SSID                    BSSID               Channel  Encryption  RSSI  FirstSeen  LastSeen
MiFibra-BB6F            FA:8F:CA:61:05:78   6        WPA2        -67   12:34:56   12:35:12
Movistar_5G             00:1A:2B:3C:4D:5E   44       WPA2        -72   12:34:57   12:35:15
...
```

### Si además tienes GPS

Si el módulo GPS está conectado y con fix, el log puede incluir coordenadas:

```text
SSID,BSSID,Channel,Encryption,RSSI,Latitude,Longitude,Altitude
MiFibra-BB6F,FA:8F:CA:61:05:78,6,WPA2,-67,40.4168,-3.7038,650
```

---

## 🎯 Para qué sirve

### 1. Inventario de redes

Es la forma más rápida de saber **qué redes hay en tu zona**. Útil para:

- Elegir el canal menos saturado para tu propio router.
- Detectar redes ocultas o no autorizadas.
- Hacer un mapa del espectro WiFi de una ubicación.

### 2. Preparación para capturar handshakes

Antes de capturar un handshake, necesitas saber:

- **En qué canal está el AP** (para no perder paquetes).
- **El BSSID del AP** (para filtros en Wireshark).
- **El tipo de cifrado** (WPA2 se puede crackear, WPA3 no de la misma forma).
- **Si hay clientes conectados** (para saber si merece la pena forzar un deauth).

### 3. Análisis de saturación

Si ves muchos APs en el mismo canal, sabrás que ese canal está saturado. Útil para:

- Elegir el mejor canal para tu router.
- Diagnosticar problemas de WiFi lento.

### 4. Detección de anomalías

Beacons con SSID sospechosos (tipo `FreeWiFi`, `WiFi_Gratis`, `HackMe`) pueden ser **APs maliciosos** esperando que te conectes. **Beacon Sniff** te los muestra.

---

## 🎯 Diferencias con Scan AP/STA

| Aspecto | Beacon Sniff | Scan AP/STA |
|---|---|---|
| **Tipo** | Pasivo (solo escucha) | Activo (envía probes) |
| **Velocidad** | Instantáneo | Más lento (espera respuestas) |
| **Datos** | SSID, BSSID, canal, cifrado | Igual + clientes conectados |
| **Clientes** | No los muestra | Sí los muestra |
| **Uso** | Inventario rápido | Análisis completo |

**En la práctica:** empieza con **Beacon Sniff** para ver qué hay, y luego usa **Scan AP/STA** si necesitas detalles de clientes.

---

## ⚠️ Advertencias

- **Legalidad:** escuchar beacons es **pasivo** y legal en la mayoría de países. Los beacons son emisiones públicas del AP.
- **Canal:** si tienes el Marauder en un solo canal, solo verás los APs de ese canal. Para ver todos, necesita escanear todos los canales secuencialmente.
- **Tiempo:** en zonas con muchas redes (edificios, centros comerciales), la lista puede crecer a cientos de entradas en segundos.
- **SSID ocultos:** algunos APs ocultan su SSID. Aparecerán con SSID vacío o `<hidden>`. No es un error, es una configuración del AP.
- **SSID duplicados:** varios APs pueden emitir el mismo SSID (mesh, repetidores). Fíjate en el BSSID para distinguirlos.
- **Almacenamiento:** en zonas muy densas, el log puede crecer rápido. Un beacon sniff de 1 hora puede generar 1-5 MB.

---

## 🔗 Relacionado

- [EAPOL/PMKID Scan](eapol-pmkid.md) — el siguiente paso tras identificar una red
- [Scan AP/STA](scan-ap-sta.md) — variante activa que muestra clientes
- [Probe Request Sniff](probe-request.md) — para ver qué buscan los clientes
- [Channel Analyzer](channel-analyzer.md) — para analizar saturación por canal
- [Wardrive](wardrive.md) — combina beacons con GPS para mapear
- [Detect MultiSSID](detect-multissid.md) — para detectar APs sospechosos con múltiples SSID