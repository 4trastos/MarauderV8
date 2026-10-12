# 📡 Set MACs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Set MACs** permite **cambiar las direcciones MAC** del Marauder (WiFi y Bluetooth). Esto se conoce como **MAC spoofing**.

Cambiar la MAC es útil para:

- **Ocultar la MAC real** del Marauder.
- **Suplantar** la MAC de otro dispositivo.
- **Evitar filtros MAC** en una red.
- **Reiniciar** contadores de DHCP.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Set MACs**.
3. Selecciona:
   - **WiFi MAC**: MAC del adaptador WiFi.
   - **BT MAC**: MAC del adaptador Bluetooth.
4. Introduce la MAC nueva (formato `XX:XX:XX:XX:XX:XX`).
5. Pulsa **Save**.
6. La MAC se aplica inmediatamente (o al reiniciar, según firmware).

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **WiFi MAC** | MAC del WiFi | La real del chip |
| **BT MAC** | MAC del Bluetooth | La real del chip |
| **Aleatoria** | Generar MAC aleatoria | No |
| **Aplicar** | Aplicar al instante | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Set MACs ===
WiFi MAC actual:   FA:8F:CA:61:05:78
WiFi MAC nueva:    00:11:22:33:44:55
BT MAC actual:     DE:AD:BE:EF:12:34
BT MAC nueva:      AA:BB:CC:DD:EE:FF

[Save]
```

No genera archivos. El cambio es en memoria.

---

## 🎯 Para qué sirve

### 1. Ocultar la MAC real

Si no quieres que tu MAC real aparezca en los logs de una red, cámbiala.

### 2. Evitar filtros MAC

Si una red tiene filtrado MAC (solo permite ciertas MACs), puedes suplantar la de un dispositivo autorizado.

### 3. Suplantar dispositivos

Si quieres hacerte pasar por otro dispositivo (AP, cliente), puedes usar su MAC.

### 4. Reiniciar contadores DHCP

Si te has conectado muchas veces a una red y el DHCP te da siempre la misma IP, cambia la MAC para obtener una nueva.

### 5. Base para ataques

Muchos ataques requieren MAC spoofing:

- **AP Clone Spam**: suplantar la MAC del AP.
- **Karma**: responder con MACs distintas.
- **Deauth**: enviar con MAC del AP suplantado.

---

## ⚠️ Advertencias

- **Legalidad:** suplantar la MAC de un dispositivo ajeno es **delito** (suplantación de identidad).
- **Detección:** los WIDS/WIPS detectan MACs duplicadas o sospechosas.
- **Restricciones:** algunas MACs no se pueden usar (multicast, broadcast, etc.).
- **Persistencia:** algunos firmwares no guardan la MAC tras reiniciar. Comprueba el tuyo.
- **Conexión:** si estás conectado a una red y cambias la MAC, se te desconectará.
- **Filtros MAC:** el filtrado MAC es fácil de saltar con spoofing. No es una medida de seguridad real.

---

## 🔗 Relacionado

- [AP Clone Spam](../attacks/ap-clone-spam.md) — usa MAC spoofing
- [Karma](../attacks/karma.md) — usa MAC spoofing
- [Deauth Targeted](../attacks/deauth-targeted.md) — puede usar MAC spoofing
- [Join WiFi](join-wifi.md) — cambia la MAC antes de conectar
