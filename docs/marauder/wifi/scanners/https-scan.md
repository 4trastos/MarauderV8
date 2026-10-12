# 📡 HTTPS Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**HTTPS Scan** busca **servidores web HTTPS** (puerto 443) en la red. HTTPS es la versión **cifrada** de HTTP: usa TLS/SSL para proteger el tráfico entre el cliente y el servidor.

Encontrar un servidor HTTPS en tu red es normal si tienes:

- Un router con panel de administración moderno.
- Un NAS con interfaz web segura.
- Una cámara IP moderna.
- Un servidor web con certificado SSL.

A diferencia de HTTP, HTTPS **cifra el tráfico**, así que no puedes ver el contenido sin la clave. Pero sí puedes ver:

- El **certificado SSL** del servidor.
- El **título** de la página (a veces).
- El **software** del servidor (a veces).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → HTTPS Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 1000 ms, HTTPS es más lento).
5. Pulsa **Start**.
6. El Marauder probará el puerto 443 en cada IP y mostrará los hosts con HTTPS abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto HTTPS (por defecto 443) | 443 |
| **Timeout** | Tiempo de espera | 1000 ms |
| **Certificado** | Capturar info del certificado | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== HTTPS Scan ===
Rango: 192.168.1.0/24
Puerto: 443
Timeout: 1000 ms

Servidores HTTPS encontrados:
192.168.1.1     CN=router.local (self-signed)
192.168.1.20    CN=nas.local (Let's Encrypt)
192.168.1.30    CN=camera.local (self-signed)

Total: 3 servidores HTTPS de 254 escaneados
Tiempo: 15 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,CN,Issuer,ValidFrom,ValidTo
192.168.1.1,443,router.local,self-signed,2026-01-01,2027-01-01
192.168.1.20,443,nas.local,Let's Encrypt,2026-09-01,2027-09-01
192.168.1.30,443,camera.local,self-signed,2026-01-01,2027-01-01
```

El **CN** (Common Name) y el **emisor** del certificado revelan mucho sobre el dispositivo.

---

## 🎯 Para qué sirve

### 1. Inventario de servidores HTTPS

Saber qué dispositivos tienen HTTPS es útil para:

- Documentar la red.
- Saber qué dispositivos son modernos (usan cifrado).
- Identificar dispositivos por su certificado.

### 2. Detección de certificados autofirmados

Un certificado **autofirmado** (`self-signed`) es normal en:

- Routers domésticos.
- Cámaras IP.
- Dispositivos IoT.

Pero también puede indicar:

- Dispositivo mal configurado.
- Dispositivo antiguo.
- Intento de suplantación.

**HTTPS Scan** te dice qué certificados usan los dispositivos.

### 3. Detección de dispositivos modernos

Los dispositivos que usan **Let's Encrypt** o certificados de CA conocidas son más modernos y seguros que los que usan autofirmados.

### 4. Base para ataques

Si encuentras un servidor HTTPS, puedes:

- **Ver el certificado** para saber qué software corre.
- **Probar credenciales** por defecto.
- **Buscar vulnerabilidades** en la versión de TLS/SSL.

---

## 🎯 Tipos de certificados

| Tipo | Significado |
|---|---|
| **Self-signed** | Generado por el propio dispositivo. No verificado por CA. |
| **Let's Encrypt** | CA gratuita. Certificado válido y verificado. |
| **CA comercial** | DigiCert, GlobalSign, etc. Certificado de pago. |
| **Expirado** | El certificado ha caducado. El navegador avisará. |
| **Wildcard** | Válido para varios subdominios (`*.local`). |

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos HTTPS de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** los servidores HTTPS registran accesos en sus logs.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto.
- **HTTPS es más lento:** el handshake TLS tarda más que HTTP. El scan es más lento.
- **Puertos alternativos:** muchos paneles usan puertos alternativos (8443, 9443). **Port Scan All** te ayuda.
- **Certificado no siempre visible:** algunos servidores no revelan el certificado sin completar el handshake TLS.
- **Credenciales por defecto:** probar credenciales por defecto en dispositivos ajenos es **delito**. Solo en tu red.

---

## 🔗 Relacionado

- [HTTP Scan](http-scan.md) — versión sin cifrar
- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Port Scan All](port-scan-all.md) — para buscar HTTPS en puertos alternativos
- [SSH Scan](ssh-scan.md) — alternativa segura a paneles web