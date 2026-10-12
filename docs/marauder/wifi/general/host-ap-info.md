# 📡 Host AP Info

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Host AP Info** muestra **información detallada** del AP que el Marauder está levantando con **Start AP**: SSID, BSSID, canal, cifrado, clientes conectados, IP, etc.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. **Levanta un AP** con **Start AP**.
2. Navega hasta **WiFi → General → Host AP Info**.
3. Verás toda la información del AP activo.
4. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **AP** | AP a consultar | El activo |

---

## 📊 Qué genera

### En pantalla

```text
=== Host AP Info ===
SSID:        FreeWiFi
BSSID:       DE:AD:BE:EF:12:34
Canal:       6
Cifrado:     Abierto
IP del AP:   192.168.4.1
Máscara:     255.255.255.0
DHCP:        Activo (rango 192.168.4.2-192.168.4.10)
Clientes:    2
  - 3C:5A:B4:12:34:56 (IP: 192.168.4.2, RSSI: -60)
  - A4:83:E7:11:22:33 (IP: 192.168.4.3, RSSI: -68)
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Ver clientes conectados

Si has levantado un AP para **Evil Portal** o **Karma**, **Host AP Info** te dice qué dispositivos se han conectado.

### 2. Ver IPs asignadas

Si el AP tiene DHCP activo, verás qué IP ha asignado a cada cliente.

### 3. Diagnóstico

Si un cliente no se conecta, **Host AP Info** te ayuda a ver si el problema es del AP o del cliente.

### 4. Base para ataques posteriores

Una vez que sabes qué clientes están conectados, puedes lanzar ataques dirigidos contra ellos.

---

## ⚠️ Advertencias

- **Dependencia:** necesitas tener un AP activo (**Start AP**).
- **Actualización:** la info se actualiza cada vez que un cliente se conecta o desconecta.
- **Clientes:** el ESP32 tiene recursos limitados. No esperes más de 4-8 clientes.
- **Privacidad:** los datos de los clientes (MAC, IP) son información sensible. No los compartas.

---

## 🔗 Relacionado

- [Start AP](start-ap.md) — levanta el AP
- [Evil Portal](../attacks/evil-portal.md) — ataque que usa el AP
- [Karma](../attacks/karma.md) — ataque que usa el AP
