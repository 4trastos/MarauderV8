# 📡 HTTP Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**HTTP Scan** busca **servidores web HTTP** (puerto 80) en la red. HTTP (*HyperText Transfer Protocol*) es el protocolo de la web. Encontrar un servidor HTTP en tu red es normal si tienes:

- Un router con panel de administración web.
- Una impresora con interfaz web.
- Un NAS con interfaz web.
- Una cámara IP con interfaz web.
- Un servidor web propio.

Pero también puede ser un **riesgo** si:

- Tiene credenciales por defecto.
- Tiene vulnerabilidades conocidas.
- Expone información sensible.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → HTTP Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 500 ms).
5. Pulsa **Start**.
6. El Marauder probará el puerto 80 en cada IP y mostrará los hosts con HTTP abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto HTTP (por defecto 80) | 80 |
| **Timeout** | Tiempo de espera | 500 ms |
| **Título** | Capturar título de la página | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== HTTP Scan ===
Rango: 192.168.1.0/24
Puerto: 80
Timeout: 500 ms

Servidores HTTP encontrados:
192.168.1.1     "Router Admin Panel" (nginx)
192.168.1.15    "HP LaserJet" (HP)
192.168.1.20    "Synology NAS" (nginx)
192.168.1.30    "IP Camera" (Boa)

Total: 4 servidores HTTP de 254 escaneados
Tiempo: 12 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,Title,Server
192.168.1.1,80,Router Admin Panel,nginx/1.18.0
192.168.1.15,80,HP LaserJet,HP-HTTP
192.168.1.20,80,Synology NAS,nginx
192.168.1.30,80,IP Camera,Boa/0.94
```

El **título** y el **servidor** revelan mucho sobre el dispositivo.

---

## 🎯 Para qué sirve

### 1. Inventario de dispositivos con web

Saber qué dispositivos tienen interfaz web es útil para:

- Documentar la red.
- Saber a qué dispositivos puedes acceder.
- Identificar dispositivos por su título.

### 2. Detección de dispositivos IoT

Muchos dispositivos IoT (cámaras, impresoras, NAS) tienen interfaz web. **HTTP Scan** te los revela.

### 3. Auditoría de seguridad

Un servidor HTTP es un **punto de entrada**. Si está mal configurado:

- Credenciales por defecto → acceso no autorizado.
- Vulnerabilidades conocidas → explotación.
- Sin autenticación → acceso libre.

**HTTP Scan** te dice qué servidores hay y qué software corren.

### 4. Base para ataques

Si encuentras un servidor HTTP, puedes:

- **Acceder** al panel de administración.
- **Probar credenciales** por defecto (`admin/admin`, `root/root`).
- **Buscar vulnerabilidades** en la versión del servidor.

---

## 🎯 Títulos HTTP comunes y qué revelan

| Título | Dispositivo |
|---|---|
| `Router Admin Panel` | Router |
| `HP LaserJet` | Impresora HP |
| `Synology NAS` | NAS Synology |
| `IP Camera` | Cámara IP |
| `Pi-hole Admin` | Pi-hole |
| `OpenWrt` | Router con OpenWrt |
| `Apache2 Ubuntu Default Page` | Servidor Ubuntu por defecto |

El título te dice **qué dispositivo es** sin necesidad de acceder.

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos HTTP de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** los servidores HTTP registran accesos en sus logs. En entornos empresariales, te detectarán.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto.
- **HTTPS:** muchos servidores usan HTTPS (443) en lugar de HTTP (80). **HTTPS Scan** te los revela.
- **Puertos alternativos:** muchos paneles usan puertos alternativos (8080, 8000, 8443). **Port Scan All** te ayuda.
- **Credenciales por defecto:** probar credenciales por defecto en dispositivos ajenos es **delito**. Solo en tu red.

---

## 🔗 Relacionado

- [HTTPS Scan](https-scanner.md) — para servidores con cifrado
- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Port Scan All](port-scan-all.md) — para buscar HTTP en puertos alternativos
- [SSH Scan](ssh-scan.md) — alternativa segura a paneles web
- [Raw Capture](../sniffers/raw-capture.md) — para capturar tráfico HTTP en claro
