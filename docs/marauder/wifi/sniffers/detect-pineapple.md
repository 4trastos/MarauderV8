# 📡 Detect Pineapple

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Detect Pineapple** detecta dispositivos **WiFi Pineapple** en tu zona. Un WiFi Pineapple es una **herramienta de auditoría** fabricada por **Hak5** que se usa para:

- **Ataques de red** (Evil Portal, Karma, etc.).
- **Auditorías profesionales**.
- **Pruebas de penetración**.
- **Ataques maliciosos** (en manos de cualquiera).

Los Pineapples emiten **beacons y probe responses muy específicos** que los identifican. **Detect Pineapple** escucha esos patrones y te avisa.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Detect Pineapple**.
3. Pulsa **Start**.
4. El Marauder escaneará todos los canales buscando:
   - **MACs conocidas** de Pineapples (OUIs de Hak5).
   - **SSIDs típicos** (`Pineapple`, `pwned`, etc.).
   - **Patrones de respuesta** característicos de Karma.
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
=== Pineapple Detectados ===

MAC                 SSID              Canal  RSSI
00:13:37:AA:BB:CC   Pineapple         6      -58
00:13:37:DD:EE:FF   pwned             1      -65
```

### En la SD

Un archivo `.txt`:

```text
Timestamp,MAC,SSID,Channel,RSSI
2026-10-11 12:35:01,00:13:37:AA:BB:CC,Pineapple,6,-58
2026-10-11 12:35:05,00:13:37:DD:EE:FF,pwned,1,-65
...
```

---

## 🎯 Para qué sirve

### 1. Detectar Pineapples cercanos

Si estás en un entorno con hackers o auditores, puede haber Pineapples. **Detect Pineapple** te avisa.

### 2. Auditoría de seguridad

Si administras una red, un Pineapple en la zona puede estar atacando a tus clientes. **Detect Pineapple** te lo revela.

### 3. Defensa contra ataques

Si un Pineapple está lanzando un **Evil Portal** contra tus clientes, **Detect Pineapple** te dice:

- **Dónde está** (por RSSI).
- **Qué está emitiendo** (SSID).
- **Cómo localizarlo** (con Fox Hunt).

### 4. Investigación

Si estás estudiando Pineapples, **Detect Pineapple** te dice cuántos hay y dónde.

---

## 🎯 Cómo funciona la detección

Los Pineapples emiten:

1. **SSIDs específicos** en sus beacons:
   - `Pineapple`
   - `pwned`
   - `Pineapple_XXXX` (con sufijo)
   - `FreeWiFi` (a veces)

2. **MACs conocidas**:
   - Los Pineapples usan MACs de Hak5.
   - Los OUIs son conocidos (`00:13:37`, etc.).

3. **Patrones de respuesta**:
   - Los Pineapples responden a **cualquier** probe request (Karma).
   - Eso los delata.

**Detect Pineapple** combina los tres para identificar dispositivos.

---

## ⚠️ Advertencias

- **Falsos positivos:** otros dispositivos pueden emitir SSIDs similares. Confirma con **Beacon Sniff**.
- **MAC spoofing:** un Pineapple puede cambiar su MAC para no ser detectado.
- **SSID spoofing:** un atacante puede emitir SSIDs de Pineapple para engañarte.
- **Alcance:** solo detectas Pineapples a tu alcance. Si están lejos, no los ves.
- **Legalidad:** escuchar beacons es **pasivo** y legal. Detectar dispositivos es defensivo.

---

## 🔗 Relacionado

- [Beacon Sniff](beacon.md) — para ver todos los beacons
- [Detect Pwnagotchi](detect-pwnagotchi.md) — para detectar Pwnagotchis
- [Detect MultiSSID](detect-multissid.md) — para detectar beacons spam
- [Fox Hunt](fox-hunt.md) — para localizar físicamente al Pineapple
