# 📡 Probe Request Sniff

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Probe Request Sniff** captura las **tramas de solicitud de sondeo** (probe requests) que emiten los dispositivos cliente (móviles, portátiles, tablets) cuando **buscan redes conocidas**. A diferencia de los beacons (que emiten los AP), los probe requests los emiten los **clientes**.

Es una herramienta **pasiva** que revela información muy valiosa sobre los dispositivos de tu entorno:

- **Qué redes buscan** (SSIDs de su lista de redes guardadas).
- **Qué dispositivos hay** (MACs, aunque muchas están aleatorizadas).
- **Dónde están** (RSSI, y con GPS, coordenadas).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada**.
2. Navega hasta **WiFi → Sniffers → Probe Request Sniff**.
3. Pulsa **Start**.
4. El Marauder escuchará todos los canales y registrará cada probe request que reciba.
5. Verás en pantalla:
   - **MAC del cliente** (o MAC aleatoria)
   - **SSID buscado**
   - **RSSI**
   - **Canal**
6. Pulsa **Stop** cuando tengas lo que buscas.
7. Si tienes SD, se guarda en `/logs/probe_XXXX.txt`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canales** | Qué canales escuchar | Todos |
| **Filtro SSID** | Solo capturar probes de un SSID concreto | Ninguno |
| **Filtro MAC** | Solo capturar probes de una MAC concreta | Ninguno |

---

## 📊 Qué genera

### En pantalla

```text
MAC                 SSID                    CH  RSSI
3C:5A:B4:12:34:56   MiFibra-BB6F            6   -65
A4:83:E7:11:22:33   Movistar_5G             44  -70
F0:18:98:AA:BB:CC   (wildcard)              1   -75
8C:1A:BF:9D:8E:7F   Vodafone-2.4G           6   -68
FA:8F:CA:61:05:78   FreeWiFi                11  -80
...
```

**Tipos de probe request:**

- **Dirigido**: el cliente busca un SSID concreto (`MiFibra-BB6F`).
- **Wildcard**: el cliente busca cualquier red (`(wildcard)` o SSID vacío). Típico de escaneos activos.
- **Broadcast**: el cliente busca una red con SSID oculto.

### En la SD

Un archivo `.txt`:

```text
MAC                 SSID                    Channel  RSSI  Timestamp
3C:5A:B4:12:34:56   MiFibra-BB6F            6        -65   12:35:01
A4:83:E7:11:22:33   Movistar_5G             44       -70   12:35:03
...
```

### Si además tienes GPS

```text
MAC,SSID,Channel,RSSI,Latitude,Longitude
3C:5A:B4:12:34:56,MiFibra-BB6F,6,-65,40.4168,-3.7038
```

Esto te permite **mapear dispositivos** y sus redes guardadas.

---

## 🎯 Para qué sirve

### 1. Descubrir redes ocultas

Si un cliente busca un SSID que no ves en los beacons, es que esa red:

- Está **oculta** (no emite beacons con SSID).
- Está **fuera de rango** pero el cliente la tiene guardada.
- Es una **red antigua** a la que el cliente se conectó hace tiempo.

**Probe Request Sniff** te revela esos SSIDs ocultos.

### 2. Inventario de dispositivos

Cada probe request viene de una MAC. Aunque muchas son aleatorias, algunas son **MACs reales** de fabricante. Puedes:

- Identificar fabricantes por OUI (con `Wireshark` o `tshark`).
- Ver cuántos dispositivos hay en la zona.
- Rastrear dispositivos específicos.

### 3. Análisis de comportamiento

Los probe requests revelan patrones:

- Un móvil que busca `MiFibra-BB6F` cada 30 segundos → está en tu casa, con la red guardada.
- Un dispositivo que busca 20 SSIDs distintos → ha viajado mucho.
- Un dispositivo que busca `(wildcard)` constantemente → está escaneando activamente.

### 4. Base para ataques Karma / Evil Portal

Los ataques **Karma** y **Evil Portal** se basan en **responder a los probe requests** con el SSID que el cliente busca. Sin esta información, no sabes qué SSID usar para atraer al cliente.

### 5. Detección de Pwnagotchi / Pineapple

Los Pwnagotchi emiten probe requests muy específicos. **Detect Pwnagotchi** usa esta misma lógica.

---

## 🎯 Diferencias con Beacon Sniff

| Aspecto | Probe Request Sniff | Beacon Sniff |
|---|---|---|
| **Emisor** | Clientes (móviles, portátiles) | APs (routers) |
| **Dirección** | Cliente → AP | AP → broadcast |
| **Info** | Redes que busca el cliente | Redes que existen |
| **MAC** | MAC del cliente (a menudo aleatoria) | BSSID del AP (real) |
| **Uso** | Inventario de dispositivos | Inventario de redes |
| **Legalidad** | Zona gris (revela privacidad) | Legal (emisiones públicas) |

**En la práctica:** combínalos. **Beacon Sniff** te dice qué redes hay. **Probe Request Sniff** te dice qué dispositivos hay y qué buscan.

---

## ⚠️ Advertencias

- **Legalidad:** capturar probe requests revela información **personal** de los dispositivos (qué redes buscan). En algunos países, esto puede considerarse **invasión de privacidad**. Infórmate de la legislación local.
- **MAC randomization:** la mayoría de móviles modernos (iOS 8+, Android 6+) usan **MAC aleatoria** en los probe requests. Verás MACs que empiezan por `FA`, `F2`, `F6`, etc. No es un error, es una medida de privacidad.
- **Probes dirigidos vs wildcard:** los dirigidos revelan SSIDs guardados; los wildcard solo revelan que hay un dispositivo escaneando.
- **Ruido:** en zonas muy saturadas, puedes recibir miles de probes por minuto. Filtra por SSID o MAC si buscas algo concreto.
- **Detección:** algunos dispositivos modernos **no emiten probe requests** hasta que el usuario abre la pantalla de WiFi manualmente. No los verás si están en modo pasivo.
- **Almacenamiento:** en zonas densas, el log puede crecer muy rápido. 1 hora de captura puede generar 10-50 MB.

---

## 🔗 Relacionado

- [Beacon Sniff](beacon.md) — complementario: redes vs dispositivos
- [Scan AP/STA](scan-ap-sta.md) — variante activa que muestra clientes conectados
- [Detect Pwnagotchi](detect-pwnagotchi.md) — usa probes específicos para detectar Pwnagotchis
- [Karma](../attacks/karma.md) — ataque que responde a probe requests
- [Evil Portal](../attacks/evil-portal.md) — portal captive que usa probe requests
- [Wardrive](wardrive.md) — combina probes con GPS para mapear dispositivos