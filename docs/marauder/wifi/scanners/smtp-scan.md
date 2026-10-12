# 📡 SMTP Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**SMTP Scan** busca **servidores SMTP** (puerto 25) en la red. SMTP (*Simple Mail Transfer Protocol*) es el protocolo para **enviar correo electrónico**.

Encontrar un servidor SMTP en tu red es normal si tienes:

- Un servidor de correo propio.
- Una impresora que envía escaneos por email.
- Una cámara IP que envía alertas.
- Un NAS que envía notificaciones.

Pero también puede ser un **riesgo** si:

- Está mal configurado (open relay).
- Permite enviar spam.
- No requiere autenticación.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → SMTP Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 500 ms).
5. Pulsa **Start**.
6. El Marauder probará el puerto 25 en cada IP y mostrará los hosts con SMTP abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto SMTP (por defecto 25) | 25 |
| **Timeout** | Tiempo de espera | 500 ms |
| **Banner** | Capturar banner SMTP | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== SMTP Scan ===
Rango: 192.168.1.0/24
Puerto: 25
Timeout: 500 ms

Servidores SMTP encontrados:
192.168.1.10    ESMTP Postfix
192.168.1.25    ESMTP Exim 4.94

Total: 2 servidores SMTP de 254 escaneados
Tiempo: 12 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,Banner
192.168.1.10,25,220 mail.local ESMTP Postfix
192.168.1.25,25,220 smtp.local ESMTP Exim 4.94
```

---

## 🎯 Para qué sirve

### 1. Inventario de servidores de correo

Saber qué dispositivos pueden enviar correo es útil para:

- Documentar la red.
- Detectar configuraciones no autorizadas.
- Auditar cumplimiento.

### 2. Detección de open relays

Un **open relay** es un servidor SMTP mal configurado que **reenvía correo de cualquiera**. Es un riesgo porque:

- Los spammers lo usan para enviar spam.
- Tu IP puede acabar en listas negras.
- Puedes recibir quejas de tu ISP.

**SMTP Scan** te dice si hay servidores SMTP. Luego puedes probar si son open relays.

### 3. Detección de dispositivos IoT

Muchos dispositivos IoT (impresoras, cámaras, NAS) tienen SMTP configurado para enviar alertas. **SMTP Scan** te los revela.

### 4. Base para ataques

Si encuentras un servidor SMTP, puedes:

- **Enumerar usuarios** con `VRFY` o `EXPN`.
- **Enviar correos falsos** si no requiere autenticación.
- **Fuerza bruta** si requiere autenticación.

---

## 🎯 Banners SMTP comunes

| Banner | Significado |
|---|---|
| `220 mail.local ESMTP Postfix` | Postfix (Linux) |
| `220 smtp.local ESMTP Exim 4.94` | Exim (Linux) |
| `220 mail.local ESMTP Sendmail 8.15` | Sendmail (Linux) |
| `220 mail.local Microsoft ESMTP MAIL Service` | Exchange (Windows) |

El banner revela el software del servidor.

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos SMTP de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** los servidores SMTP registran conexiones. En entornos empresariales, te detectarán.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto.
- **Puerto alternativo:** SMTP también usa el puerto 587 (submission) y 465 (SMTPS). **SMTP Scan** por defecto solo prueba el 25.
- **Spam:** no uses un servidor SMTP ajeno para enviar correo. Es **delito** y puede meterte en problemas legales graves.

---

## 🔗 Relacionado

- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Port Scan All](port-scan-all.md) — para buscar SMTP en puertos alternativos
- [DNS Scan](dns-scan.md) — protocolo relacionado con correo
- [HTTP Scan](http-scan.md) — para buscar paneles de administración
