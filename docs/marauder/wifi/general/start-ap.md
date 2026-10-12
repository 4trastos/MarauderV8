# 📡 Start AP

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Start AP** convierte el Marauder en un **Punto de Acceso (AP)**. Los dispositivos cercanos pueden conectarse a él como si fuera un router normal.

Es la base para ataques como **Evil Portal**, **Karma** y **AP Clone Spam**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Start AP**.
3. Configura:
   - **SSID**: nombre del AP (por defecto: `Marauder`).
   - **Contraseña**: password del AP (o abierto).
   - **Canal**: canal donde emitir.
   - **Cifrado**: abierto, WPA2 o WPA3.
4. Pulsa **Start**.
5. El Marauder levanta el AP.
6. Los dispositivos cercanos verán el SSID y podrán conectarse.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **SSID** | Nombre del AP | `Marauder` |
| **Contraseña** | Password (vacío = abierto) | Ninguna |
| **Canal** | Canal donde emitir | 1 |
| **Cifrado** | Abierto, WPA2, WPA3 | Abierto |
| **Máx. clientes** | Nº máximo de clientes | 4 |

---

## 📊 Qué genera

### En pantalla

```text
=== Start AP ===
SSID: FreeWiFi
Canal: 6
Cifrado: Abierto

Estado: Activo
Clientes conectados: 2
IP del AP: 192.168.4.1
```

### En el aire

Un AP falso con el SSID configurado. Los dispositivos cercanos lo ven como una red disponible.

---

## 🎯 Para qué sirve

### 1. Base para Evil Portal

Una vez levantado el AP, puedes lanzar **Evil Portal** para mostrar un portal captive falso.

### 2. Base para Karma

El AP puede responder a probe requests de clientes que buscan redes conocidas.

### 3. Base para AP Clone Spam

Puedes clonar un AP legítimo cambiando el SSID y BSSID.

### 4. Servidor local

Si conectas el Marauder a internet (con **Join WiFi**), puedes compartir la conexión con los clientes que se conecten a tu AP.

### 5. Pruebas de red

Si quieres probar cómo se comporta un dispositivo al conectarse a una red nueva.

---

## ⚠️ Advertencias

- **Legalidad:** levantar un AP con el SSID de una red ajena es **delito** (suplantación de identidad).
- **Detección:** los WIDS/WIPS detectan APs no autorizados.
- **Alcance:** limitado (~10-30 metros).
- **Canales:** si el canal está saturado, el AP puede no funcionar bien.
- **Clientes:** el ESP32 tiene recursos limitados. No esperes más de 4-8 clientes.
- **Seguridad:** si levantas un AP abierto, cualquiera puede conectarse. Ten cuidado con lo que haces con esos clientes.

---

## 🔗 Relacionado

- [Evil Portal](../attacks/evil-portal.md) — ataque que usa el AP
- [Karma](../attacks/karma.md) — ataque que usa el AP
- [AP Clone Spam](../attacks/ap-clone-spam.md) — clonar un AP
- [Host AP Info](host-ap-info.md) — ver info del AP levantado
- [Join WiFi](join-wifi.md) — alternativa: conectar a una red existente