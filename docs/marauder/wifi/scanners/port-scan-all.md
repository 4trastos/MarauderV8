# 📡 Port Scan All

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Port Scan All** escanea los **65535 puertos TCP** de un host para descubrir **qué servicios están abiertos**. Es la herramienta más completa (y lenta) de escaneo de puertos del Marauder.

A diferencia de los scanners específicos (SSH, HTTP, etc.), **Port Scan All** no se limita a un puerto concreto: los prueba todos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → Port Scan All**.
3. Introduce la **IP objetivo** (por defecto: la del gateway).
4. Configura el **timeout** por puerto (por defecto: 500 ms).
5. Pulsa **Start**.
6. El Marauder escaneará los 65535 puertos secuencialmente y mostrará los abiertos.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **IP objetivo** | IP a escanear | Gateway |
| **Rango de puertos** | Puertos a escanear | 1-65535 |
| **Timeout** | Tiempo de espera por puerto | 500 ms |
| **Hilos** | Escaneos en paralelo | 1 |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Port Scan All ===
Objetivo: 192.168.1.1
Rango: 1-65535
Timeout: 500 ms

Puertos abiertos:
22    (SSH)
53    (DNS)
80    (HTTP)
443   (HTTPS)
8080  (HTTP alternativo)

Total: 5 puertos abiertos de 65535 escaneados
Tiempo: ~9 horas (a 500ms por puerto)
```

### En la SD

Un archivo `.txt`:

```text
Port,Service,Banner
22,SSH,SSH-2.0-OpenSSH_8.2p1
53,DNS,—
80,HTTP,Server: nginx/1.18.0
443,HTTPS,—
8080,HTTP,Server: Apache/2.4.41
```

---

## 🎯 Para qué sirve

### 1. Inventario completo de servicios

Si quieres saber **todo** lo que un host expone a la red, **Port Scan All** es la herramienta. Te dice:

- Qué puertos están abiertos.
- Qué servicios corren en cada uno.
- Qué versión del servicio (si el banner lo revela).

### 2. Auditoría de seguridad

Un host con muchos puertos abiertos es **más vulnerable**. **Port Scan All** te ayuda a:

- Detectar servicios no autorizados.
- Ver si hay puertos peligrosos abiertos (Telnet, FTP, SMB).
- Documentar la superficie de ataque.

### 3. Base para ataques específicos

Si encuentras un puerto abierto, puedes:

- **SSH (22)** → intentar fuerza bruta.
- **HTTP (80)** → buscar vulnerabilidades web.
- **SMB (445)** → buscar shares abiertos.
- **RDP (3389)** → intentar conexión remota.

### 4. Diagnóstico de red

Si un servicio no funciona, **Port Scan All** te dice si el puerto está abierto:

- Si está **abierto** → el servicio corre, problema en otro sitio.
- Si está **cerrado** → el servicio no corre o el firewall lo bloquea.

---

## 🎯 Diferencias con scanners específicos

| Aspecto | Port Scan All | SSH Scan / HTTP Scan / etc. |
|---|---|---|
| **Puertos** | 65535 | 1 |
| **Tiempo** | Horas | Segundos |
| **Uso** | Inventario completo | Búsqueda específica |
| **Carga en la red** | Alta | Baja |
| **Detección** | Fácil (muchos paquetes) | Difícil |

**En la práctica:** empieza con los scanners específicos (SSH, HTTP, etc.). Si no encuentras lo que buscas, lanza **Port Scan All**.

---

## ⚠️ Advertencias

- **Lentitud:** escanear 65535 puertos a 500 ms por puerto tarda **~9 horas**. Reduce el rango o el timeout si tienes prisa.
- **Legalidad:** escanear puertos de un host ajeno es **delito**. Solo en tu red o con autorización.
- **Detección:** los IDS/IPS detectan fácilmente un port scan completo. En entornos empresariales, te detectarán.
- **Saturación:** 65535 paquetes en poco tiempo pueden saturar la red.
- **Firewall:** algunos firewalls responden con "RST" (puerto cerrado) y otros no responden (timeout). Los timeouts ralentizan mucho el scan.
- **IPv6:** la mayoría de firmwares solo soportan IPv4.

---

## 🔗 Relacionado

- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [SSH Scan](ssh-scan.md) — específico para SSH
- [HTTP Scan](http-scan.md) — específico para HTTP
- [HTTPS Scan](https-scan.md) — específico para HTTPS
- [RDP Scan](rdp-scan.md) — específico para RDP