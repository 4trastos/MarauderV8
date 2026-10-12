# 📡 View AP Info

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**View AP Info** muestra **información detallada** de un Punto de Acceso concreto: SSID, BSSID, canal, cifrado, RSSI, clientes conectados, etc. Es una utilidad de **consulta**: no modifica nada, solo muestra datos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. **Escanea las redes** con **Scan AP/STA** o **Beacon Sniff**.
3. Navega hasta **WiFi → General → View AP Info**.
4. Selecciona el AP que quieras consultar.
5. Verás toda la información disponible.
6. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **AP** | AP a consultar | Ninguno |

---

## 📊 Qué genera

### En pantalla

```text
=== View AP Info ===
SSID:        MiFibra-BB6F
BSSID:       FA:8F:CA:61:05:78
Canal:       6
Cifrado:     WPA2-PSK-CCMP
RSSI:        -67 dBm
Primera vez: 12:34:56
Última vez:  12:35:12
Paquetes:    1247
Clientes:    3
  - 3C:5A:B4:12:34:56 (RSSI: -65)
  - A4:83:E7:11:22:33 (RSSI: -70)
  - F0:18:98:AA:BB:CC (RSSI: -68)
Fabricante:  (desconocido)
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Ver detalles de un AP

Antes de atacar un AP, quieres saber:

- Su **canal** (para estar en el correcto).
- Su **cifrado** (WPA2 vs WPA3).
- Sus **clientes** (para atacar dirigido).
- Su **RSSI** (para saber si estás cerca).

**View AP Info** te da todo eso en una pantalla.

### 2. Confirmar que es el AP correcto

Si tienes varios APs con el mismo SSID, **View AP Info** te ayuda a distinguirlos por BSSID.

### 3. Ver clientes conectados

Si quieres atacar a un cliente específico, **View AP Info** te lista los clientes conectados al AP.

---

## ⚠️ Advertencias

- **Dependencia:** necesitas haber escaneado APs antes.
- **Datos limitados:** la info mostrada depende de lo que el Marauder haya capturado.
- **Fabricante:** a veces no se puede determinar. Aparece como `(desconocido)`.
- **Actualización:** la info se actualiza cada vez que escaneas. Si quieres datos frescos, vuelve a escanear.

---

## 🔗 Relacionado

- [Scan AP/STA](../sniffers/scan-ap-sta.md) — escanea APs
- [Select APs](select-aps.md) — selecciona APs objetivo
- [Deauth Targeted](../attacks/deauth-targeted.md) — ataque dirigido
