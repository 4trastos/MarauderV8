# 📡 RDP Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**RDP Scan** busca **servidores RDP** (puerto 3389) en la red. RDP (*Remote Desktop Protocol*) es el protocolo de **escritorio remoto** de Microsoft. Permite conectarte a un Windows y controlarlo como si estuvieras delante.

Encontrar un servidor RDP en tu red es normal si tienes:

- Un Windows con escritorio remoto habilitado.
- Un servidor Windows para administración remota.
- Un equipo al que te conectas desde casa.

Pero también puede ser un **riesgo grave** si:

- Está expuesto a internet.
- Tiene credenciales débiles.
- No tiene autenticación de dos factores.

RDP es uno de los **vectores de ataque más usados** en ransomware. Si encuentras RDP en tu red, asegúrate de que está bien protegido.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → RDP Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 1000 ms).
5. Pulsa **Start**.
6. El Marauder probará el puerto 3389 en cada IP y mostrará los hosts con RDP abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto RDP (por defecto 3389) | 3389 |
| **Timeout** | Tiempo de espera | 1000 ms |
| **NLA** | Detectar si requiere NLA | Sí |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== RDP Scan ===
Rango: 192.168.1.0/24
Puerto: 3389
Timeout: 1000 ms

Servidores RDP encontrados:
192.168.1.50    Windows 10 Pro (NLA: sí)
192.168.1.60    Windows Server 2019 (NLA: sí)

Total: 2 servidores RDP de 254 escaneados
Tiempo: 15 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,OS,NLA
192.168.1.50,3389,Windows 10 Pro,sí
192.168.1.60,3389,Windows Server 2019,sí
```

---

## 🎯 Para qué sirve

### 1. Inventario de servidores RDP

Saber qué dispositivos tienen RDP abierto es útil para:

- Documentar la red.
- Saber a qué equipos puedes conectarte.
- Auditar la seguridad de la red.

### 2. Detección de riesgos

RDP es un **vector de ataque crítico**. Si encuentras RDP en tu red:

- **Verifica** que está detrás de un firewall.
- **Verifica** que requiere NLA (Network Level Authentication).
- **Verifica** que usa contraseñas fuertes.
- **Verifica** que tiene 2FA si es posible.

**RDP Scan** te dice si hay RDP y si requiere NLA.

### 3. Detección de dispositivos no autorizados

Si alguien ha habilitado RDP sin autorización, **RDP Scan** te lo revela. Eso puede ser:

- Un usuario despistado.
- Un administrador negligente.
- Un atacante que ha comprometido un equipo.

### 4. Base para ataques

Si encuentras RDP, puedes:

- **Fuerza bruta** con `hydra` o `ncrack`.
- **Explotar** vulnerabilidades (BlueKeep, etc.).
- **Conectar** si tienes credenciales.

---

## 🎯 NLA (Network Level Authentication)

**NLA** es una capa de autenticación que requiere que el cliente se autentique **antes** de establecer la sesión RDP. Es una medida de seguridad importante.

| NLA | Significado |
|---|---|
| **Sí** | El servidor requiere autenticación previa. Más seguro. |
| **No** | El servidor permite conectar sin autenticación previa. **Menos seguro.** |

Si encuentras un servidor RDP **sin NLA**, es un riesgo grave.

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos RDP de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** los servidores RDP registran intentos de conexión. En entornos empresariales, te detectarán.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto.
- **Puertos alternativos:** algunos administradores cambian RDP a otro puerto. **Port Scan All** te ayuda.
- **RDP expuesto a internet:** si tu RDP está expuesto a internet, **ciérralo ya**. Es uno de los vectores de ransomware más usados.
- **BlueKeep:** una vulnerabilidad crítica de RDP (CVE-2019-0708) que permite ejecución remota de código. Si tienes RDP sin parchear, estás en riesgo.

---

## 🔗 Relacionado

- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Port Scan All](port-scan-all.md) — para buscar RDP en puertos alternativos
- [SSH Scan](ssh-scan.md) — alternativa segura en Linux
- [HTTP Scan](http-scan.md) — para buscar paneles de administración
- [HTTPS Scan](https-scanner.md) — para servidores web seguros
```

---

### 🗂️ Estructura actualizada

```text
docs/marauder/wifi/
├── README.md                         ✅
├── sniffers/                          ✅ 100% COMPLETADO (17 archivos)
├── scanners/                          ✅ 100% COMPLETADO (9 archivos + README)
│   ├── README.md                     ✅ (nuevo)
│   ├── ping-scan.md                  ✅ (nuevo)
│   ├── port-scan-all.md              ✅ (nuevo)
│   ├── ssh-scan.md                   ✅ (nuevo)
│   ├── telnet-scan.md                ✅ (nuevo)
│   ├── smtp-scan.md                  ✅ (nuevo)
│   ├── dns-scan.md                   ✅ (nuevo)
│   ├── http-scan.md                  ✅ (nuevo)
│   ├── https-scan.md                 ✅ (nuevo)
│   └── rdp-scan.md                   ✅ (nuevo)
├── attacks/
│   ├── deauth-targeted.md            ✅
│   ├── deauth-flood.md               ✅
│   └── ...                           ⏳ 15 más pendientes
└── general/                          ⏳ 16 archivos pendientes
```

---

### 🎉 Scanners completados

Con estos 9 archivos + el README, la sección **Scanners** queda **100% documentada**. Son 10 archivos en total.

---

### 🎯 Siguiente bloque

Ahora toca elegir entre:

- **Opción A:** `attacks/` completo → quedan 15 archivos (beacon spam list, beacon spam random, funny ssid, rick roll, probe flood, evil portal, ap clone spam, karma, bad msg, bad msg targeted, assoc sleep, assoc sleep targ, sae commit flood, channel switch, quiet time)
- **Opción B:** `general/` completo → 16 archivos (generate SSIDs, select probe SSIDs, add SSIDs, clear SSIDs, clear APs, clear stations, select EP HTML, select APs, view AP info, select stations, join wifi, join saved wifi, start AP, host AP info, set MACs, shutdown wifi)

¿Cuál prefieres?