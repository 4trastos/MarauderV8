# 📡 AirTag Sniffer

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**AirTag Sniffer** detecta específicamente **Apple AirTags** (y dispositivos similares de la red Find My de Apple) por su **firma BLE**. Los AirTags emiten anuncios BLE con un formato específico que los identifica.

Es la herramienta **defensiva** contra el **stalking** con AirTags: te dice si hay un AirTag cerca de ti.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Sniffers → AirTag Sniffer**.
3. Pulsa **Start**.
4. El Marauder escaneará los canales BLE buscando anuncios de AirTag.
5. Verás en pantalla:
   - **MAC** del AirTag (aleatoria).
   - **RSSI**.
   - **Estado** (separado, emparejado, etc.).
   - **Último visto**.
6. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Duración** | Tiempo de escaneo | Sin límite |
| **Filtro RSSI** | Solo AirTags cercanos | Ninguno |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== AirTag Sniffer ===
AirTags detectados: 2

MAC                 RSSI  Estado      Último visto
DE:AD:BE:EF:12:34   -62   Separado    12:35:01
AA:BB:CC:DD:EE:FF   -70   Separado    12:35:05
```

### En la SD

Un archivo `.txt`:

```text
MAC,RSSI,State,LastSeen
DE:AD:BE:EF:12:34,-62,Separado,12:35:01
AA:BB:CC:DD:EE:FF,-70,Separado,12:35:05
```

---

## 🎯 Para qué sirve

### 1. Detectar stalking con AirTags

El caso de uso principal. Si alguien ha puesto un AirTag en tu mochila, coche o bolsillo, **AirTag Sniffer** te lo revela.

### 2. Auditoría de privacidad

Si estás en un espacio público o compartido, puedes comprobar si hay AirTags rastreando.

### 3. Búsqueda de AirTags perdidos

Si has perdido un AirTag tuyo, **AirTag Sniffer** te ayuda a localizarlo (con **Fox Hunt**).

### 4. Análisis de dispositivos Apple

Si quieres saber cuántos dispositivos Apple hay en una zona, **AirTag Sniffer** te da una idea.

### 5. Detección de trackers genéricos

Aunque está diseñado para AirTags, también detecta otros dispositivos de la red Find My (como algunos auriculares y accesorios Apple).

---

## 🎯 Cómo distinguir un AirTag legítimo de uno malicioso

| Señal | Legítimo | Malicioso |
|---|---|---|
| **Estado** | Emparejado con su dueño | Separado mucho tiempo |
| **RSSI** | Variable (el dueño se mueve) | Constante (el AirTag te sigue) |
| **Ubicación** | En tu casa, en tu mochila | En tu coche, en tu bolsillo |
| **Duración** | Aparece y desaparece | Presente siempre |

Si un AirTag aparece **siempre** cerca de ti durante **horas o días**, puede ser malicioso.

---

## ⚠️ Advertencias

- **Legalidad:** escanear BLE es **pasivo** y legal.
- **MAC randomization:** los AirTags usan MAC aleatoria que cambia cada cierto tiempo. Verás MACs distintas para el mismo AirTag.
- **Falsos positivos:** otros dispositivos Apple pueden emitir anuncios similares. Confirma con **BLE Sniff**.
- **Alcance:** BLE tiene un alcance de ~10-30 metros. Si el AirTag está lejos, no lo ves.
- **Privacidad:** si detectas un AirTag ajeno, no intentes acceder a su información. Solo documenta.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — escaneo general de BLE
- [BLE Sniff](ble-sniff.md) — captura anuncios a pcap
- [Flipper Sniffer](flipper-sniffer.md) — detecta Flipper Zero
- [Fox Hunt](../wifi/sniffers/fox-hunt.md) — para localizar físicamente el AirTag
