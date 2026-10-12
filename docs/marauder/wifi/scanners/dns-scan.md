# 📡 DNS Scan

[⬅️ Volver al índice Scanners](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**DNS Scan** busca **servidores DNS** (puerto 53) en la red. DNS (*Domain Name System*) es el protocolo que traduce **nombres de dominio** (`google.com`) a **direcciones IP** (`142.250.184.14`).

Encontrar un servidor DNS en tu red es normal si tienes:

- Un router que hace de DNS local.
- Un servidor DNS propio (Pi-hole, AdGuard Home, BIND).
- Un NAS con DNS.

Pero también puede ser un **riesgo** si:

- Está mal configurado (open resolver).
- Permite consultas recursivas desde fuera.
- Puede ser usado para **amplificación DNS** (DDoS).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Conecta el Marauder a la red objetivo (con **Join WiFi**).
2. Navega hasta **WiFi → Scanners → DNS Scan**.
3. Introduce el **rango de IPs** a escanear.
4. Configura el **timeout** (por defecto: 500 ms).
5. Pulsa **Start**.
6. El Marauder probará el puerto 53 en cada IP (TCP y UDP) y mostrará los hosts con DNS abierto.
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Rango IP** | Rango a escanear | `192.168.1.0/24` |
| **Puerto** | Puerto DNS (por defecto 53) | 53 |
| **Protocolo** | TCP, UDP o ambos | Ambos |
| **Timeout** | Tiempo de espera | 500 ms |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== DNS Scan ===
Rango: 192.168.1.0/24
Puerto: 53
Protocolo: TCP + UDP
Timeout: 500 ms

Servidores DNS encontrados:
192.168.1.1     (router, DNS forwarder)
192.168.1.100   (Pi-hole, DNS recursivo)

Total: 2 servidores DNS de 254 escaneados
Tiempo: 12 segundos
```

### En la SD

Un archivo `.txt`:

```text
IP,Port,Protocol,Type
192.168.1.1,53,TCP,Forwarder
192.168.1.1,53,UDP,Forwarder
192.168.1.100,53,TCP,Recursive
192.168.1.100,53,UDP,Recursive
```

---

## 🎯 Para qué sirve

### 1. Inventario de servidores DNS

Saber qué dispositivos hacen de DNS es útil para:

- Documentar la red.
- Entender cómo se resuelven los nombres.
- Detectar DNS no autorizados.

### 2. Detección de open resolvers

Un **open resolver** es un servidor DNS mal configurado que **responde a consultas de cualquiera**. Es un riesgo porque:

- Los atacantes lo usan para **amplificación DNS** (DDoS).
- Tu IP puede acabar en listas negras.
- Puedes recibir quejas de tu ISP.

**DNS Scan** te dice si hay servidores DNS. Luego puedes probar si son open resolvers.

### 3. Detección de DNS maliciosos

Un atacante puede levantar un **DNS falso** en tu red para:

- Redirigir dominios a IPs maliciosas.
- Interceptar tráfico.
- Hacer phishing.

**DNS Scan** te ayuda a detectar servidores DNS no autorizados.

### 4. Base para ataques

Si encuentras un servidor DNS, puedes:

- **Enumerar** dominios internos.
- **Amplificación DNS** (si es open resolver).
- **DNS spoofing** (si puedes interceptar consultas).

---

## 🎯 Tipos de servidores DNS

| Tipo | Descripción |
|---|---|
| **Forwarder** | Reenvía consultas a otro DNS (típico en routers) |
| **Recursive** | Resuelve consultas por sí mismo (Pi-hole, BIND) |
| **Authoritative** | Sirve zonas propias (servidores de dominio) |
| **Caching** | Cachea respuestas para acelerar consultas |

---

## ⚠️ Advertencias

- **Legalidad:** escanear puertos DNS de hosts ajenos es **delito**. Solo en tu red o con autorización.
- **Detección:** los servidores DNS registran consultas. En entornos empresariales, te detectarán.
- **UDP vs TCP:** DNS usa principalmente UDP (puerto 53), pero también TCP para respuestas grandes. Algunos servidores solo responden a uno.
- **Falsos positivos:** algunos firewalls responden como si el puerto estuviera abierto.
- **Puerto alternativo:** DNS over HTTPS (DoH) usa el 443, y DNS over TLS (DoT) usa el 853. **DNS Scan** por defecto solo prueba el 53.
- **Amplificación DNS:** no uses un open resolver para ataques DDoS. Es **delito grave**.

---

## 🔗 Relacionado

- [Ping Scan](ping-scan.md) — para identificar hosts antes de escanear
- [Port Scan All](port-scan-all.md) — para buscar DNS en puertos alternativos
- [SMTP Scan](smtp-scan.md) — protocolo relacionado con correo
- [HTTP Scan](http-scan.md) — para buscar paneles de administración