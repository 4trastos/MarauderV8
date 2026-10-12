# 📡 Telnet Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Telnet Scan** busca **servidores Telnet** (puerto 23) en la red. Telnet es un protocolo de administración remota **muy antiguo e inseguro**: envía todo el tráfico **en claro**, incluyendo usuario y contraseña.

Encontrar un servidor Telnet en tu red es **una mala señal**:

- Es un protocolo obsoleto (sustituido por SSH).
- Transmite credenciales sin cifrar.
- Suele estar en dispositivos IoT antiguos o mal configurados.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → Telnet Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 500 ms).
5. Pulsa **Start**.
6. El Marauder probará el puerto 23 en cada IP y mostrará los hosts con Telnet abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto Telnet (por defecto 23) | 23 |
| **Timeout** | Tiempo de espera | 500 ms |
| **Banner** | Capturar banner Telnet | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Telnet Scan ===
Rango: 192.168.1.0/24
Puerto: 23
Timeout: 500 ms

Servidores Telnet encontrados:
192.168.1.30    BusyBox telnetd
192.168.1.45    Cisco IOS Telnet

Total: 2 servidores Telnet de 254 escaneados
Tiempo: 12 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,Banner
192.168.1.30,23,BusyBox telnetd
192.168.1.45,23,Cisco IOS Telnet
```

---

## 🎯 Para qué sirve

### 1. Detectar dispositivos inseguros

Telnet es **inseguro por diseño**. Si encuentras un servidor Telnet en tu red:

- Está mal configurado.
- Probablemente sea un dispositivo IoT antiguo.
- Sus credenciales viajan sin cifrar.

**Telnet Scan** te ayuda a detectar estos dispositivos y **remediarlos**.

### 2. Inventario de dispositivos IoT

Muchos dispositivos IoT antiguos (cámaras, routers, impresoras) usan Telnet para administración. **Telnet Scan** te los revela.

### 3. Base para ataques

Telnet es **muy fácil de atacar**:

- Credenciales por defecto (`admin/admin`, `root/root`).
- Sin cifrado → captura de credenciales con **Raw Capture**.
- Sin bloqueo por intentos → fuerza bruta ilimitada.

### 4. Auditoría de cumplimiento

Si auditas una red para cumplimiento (ISO 27001, PCI-DSS), **Telnet Scan** te dice si hay dispositivos con Telnet abierto. Eso es **no conforme**.

---

## 🎯 Diferencias con SSH Scan

| Aspecto | Telnet | SSH |
|---|---|---|
| **Puerto** | 23 | 22 |
| **Cifrado** | **No** (todo en claro) | Sí (AES, ChaCha20) |
| **Autenticación** | Usuario + contraseña en claro | Clave pública o contraseña cifrada |
| **Seguridad** | **Obsoleto** | Estándar actual |
| **Uso** | IoT antiguo, routers viejos | Servidores, routers modernos |
| **Riesgo** | **Alto** | Bajo (si está bien configurado) |

**En la práctica:** si encuentras Telnet, considera **deshabilitarlo** y usar SSH.

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos Telnet de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** Telnet no suele registrar intentos, pero algunos dispositivos sí.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto.
- **Banner grabbing:** algunos servidores no revelan banner. Verás `—`.
- **Puerto alternativo:** algunos administradores cambian Telnet a otro puerto. **Port Scan All** te ayuda a encontrarlo.
- **Riesgo real:** si encuentras Telnet en tu red, **deshabilítalo ya**. Es un riesgo de seguridad.

---

## 🔗 Relacionado

- [SSH Scan](ssh-scan.md) — alternativa segura a Telnet
- [Port Scan All](port-scan-all.md) — para buscar Telnet en puertos alternativos
- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Raw Capture](../sniffers/raw-capture.md) — para capturar credenciales Telnet en claro
