# 📡 Flipper Sniffer

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Flipper Sniffer** detecta dispositivos **Flipper Zero** (y similares) por su **firma BLE**. El Flipper Zero es una herramienta de auditoría portátil que puede:

- Emular tarjetas RFID/NFC.
- Emitir señales infrarrojas.
- Comunicarse por BLE.
- Hacer Bad USB.

Los Flipper Zero emiten anuncios BLE con un formato específico que los identifica.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Sniffers → Flipper Sniffer**.
3. Pulsa **Start**.
4. El Marauder escaneará los canales BLE buscando anuncios de Flipper.
5. Verás en pantalla:
   - **MAC** del Flipper.
   - **Nombre** (suele ser `Flipper`).
   - **RSSI**.
   - **Estado**.
6. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Duración** | Tiempo de escaneo | Sin límite |
| **Filtro RSSI** | Solo Flippers cercanos | Ninguno |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Flipper Sniffer ===
Flippers detectados: 1

MAC                 Nombre     RSSI  Estado
DE:AD:BE:EF:12:34   Flipper    -58   Activo
```

### En la SD

Un archivo `.txt`:

```text
MAC,Name,RSSI,State
DE:AD:BE:EF:12:34,Flipper,-58,Activo
```

---

## 🎯 Para qué sirve

### 1. Detectar Flippers cercanos

Si estás en un entorno con hackers o auditores, puede haber Flippers. **Flipper Sniffer** te avisa.

### 2. Auditoría de seguridad

Si administras una red, un Flipper en la zona puede estar intentando ataques (Bad USB, RFID, etc.).

### 3. Detección de dispositivos sospechosos

Si ves un Flipper cerca, puede ser:

- Un auditor autorizado.
- Un curioso con herramientas.
- Un atacante malicioso.

### 4. Investigación

Si estás estudiando Flippers, **Flipper Sniffer** te dice cuántos hay y dónde.

---

## 🎯 Cómo funciona la detección

Los Flipper Zero emiten:

1. **Anuncios BLE** con nombre `Flipper`.
2. **Servicios BLE específicos** que los identifican.
3. **Patrones de conexión** característicos.

**Flipper Sniffer** combina los tres para identificar dispositivos.

---

## ⚠️ Advertencias

- **Legalidad:** escanear BLE es **pasivo** y legal.
- **MAC spoofing:** un Flipper puede cambiar su MAC y nombre para no ser detectado.
- **Alcance:** BLE tiene un alcance de ~10-30 metros.
- **Falsos positivos:** otros dispositivos pueden llamarse `Flipper`. Confirma con **BLE Sniff**.
- **Privacidad:** si detectas un Flipper ajeno, no interactúes con él.

---

## 🔗 Relacionado

- [BLE Scan](ble-scan.md) — escaneo general de BLE
- [BLE Sniff](ble-sniff.md) — captura anuncios a pcap
- [AirTag Sniffer](airtag-sniffer.md) — detecta AirTags
- [Fox Hunt](../wifi/sniffers/fox-hunt.md) — para localizar físicamente el Flipper
