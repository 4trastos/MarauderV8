# 📡 Ping Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Ping Scan** envía paquetes **ICMP Echo Request** (pings) a un rango de direcciones IP para descubrir **hosts vivos** en la red. Es el primer paso de cualquier auditoría de red: saber qué dispositivos están activos.

A diferencia de los sniffers (que solo escuchan), **Ping Scan** genera tráfico activo hacia la red.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → Ping Scan**.
3. Introduce el **rango de IPs** a escanear (por defecto: `192.168.1.0/24`).
4. Configura el **timeout** por host (por defecto: 1 segundo).
5. Pulsa **Start**.
6. El Marauder enviará pings secuencialmente y mostrará los hosts que respondan.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear (CIDR) | `192.168.1.0/24` |
| **Timeout** | Tiempo de espera por host | 1000 ms |
| **Reintentos** | Nº de pings por host | 1 |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Ping Scan ===
Rango: 192.168.1.0/24
Timeout: 1000 ms

Hosts vivos:
192.168.1.1     (router)
192.168.1.5     (portátil)
192.168.1.10    (móvil)
192.168.1.15    (impresora)
192.168.1.20    (NAS)
...

Total: 5 hosts vivos de 254 escaneados
Tiempo: 12 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Hostname (si se resuelve),MAC (si está en ARP),RTT
192.168.1.1,router.local,FA:8F:CA:61:05:78,2ms
192.168.1.5,portatil.local,3C:5A:B4:12:34:56,5ms
...
```

---

## 🎯 Para qué sirve

### 1. Inventario de red

El caso de uso principal. **Ping Scan** te dice **cuántos dispositivos hay** en la red y **cuáles están activos**.

Útil para:

- Saber cuántos dispositivos hay en tu casa.
- Detectar dispositivos no autorizados.
- Documentar una red antes de una auditoría.

### 2. Base para otros scanners

**Ping Scan** es el paso previo a:

- **Port Scan All** (solo escanear hosts vivos).
- **SSH Scan** (solo hosts con SSH).
- **HTTP Scan** (solo hosts con web).

Sin saber qué hosts hay, no puedes escanear servicios.

### 3. Diagnóstico de conectividad

Si un dispositivo no responde a ping:

- Está apagado.
- Está en otra red.
- Tiene el firewall bloqueando ICMP.
- Está mal configurado.

### 4. Detección de intrusos

Si haces ping scan periódicamente, puedes ver **cuándo aparece un dispositivo nuevo**. Útil para:

- Detectar si alguien se ha conectado a tu red.
- Vigilar tu red doméstica.
- Auditar una oficina.

---

## 🎯 Diferencias con `nmap`

| Aspecto | Ping Scan (Marauder) | nmap |
|---|---|---|
| **Dónde corre** | En el ESP32 | En un PC |
| **Complejidad** | Simple | Muy completo |
| **Salida** | Lista de hosts | Lista + detalles + scripts |
| **Velocidad** | Media | Rápida |
| **Uso** | Rápido, portátil | Auditoría completa |

**En la práctica:** usa **Ping Scan** para un inventario rápido desde el Marauder, y `nmap` desde el PC para análisis profundos.

---

## ⚠️ Advertencias

- **Legalidad:** escanear una red ajena es **delito**. Solo en tu red o con autorización.
- **Detección:** algunos firewalls bloquean ICMP y no verás los hosts. En ese caso, prueba con ARP scan.
- **Velocidad:** escanear un /24 (254 hosts) tarda 10-30 segundos. Un /16 (65.534 hosts) puede tardar horas.
- **IPv6:** la mayoría de firmwares solo soportan IPv4. Si tu red es IPv6, no funcionará.
- **WiFi:** el Marauder debe estar conectado a la red WiFi objetivo. Si no, no puede enviar pings.
- **Batería:** un scan largo consume batería.

---

## 🔗 Relacionado

- [Port Scan All](port-scan-all.md) — siguiente paso tras identificar hosts
- [SSH Scan](ssh-scan.md) — para buscar SSH
- [HTTP Scan](http-scan.md) — para buscar webs
- [Join WiFi](../general/join-wifi.md) — para conectar el Marauder a la red