# 📡 ESP32 Marauder v8 — Documentación completa

[⬅️ Volver al índice principal](../../README.md)

---

Guía completa de todas las funciones del **ESP32 Marauder v8**, organizadas por módulo. Cada sección documenta las herramientas disponibles, cómo usarlas y para qué sirven en un contexto de auditoría WiFi/Bluetooth.

## 📑 Índice de módulos

| Módulo | Descripción | Estado |
|---|---|---|
| [📶 WiFi](wifi/README.md) | Sniffers, scanners, ataques y configuración WiFi | ✅ Documentado |
| [🔵 Bluetooth](bluetooth/README.md) | Escaneo, sniffing y ataques BLE | ✅ Documentado |
| [🛰️ GPS](gps/README.md) | Wardriving, geolocalización y logs GPS | ✅ Documentado |

---

## 📶 WiFi

El módulo principal del Marauder. Cubre desde la captura pasiva de handshakes hasta ataques activos contra redes y clientes.

**Subsecciones:**

- [🔍 Sniffers](wifi/README.md#-sniffers) — Captura pasiva (EAPOL/PMKID, beacons, probes, etc.)
- [📡 Scanners](wifi/README.md#-scanners) — Descubrimiento activo de servicios (ping, puertos, SSH, etc.)
- [⚔️ Attacks](wifi/README.md#️-attacks) — Herramientas ofensivas (deauth, evil portal, karma, etc.)
- [⚙️ General](wifi/README.md#️-general) — Configuración y utilidades del dispositivo

**Acceso directo:**

- [📖 Ver índice completo de WiFi](wifi/README.md)

---

## 🔵 Bluetooth

Módulo de auditoría Bluetooth Low Energy (BLE). Permite escanear dispositivos cercanos, capturar anuncios y analizar el tráfico BLE.

**Contenido previsto:**

- BLE Scan
- BLE Sniff
- AirTag Sniffer
- Flipper Sniffer
- BLE Spam
- BT Info

**Acceso directo:**

- [📖 Ver índice de Bluetooth](bluetooth/README.md)

---

## 🛰️ GPS

Módulo de geolocalización. Se usa junto con el módulo WiFi para **wardriving**: registrar redes y dispositivos junto a sus coordenadas GPS.

**Contenido previsto:**

- GPS Info
- GPS Data
- Wardrive (integrado con WiFi)
- Logs WigleWifi CSV

**Acceso directo:**

- [📖 Ver índice de GPS](gps/README.md)

---

## ⚠️ Uso legal

Todas las funciones de este dispositivo (**especialmente las de la sección `Attacks`**) deben usarse únicamente en:

- **Tu propia red**
- **Redes con autorización explícita por escrito** (pentest contratado)
- **Laboratorios aislados** (CTF, entornos de práctica)

El uso contra redes de terceros es **delito** en España (art. 197 bis y 264 del Código Penal) y en la mayoría de jurisdicciones.

**Wardriving responsable**: registrar redes abiertas con GPS es legal en muchos países, pero **interactuar con ellas** (conectarse, inyectar tráfico) no lo es.

---

## 🔗 Recursos relacionados

- [Repositorio oficial del ESP32 Marauder](https://github.com/justcallmekoko/ESP32Marauder)
- [Wiki oficial del Marauder](https://github.com/justcallmekoko/ESP32Marauder/wiki)
- [Guía NIST de auditoría WiFi](../README.md)
- [WiGLE — Base de datos mundial de redes WiFi](https://wigle.net/)
