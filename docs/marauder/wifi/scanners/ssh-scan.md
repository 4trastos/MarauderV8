# 📡 SSH Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**SSH Scan** busca **servidores SSH** (puerto 22) en la red. SSH (*Secure Shell*) es el protocolo estándar para administración remota segura de servidores, routers, switches y dispositivos IoT.

Encontrar un servidor SSH en tu red es normal si tienes servidores o dispositivos administrables. Pero también puede ser un **riesgo de seguridad** si:

- Usa contraseñas débiles.
- Tiene versiones antiguas con vulnerabilidades.
- No está detrás de un firewall.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → SSH Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 500 ms).
5. Pulsa **Start**.
6. El Marauder probará el puerto 22 en cada IP y mostrará los hosts con SSH abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto SSH (por defecto 22) | 22 |
| **Timeout** | Tiempo de espera | 500 ms |
| **Banner** | Capturar banner SSH | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== SSH Scan ===
Rango: 192.168.1.0/24
Puerto: 22
Timeout: 500 ms

Servidores SSH encontrados:
192.168.1.1     SSH-2.0-OpenSSH_8.2p1
192.168.1.20    SSH-2.0-OpenSSH_7.4
192.168.1.50    SSH-2.0-Dropbear_2019.78

Total: 3 servidores SSH de 254 escaneados
Tiempo: 15 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,Banner
192.168.1.1,22,SSH-2.0-OpenSSH_8.2p1
192.168.1.20,22,SSH-2.0-OpenSSH_7.4
192.168.1.50,22,SSH-2.0-Dropbear_2019.78
```

El **banner** revela la versión del servidor SSH. Eso es información valiosa para un atacante (sabe qué vulnerabilidades buscar).

---

## 🎯 Para qué sirve

### 1. Inventario de servidores SSH

Saber qué dispositivos tienen SSH abierto es útil para:

- Documentar la red.
- Saber a qué dispositivos puedes conectarte.
- Identificar dispositivos administrables.

### 2. Auditoría de seguridad

Un servidor SSH es un **punto de entrada**. Si está mal configurado:

- Contraseñas débiles → fuerza bruta.
- Versión antigua → vulnerabilidades conocidas.
- Sin firewall → expuesto a la red.

**SSH Scan** te dice qué servidores hay y qué versión corren.

### 3. Base para ataques

Si encuentras un servidor SSH, puedes:

- **Fuerza bruta** con `hydra` o `medusa`.
- **Explotar** vulnerabilidades de la versión.
- **Verificar** si acepta contraseñas vacías.

### 4. Diagnóstico

Si no puedes conectarte por SSH a un servidor:

- **SSH Scan** te dice si el puerto está abierto.
- Si está abierto, el problema es de credenciales.
- Si está cerrado, el problema es de red o servicio.

---

## 🎯 Banners SSH comunes

| Banner | Significado |
|---|---|
| `SSH-2.0-OpenSSH_8.2p1` | OpenSSH 8.2 en Ubuntu 20.04 |
| `SSH-2.0-OpenSSH_7.4` | OpenSSH 7.4 en CentOS 7 |
| `SSH-2.0-Dropbear_2019.78` | Dropbear en routers/IoT |
| `SSH-2.0-Cisco-1.25` | Cisco IOS |
| `SSH-2.0-ROSSSH` | RouterOS (Mikrotik) |

El banner te dice **qué sistema operativo** corre el servidor y **qué versión** de SSH. Eso te permite buscar vulnerabilidades específicas.

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos SSH de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** los servidores SSH suelen registrar los intentos de conexión. En entornos empresariales, te detectarán.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto aunque no lo esté.
- **Banner grabbing:** algunos servidores no revelan su banner. Verás `—` en lugar de la versión.
- **Puerto alternativo:** algunos administradores cambian SSH al puerto 2222 o similar. **SSH Scan** por defecto solo prueba el 22.

---

## 🔗 Relacionado

- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Port Scan All](port-scan-all.md) — para buscar SSH en puertos alternativos
- [Telnet Scan](telnet-scan.md) — protocolo similar pero inseguro
- [HTTP Scan](http-scan.md) — para buscar webs