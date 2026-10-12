# 📡 Deauth Sniff

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Deauth Sniff** es un sniffer **pasivo** que detecta si alguien está lanzando **tramas de desautenticación** (deauth) en tu zona. A diferencia de **Deauth Targeted** o **Deauth Flood** (que las envían), este solo **escucha** y te avisa cuando las detecta.

Es la herramienta **defensiva** del Marauder: te dice si estás siendo atacado, o si alguien está haciendo pruebas cerca de ti.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada** (recomendable).
2. Navega hasta **WiFi → Sniffers → Deauth Sniff**.
3. Pulsa **Start**.
4. El Marauder escuchará todos los canales y detectará tramas de deauth.
5. Verás en pantalla:
   - **AP emisor** (normalmente suplantado)
   - **Cliente objetivo** (o broadcast)
   - **Razón** (código de deauth)
   - **RSSI**
   - **Timestamp**
6. Pulsa **Stop** cuando termines.
7. Si tienes SD, se guarda en `/logs/deauth_XXXX.txt`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canales** | Qué canales escuchar | Todos |
| **Filtro BSSID** | Solo deauths de un AP concreto | Ninguno |
| **Filtro STA** | Solo deauths a un cliente concreto | Ninguno |
| **Alerta** | Sonido/led al detectar | Activado |

---

## 📊 Qué genera

### En pantalla

```text
=== Deauth Detected ===
AP (spoofed):   FA:8F:CA:61:05:78
Target STA:     3C:5A:B4:12:34:56
Reason:         7 (Class 3 frame received from nonassociated STA)
RSSI:           -62
Timestamp:      12:35:01

Total deauths:  47
APs afectados:  2
Clientes afectados: 5
```

### En la SD

Un archivo `.txt`:

```text
Timestamp           AP (spoofed)        Target STA          Reason  RSSI
2026-10-11 12:35:01 FA:8F:CA:61:05:78   3C:5A:B4:12:34:56   7       -62
2026-10-11 12:35:02 FA:8F:CA:61:05:78   A4:83:E7:11:22:33   7       -65
2026-10-11 12:35:03 FA:8F:CA:61:05:78   broadcast           7       -60
...
```

### Si además tienes GPS

```text
Timestamp,AP,Target,Reason,RSSI,Latitude,Longitude
2026-10-11 12:35:01,FA:8F:CA:61:05:78,3C:5A:B4:12:34:56,7,-62,40.4168,-3.7038
```

Esto te permite **mapear los ataques** y saber dónde ocurren.

---

## 🎯 Para qué sirve

### 1. Detectar si estás siendo atacado

El caso de uso principal. Si tu WiFi se cae de repente y sospechas que alguien está haciendo deauth, **Deauth Sniff** te lo confirma:

- Verás las tramas de deauth.
- Verás el AP suplantado (que puede ser tu router).
- Verás el cliente objetivo (tu móvil, tu portátil).

### 2. Detectar ataques en tu zona

Aunque no seas el objetivo, si alguien está haciendo deauth cerca de ti, **Deauth Sniff** lo detecta. Útil para:

- Auditorías de seguridad en empresas.
- Detectar vecinos con Marauders.
- Detectar ataques en espacios públicos (aeropuertos, cafeterías).

### 3. Forense post-incidente

Si tu red ha sufrido un ataque, **Deauth Sniff** con GPS te da:

- **Cuándo** ocurrió.
- **Desde dónde** (si tienes GPS).
- **A quién** afectó.

Útil para denunciar o documentar el incidente.

### 4. Análisis de interferencias

A veces, las caídas de WiFi no son por ataques, sino por **interferencias** (microondas, cámaras, otros routers). **Deauth Sniff** te ayuda a descartar la hipótesis del ataque.

---

## 🎯 Códigos de razón de deauth

Las tramas de deauth incluyen un **código de razón**. Los más comunes:

| Código | Significado | Interpretación |
|---|---|---|
| **1** | Unspecified reason | Genérico |
| **2** | Previous auth no longer valid | El AP cambió |
| **3** | Deauthenticated because sending STA is leaving | El cliente se va |
| **4** | Disassociated due to inactivity | Timeout |
| **5** | Disassociated because AP is unable to handle all STAs | AP saturado |
| **6** | Class 2 frame received from nonauthenticated STA | Error de protocolo |
| **7** | Class 3 frame received from nonassociated STA | **Típico de ataque** |
| **8** | Disassociated because sending STA is leaving BSS | El cliente se va |
| **15** | 4-way handshake timeout | Fallo de handshake |
| **16** | Group key handshake timeout | Fallo de grupo |

**El código 7** es el más frecuente en ataques de deauth con Marauder o `aireplay-ng`.

---

## ⚠️ Advertencias

- **Legalidad:** escuchar deauths es **pasivo** y legal. Solo estás recibiendo tramas que van por el aire.
- **Falsos positivos:** no todas las deauths son ataques. Algunos APs las envían legítimamente (reinicios, actualizaciones, gestión de clientes).
- **Detección:** si alguien está haciendo deauth con **MAC spoofing**, verás el BSSID suplantado, no el real del atacante.
- **Ruido:** en zonas muy saturadas, puedes recibir muchas deauths legítimas. Filtra por BSSID o STA si buscas algo concreto.
- **Almacenamiento:** en zonas con ataques activos, el log puede crecer rápido.
- **GPS:** sin GPS, no sabrás **desde dónde** se lanza el ataque, solo que existe.

### Cómo distinguir un ataque de un deauth legítimo

| Señal | Ataque | Legítimo |
|---|---|---|
| **Frecuencia** | Muchas deauths en poco tiempo | Esporádicas |
| **Código de razón** | 7 (Class 3 frame) | 3, 4, 8 (STA leaving) |
| **BSSID** | Suplantado (MAC aleatoria o del AP) | El BSSID real del AP |
| **Target** | Broadcast o clientes específicos | STA concreta |
| **Patrón** | Repetitivo, constante | Puntual |

---

## 🔗 Relacionado

- [Deauth Targeted](../attacks/deauth-targeted.md) — ataque dirigido que este sniffer detecta
- [Deauth Flood](../attacks/deauth-flood.md) — ataque masivo que este sniffer detecta
- [Beacon Sniff](beacon.md) — para inventariar redes antes de analizar deauths
- [Scan AP/STA](scan-ap-sta.md) — para identificar AP y clientes afectados
- [MAC Monitor](mac-monitor.md) — para vigilar MACs específicas
- [Fox Hunt](fox-hunt.md) — para localizar físicamente al atacante
