# 📡 Beacon Spam List

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Beacon Spam List** emite **beacons falsos** con SSIDs de una **lista predefinida**. Crea cientos de redes WiFi falsas en el aire, saturando el espectro y confundiendo a los dispositivos cercanos.

Es uno de los ataques más **visibles y ruidosos**. Su objetivo no es robar datos, sino **saturar** o **confundir**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Beacon Spam List**.
3. Selecciona la **lista de SSIDs** a usar (o usa la por defecto).
4. Configura el **intervalo** entre beacons (por defecto: 100 ms).
5. Pulsa **Start**.
6. El Marauder emitirá beacons falsos con los SSIDs de la lista.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Lista SSIDs** | SSIDs a emitir | Lista por defecto |
| **Intervalo** | Tiempo entre beacons | 100 ms |
| **Canal** | Canal donde emitir | 1 |
| **Aleatorio** | Orden aleatorio | No |

---

## 📊 Qué genera

### En pantalla

```text
=== Beacon Spam List ===
SSIDs: 50
Intervalo: 100 ms
Canal: 1

Emitiendo:
FreeWiFi
WiFi_Gratis
HackMe
...
Beacons enviados: 1250
```

### En el aire

Cientos de redes falsas aparecen en los dispositivos cercanos. Los móviles y portátiles las listan como redes disponibles, aunque no se pueden conectar.

---

## 🎯 Para qué sirve

### 1. Pruebas de saturación

Ver cómo se comporta una red cuando hay cientos de SSIDs falsos.

### 2. Demostraciones

Mostrar el impacto de un beacon spam en una presentación de seguridad.

### 3. Confusión de dispositivos

Algunos dispositivos pueden intentar conectarse a SSIDs falsos (si coinciden con redes guardadas).

### 4. Base para ataques más complejos

El beacon spam puede combinarse con **Evil Portal** o **Karma** para atraer clientes.

---

## ⚠️ Advertencias

- **Legalidad:** emitir beacons falsos es **interferencia de telecomunicaciones**. Delito en España (art. 197 bis, 264 CP).
- **Detección:** muy fácil de detectar. Cualquiera con un sniffer lo ve.
- **Saturación:** puede afectar a **otras redes cercanas**, no solo a la tuya.
- **Alcance:** el ESP32 tiene poca potencia. El alcance es limitado (~10-30 metros).
- **Impacto:** la mayoría de dispositivos ignoran SSIDs falsos, pero algunos pueden intentar conectarse.

---

## 🔗 Relacionado

- [Beacon Spam Random](beacon-spam-random.md) — versión con SSIDs aleatorios
- [Funny SSID Beacon](funny-ssid-beacon.md) — versión con SSIDs graciosos
- [Rick Roll Beacon](rick-roll-beacon.md) — versión con Rick Astley
- [Detect MultiSSID](../sniffers/detect-multissid.md) — detector de este ataque
- [Evil Portal](evil-portal.md) — combinación con portal captive
