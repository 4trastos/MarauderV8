# 📡 Detect Pwnagotchi

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Detect Pwnagotchi** detecta dispositivos **Pwnagotchi** en tu zona. Un Pwnagotchi es un **"hacker" portátil** basado en Raspberry Pi Zero que:

- Escucha el aire pasivamente.
- Captura handshakes WPA/WPA2 automáticamente.
- Aprende de su entorno con un sistema de IA (A2C).
- Muestra una cara animada en una pantalla e-ink.
- **Se conecta a otros Pwnagotchis** para colaborar.

Los Pwnagotchis emiten **probe requests y beacons muy específicos** que los identifican. **Detect Pwnagotchi** escucha esos patrones y te avisa.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Detect Pwnagotchi**.
3. Pulsa **Start**.
4. El Marauder escaneará todos los canales buscando:
   - **SSIDs típicos de Pwnagotchi** (`pwnagotchi`, `Pwnagotchi`, `pwngrid`).
   - **MACs conocidas** de Pwnagotchis.
   - **Patrones de probe requests** característicos.
5. Si detecta uno, verás:
   - **MAC**
   - **SSID**
   - **RSSI**
   - **Canal**
6. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canales** | Qué canales escanear | Todos |
| **Sensibilidad** | Umbral de detección | Media |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Pwnagotchi Detectados ===

MAC                 SSID              Canal  RSSI
DE:AD:BE:EF:12:34   pwnagotchi        6      -62
DE:AD:BE:EF:56:78   Pwnagotchi        1      -70
AA:BB:CC:DD:EE:FF   pwngrid           11     -75
```

### En la SD

Un archivo `.txt`:

```text
Timestamp,MAC,SSID,Channel,RSSI
2026-10-11 12:35:01,DE:AD:BE:EF:12:34,pwnagotchi,6,-62
2026-10-11 12:35:05,DE:AD:BE:EF:56:78,Pwnagotchi,1,-70
...
```

---

## 🎯 Para qué sirve

### 1. Detectar Pwnagotchis cercanos

Si vives en una zona con makers o hackers, puede haber Pwnagotchis cerca. **Detect Pwnagotchi** te avisa.

### 2. Auditoría de seguridad

Si administras una red, un Pwnagotchi en la zona puede estar capturando handshakes de tus clientes. **Detect Pwnagotchi** te lo revela.

### 3. Investigación

Si estás estudiando Pwnagotchis, **Detect Pwnagotchi** te dice cuántos hay y dónde.

### 4. Competencia amistosa

Si tú también tienes un Pwnagotchi, **Detect Pwnagotchi** te dice si hay otros en la zona. Los Pwnagotchis pueden **colaborar** entre sí.

---

## 🎯 Cómo funciona la detección

Los Pwnagotchis emiten:

1. **SSIDs específicos** en sus beacons:
   - `pwnagotchi`
   - `Pwnagotchi`
   - `pwngrid`
   - `pwnagotchi-XXXX` (con sufijo aleatorio)

2. **Probe requests específicos**:
   - Buscan redes con nombres tipo `pwnagotchi`.
   - Emiten probes a intervalos regulares.

3. **MACs conocidas**:
   - Los Pwnagotchis usan MACs de Raspberry Pi.
   - Algunos cambian la MAC, pero otros no.

**Detect Pwnagotchi** combina los tres para identificar dispositivos.

---

## ⚠️ Advertencias

- **Falsos positivos:** otros dispositivos pueden emitir SSIDs similares. Confirma con **Beacon Sniff**.
- **MAC spoofing:** un Pwnagotchi puede cambiar su MAC para no ser detectado.
- **SSID spoofing:** un atacante puede emitir SSIDs de Pwnagotchi para engañarte.
- **Alcance:** solo detectas Pwnagotchis a tu alcance. Si están lejos, no los ves.
- **Legalidad:** escuchar beacons es **pasivo** y legal. Detectar dispositivos es defensivo.

---

## 🔗 Relacionado

- [Beacon Sniff](beacon.md) — para ver todos los beacons
- [Detect Pineapple](detect-pineapple.md) — para detectar WiFi Pineapples
- [Detect MultiSSID](detect-multissid.md) — para detectar beacons spam
- [Fox Hunt](fox-hunt.md) — para localizar físicamente al Pwnagotchi