# 📶 Join WiFi

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Join WiFi** conecta el Marauder a una **red WiFi** como cliente. Esto permite al Marauder:

- **Navegar por internet** (si la red tiene salida).
- **Ejecutar scanners** (Ping Scan, Port Scan, etc.).
- **Acceder a servicios** de la red (HTTP, SSH, etc.).
- **Actualizar firmware** desde la red.

Es la forma de que el Marauder **deje de ser un observador** y se convierta en un **participante** de la red.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. **Escanea las redes** con **Scan AP/STA** o **Beacon Sniff**.
3. Navega hasta **WiFi → General → Join WiFi**.
4. Selecciona la **red** a la que quieres conectarte.
5. Introduce la **contraseña** (si es WPA/WPA2).
6. Pulsa **Connect**.
7. El Marauder se conectará y obtendrá una IP por DHCP.
8. Verás la IP asignada en pantalla.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **SSID** | Red a la que conectar | Ninguno |
| **Contraseña** | Password de la red | Ninguno |
| **DHCP** | Obtener IP automáticamente | Sí |
| **IP estática** | IP manual (si no DHCP) | Ninguna |

---

## 📊 Qué genera

### En pantalla

```text
=== Join WiFi ===
Red: MiFibra-BB6F
Contraseña: ********

Conectando...
✅ Conectado
IP: 192.168.1.42
Máscara: 255.255.255.0
Gateway: 192.168.1.1
DNS: 192.168.1.1
RSSI: -62 dBm
```

### En la SD (opcional)

Si guardas la red, se almacena en `/wifi/saved.txt`:

```text
MiFibra-BB6F:mi_password
Movistar_5G:otra_password
```

---

## 🎯 Para qué sirve

### 1. Conectar a tu red

Si quieres usar el Marauder para **escanear tu red** (Ping Scan, Port Scan, etc.), primero tienes que conectarlo.

### 2. Navegar por internet

Si necesitas que el Marauder acceda a internet (para actualizar firmware, por ejemplo), conéctalo a tu red.

### 3. Auditar tu propia red

Una vez conectado, puedes:

- Hacer **Ping Scan** para ver hosts.
- Hacer **Port Scan All** para ver servicios.
- Hacer **HTTP Scan** para ver paneles web.
- Probar credenciales en tus propios dispositivos.

### 4. Capturar tráfico

Si estás conectado a la red, puedes capturar tu propio tráfico (aunque está cifrado con WPA2, no verás el contenido).

---

## ⚠️ Advertencias

- **Contraseña:** si la red usa WPA2/WPA3, necesitas la contraseña. Sin ella, no te conectas.
- **MAC randomization:** el Marauder puede cambiar su MAC al conectarse. Si la red tiene filtrado MAC, no te conectarás.
- **DHCP:** si la red no tiene DHCP, tendrás que configurar IP estática.
- **Legalidad:** conectarte a una red ajena sin autorización es **delito**. Solo en tu red o con autorización.
- **Seguridad:** al conectarte a una red, el Marauder es visible para otros dispositivos. No lo uses para atacar la misma red a la que estás conectado (te detectarán).

---

## 🔗 Relacionado

- [Join Saved WiFi](join-saved-wifi.md) — conecta a red guardada
- [Scan AP/STA](../sniffers/scan-ap-sta.md) — escanea redes antes de conectar
- [Ping Scan](../scanners/ping-scan.md) — primer paso tras conectar
- [Start AP](start-ap.md) — alternativa: levantar tu propio AP
