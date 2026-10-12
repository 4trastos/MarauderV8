# 📡 AP Clone Spam

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**AP Clone Spam** **clona un AP legítimo** emitiendo beacons con el mismo SSID, BSSID y configuración. El objetivo es que los clientes cercanos confundan el AP clonado con el original y se conecten a él.

Es la base para ataques más complejos como **Evil Portal** o **Karma**.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea las redes** con **Beacon Sniff** o **Scan AP/STA**.
2. Identifica el AP que quieres clonar: **SSID, BSSID, canal, cifrado**.
3. Anota los datos.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → AP Clone Spam**.
3. Introduce los datos del AP a clonar:
   - **SSID**: nombre de la red.
   - **BSSID**: MAC del AP original.
   - **Canal**: canal del AP.
4. Pulsa **Start**.
5. El Marauder emitirá beacons con los mismos datos.
6. Los clientes cercanos pueden confundir el clon con el original.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **SSID** | SSID del AP original | Ninguno |
| **BSSID** | BSSID del AP original | Ninguno |
| **Canal** | Canal del AP | 1 |
| **Intervalo** | Tiempo entre beacons | 100 ms |

---

## 📊 Qué genera

### En pantalla

```text
=== AP Clone Spam ===
SSID: MiFibra-BB6F
BSSID: FA:8F:CA:61:05:78
Canal: 6

Emitiendo beacons clonados...
Beacons enviados: 500
```

### En el aire

Dos APs con el mismo SSID, BSSID y canal. Los clientes cercanos pueden intentar conectarse al clon si tiene mejor señal.

---

## 🎯 Para qué sirve

### 1. Base para Evil Portal

El clon sirve como señuelo para que los clientes se conecten a tu AP falso, donde les muestras el portal captive.

### 2. Base para Karma

El clon responde a los probe requests de los clientes que buscan esa red.

### 3. Interrupción de red

Si el clon tiene mejor señal, los clientes pueden conectarse a él en lugar del original, interrumpiendo su conexión.

### 4. Investigación

Estudiar cómo los clientes eligen entre dos APs con el mismo SSID.

---

## ⚠️ Advertencias

- **Legalidad:** clonar un AP ajeno es **delito**. Suplantación de identidad + interferencia.
- **Detección:** los WIDS/WIPS detectan APs duplicados fácilmente.
- **Alcance:** limitado (~10-30 metros). Si estás lejos del cliente, no funcionará.
- **Cifrado:** si el AP original usa WPA2/WPA3, el cliente no se conectará al clon a menos que tenga la contraseña.
- **Canales:** el clon debe estar en el mismo canal que el original.
- **Ética:** no uses este ataque para interrumpir la red de un vecino. Es delito.

---

## 🔗 Relacionado

- [Evil Portal](evil-portal.md) — combinación con portal captive
- [Karma](karma.md) — combinación con respuesta a probes
- [Beacon Spam List](beacon-spam-list.md) — variante sin clonar
- [Scan AP/STA](../sniffers/scan-ap-sta.md) — para identificar el AP a clonar
