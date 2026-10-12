# 🎭 Karma

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Karma** es un ataque que **responde a los probe requests** de los clientes haciéndose pasar por la red que buscan. Si un móvil busca `MiFibra-BB6F`, el Marauder responde como si fuera `MiFibra-BB6F`, y el móvil se conecta automáticamente.

Es un ataque **muy efectivo** porque los dispositivos confían en los probe requests que ellos mismos emiten. Es la base de **Evil Portal** y **AP Clone Spam**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Karma**.
3. Configura el **canal** donde escuchar.
4. Configura el **tiempo de respuesta** (por defecto: inmediato).
5. Pulsa **Start**.
6. El Marauder escuchará probe requests y responderá a cada uno.
7. Los clientes que busquen redes conocidas se conectarán al Marauder.
8. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal** | Canal donde escuchar | 1 |
| **Respuesta** | Inmediata o con retardo | Inmediata |
| **SSID** | SSID a usar en la respuesta | El del probe |
| **Cifrado** | Abierto, WPA2 o WPA3 | Abierto |

---

## 📊 Qué genera

### En pantalla

```text
=== Karma ===
Canal: 1

Probes recibidos: 125
Clientes conectados: 3
SSIDs respondidos:
- MiFibra-BB6F
- Movistar_5G
- Vodafone-2.4G
```

### En el aire

El Marauder responde a cada probe request con el SSID solicitado. Los clientes se conectan automáticamente a él.

---

## 🎯 Para qué sirve

### 1. Base para Evil Portal

Una vez que el cliente se conecta, puedes mostrarle un portal captive para capturar credenciales.

### 2. Análisis de dispositivos

Ver qué redes buscan los dispositivos cercanos. Es una forma de **inventario pasivo** de dispositivos.

### 3. Pruebas de seguridad

Ver si los dispositivos de tu empresa se conectan automáticamente a APs desconocidos.

### 4. Investigación

Estudiar el comportamiento de dispositivos cuando se enfrentan a un Karma attack.

---

## ⚠️ Advertencias

- **Legalidad:** Karma es **suplantación de identidad** + **interferencia**. Delito grave.
- **Detección:** los dispositivos modernos (iOS 8+, Android 6+) **ignoran** los probe responses de APs desconocidos. El ataque no funciona con ellos.
- **Alcance:** limitado (~10-30 metros).
- **Compatibilidad:** funciona mejor con dispositivos antiguos o mal configurados.
- **Cifrado:** si el SSID original usaba WPA2, el cliente esperará un handshake. Si no lo das, no se conectará.
- **Ética:** no uses Karma para atacar dispositivos ajenos. Es delito.

---

## 🔗 Relacionado

- [Evil Portal](evil-portal.md) — combinación con portal captive
- [AP Clone Spam](ap-clone-spam.md) — clonar un AP específico
- [Probe Req Flood](probe-req-flood.md) — flood de probes
- [Probe Request Sniff](../sniffers/probe-request.md) — sniffer de probes
