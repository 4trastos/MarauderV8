# 📡 Scan AP/STA

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Scan AP/STA** es un escaneo **activo** que descubre tanto **Puntos de Acceso (AP)** como **Estaciones (STA)** — es decir, los clientes conectados a cada AP. A diferencia de **Beacon Sniff** (que solo escucha), este envía **probe requests** y espera respuestas, obteniendo información más completa y detallada.

Es la herramienta clave para **identificar objetivos** antes de un deauth o una captura de handshake. Sin saber qué clientes hay conectados, no puedes forzar una reconexión dirigida.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada** (recomendable).
2. Navega hasta **WiFi → Sniffers → Scan AP/STA**.
3. Pulsa **Start**.
4. El Marauder escaneará secuencialmente todos los canales y mostrará dos listas:
   - **APs**: SSID, BSSID, canal, cifrado, RSSI.
   - **STAs**: MAC del cliente, AP al que está conectado, RSSI.
5. Pulsa **Stop** cuando tengas lo que buscas.
6. Si tienes SD, se guarda en `/logs/scan_ap_sta_XXXX.txt`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canales** | Qué canales escanear | 1-13 (2.4 GHz) |
| **Duración por canal** | Tiempo en cada canal | 300 ms |
| **Modo** | AP, STA o ambos | Ambos |
| **Guardar** | Guardar en SD | Sí (si hay SD) |

---

## 📊 Qué genera

### En pantalla

```text
=== APs ===
SSID                    BSSID               CH  ENC   RSSI  Clients
MiFibra-BB6F            FA:8F:CA:61:05:78   6   WPA2  -67   3
Movistar_5G             00:1A:2B:3C:4D:5E   44  WPA2  -72   1
Vodafone-2.4G           3C:5A:B4:12:34:56   1   WPA2  -58   0
FreeWiFi                8C:1A:BF:9D:8E:7F   11  Open  -80   2

=== STAs (clientes) ===
MAC                 AP (BSSID)              RSSI  LastSeen
3C:5A:B4:12:34:56   FA:8F:CA:61:05:78       -65   12:35:01
A4:83:E7:11:22:33   FA:8F:CA:61:05:78       -70   12:35:03
F0:18:98:AA:BB:CC   00:1A:2B:3C:4D:5E       -68   12:35:05
...
```

### En la SD

Dos archivos `.txt`:

```text
/logs/scan_ap_XXXX.txt
/logs/scan_sta_XXXX.txt
```

O un único archivo con secciones, según el firmware.

### Si además tienes GPS

Si el módulo GPS está conectado, el log incluye coordenadas:

```text
SSID,BSSID,Channel,Encryption,RSSI,Latitude,Longitude,Clients
MiFibra-BB6F,FA:8F:CA:61:05:78,6,WPA2,-67,40.4168,-3.7038,3
```

---

## 🎯 Para qué sirve

### 1. Identificar clientes para deauth

El caso de uso principal. Antes de lanzar un **Deauth Targeted**, necesitas:

- El **BSSID del AP**.
- La **MAC del cliente** al que quieres desautenticar.
- El **canal** donde están ambos.

**Scan AP/STA** te da los tres datos en una sola pasada.

### 2. Inventario completo de la red

A diferencia de **Beacon Sniff**, este scan te muestra:

- Qué APs hay.
- Cuántos clientes tiene cada AP.
- Qué clientes están conectados a qué AP.

Útil para:
- Auditorías de red.
- Detectar clientes no autorizados.
- Ver la densidad de dispositivos en una zona.

### 3. Detectar clientes ocultos

Algunos clientes no emiten probe requests (modo pasivo). **Scan AP/STA** puede detectarlos indirectamente:

- Si ves tráfico asociado a un BSSID, hay clientes.
- Si no ves el cliente, puede ser que esté en modo pasivo o aleatorizando su MAC.

### 4. Preparar un ataque dirigido

| Ataque | Qué necesitas de Scan AP/STA |
|---|---|
| **Deauth Targeted** | BSSID del AP + MAC del cliente + canal |
| **Evil Portal** | BSSID del AP + canal |
| **Karma** | SSID del AP + canal |
| **AP Clone Spam** | BSSID del AP + SSID + canal |
| **EAPOL/PMKID Scan** | BSSID del AP + canal + cliente activo |

---

## 🎯 Diferencias con Beacon Sniff

| Aspecto | Scan AP/STA | Beacon Sniff |
|---|---|---|
| **Tipo** | Activo (envía probes) | Pasivo (solo escucha) |
| **Velocidad** | Más lento (espera respuestas) | Instantáneo |
| **Clientes** | **Sí los muestra** | No los muestra |
| **Datos** | SSID, BSSID, canal, cifrado, **clientes** | SSID, BSSID, canal, cifrado |
| **Uso** | Análisis completo | Inventario rápido |
| **Detección** | Puede ser detectado por el AP | Indetectable |

**En la práctica:**

1. Empieza con **Beacon Sniff** para ver qué hay (rápido, pasivo).
2. Luego **Scan AP/STA** para ver los clientes (más lento, activo).
3. Con esa info, lanza **Deauth Targeted** + **EAPOL/PMKID Scan**.

---

## ⚠️ Advertencias

- **Legalidad:** el escaneo activo (enviar probes) puede ser detectado por el AP. En redes ajenas, es **zona gris legal**. En tu propia red, sin problema.
- **Ruido:** en zonas muy saturadas, el scan puede tardar más y dar resultados incompletos.
- **MACs aleatorias:** muchos móviles modernos usan **MAC randomization**. Verás MACs que empiezan por `FA`, `F2`, `F6`, etc. (bit local asignado a 1). Es normal, no es un error.
- **Clientes ocultos:** los clientes en modo pasivo o con power save pueden no aparecer.
- **Tiempo:** un scan completo de 2.4 GHz + 5 GHz puede tardar 30-60 segundos.
- **Almacenamiento:** en zonas densas, el log puede crecer rápido.
- **Detección:** algunos APs con **WIDS/WIPS** (sistemas de detección de intrusiones) pueden alertar al administrador si detectan probes anómalos.

---

## 🔗 Relacionado

- [Beacon Sniff](beacon.md) — versión pasiva, más rápida
- [EAPOL/PMKID Scan](eapol-pmkid.md) — siguiente paso tras identificar objetivos
- [Deauth Targeted](../attacks/deauth-targeted.md) — ataque que usa los datos de este scan
- [Probe Request Sniff](probe-request.md) — para ver qué buscan los clientes
- [Wardrive](wardrive.md) — variante con GPS para mapear