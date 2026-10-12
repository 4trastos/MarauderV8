# 📶 WiFi — Menú completo del Marauder v8

[⬅️ Volver al índice principal](../../../README.md)

---

Guía completa de todas las funciones WiFi del ESP32 Marauder v8, organizadas por categoría:

- [🔍 Sniffers](#-sniffers)
- [📡 Scanners](#-scanners)
- [⚔️ Attacks](#️-attacks)
- [⚙️ General](#️-general)

---

## 🔍 Sniffers

Herramientas de captura pasiva. Escuchan el aire sin intervenir.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **EAPOL/PMKID Scan** | Captura handshakes WPA/WPA2 o PMKIDs. La base para crackear con Hashcat. | [sniffers/eapol-pmkid.md](sniffers/eapol-pmkid.md) |
| 2 | **Probe Request Sniff** | Captura las "preguntas" de móviles/portátiles buscando redes conocidas. | [sniffers/probe-request.md](sniffers/probe-request.md) |
| 3 | **Beacon Sniff** | Escucha los "anuncios" de los routers: SSID, canal, cifrado. | [sniffers/beacon.md](sniffers/beacon.md) |
| 4 | **Deauth Sniff** | Detecta si alguien está lanzando ataques de desautenticación en tu zona. | [sniffers/deauth.md](sniffers/deauth.md) |
| 5 | **Packet Count** | Contador rápido de paquetes por tipo. Diagnóstico. | [sniffers/packet-count.md](sniffers/packet-count.md) |
| 6 | **Packet Monitor** | Estadísticas en tiempo real de las tramas que ve. | [sniffers/packet-monitor.md](sniffers/packet-monitor.md) |
| 7 | **Channel Analyzer** | Gráfico de energía WiFi por canal. Detecta saturación. | [sniffers/channel-analyzer.md](sniffers/channel-analyzer.md) |
| 8 | **Channel Summary** | Resumen numérico por canal. | [sniffers/channel-summary.md](sniffers/channel-summary.md) |
| 9 | **Raw Capture** | Captura TODO el tráfico 802.11 sin filtros. Pcap gigante. | [sniffers/raw-capture.md](sniffers/raw-capture.md) |
| 10 | **Detect Pwnagotchi** | Busca dispositivos Pwnagotchi por su firma. | [sniffers/detect-pwnagotchi.md](sniffers/detect-pwnagotchi.md) |
| 11 | **Detect Pineapple** | Busca WiFi Pineapple por su OUI de fabricante. | [sniffers/detect-pineapple.md](sniffers/detect-pineapple.md) |
| 12 | **Detect MultiSSID** | Detecta un mismo dispositivo emitiendo múltiples SSID. | [sniffers/detect-multissid.md](sniffers/detect-multissid.md) |
| 13 | **Scan AP/STA** | Escaneo general de Puntos de Acceso y Estaciones. | [sniffers/scan-ap-sta.md](sniffers/scan-ap-sta.md) |
| 14 | **Fox Hunt** | Localiza físicamente una señal por su RSSI. | [sniffers/fox-hunt.md](sniffers/fox-hunt.md) |
| 15 | **MAC Monitor** | Vigila MACs específicas y avisa cuando aparecen/desaparecen. | [sniffers/mac-monitor.md](sniffers/mac-monitor.md) |
| 16 | **SAE Commit** | Captura el intercambio inicial de WPA3 (SAE). | [sniffers/sae-commit.md](sniffers/sae-commit.md) |
| 17 | **Wardrive** | Escaneo pasivo con GPS para subir a WiGLE. | [sniffers/wardrive.md](sniffers/wardrive.md) |

---

## 📡 Scanners

Herramientas activas. **Envían tráfico** para descubrir servicios en la red.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **Ping Scan** | Envía pings ICMP para descubrir hosts vivos en la red. | [scanners/ping-scan.md](scanners/ping-scan.md) |
| 2 | **Port Scan All** | Escanea los 65535 puertos TCP de un host. | [scanners/port-scan-all.md](scanners/port-scan-all.md) |
| 3 | **SSH Scan** | Busca servidores SSH (puerto 22) en la red. | [scanners/ssh-scan.md](scanners/ssh-scan.md) |
| 4 | **Telnet Scan** | Busca servidores Telnet (puerto 23). | [scanners/telnet-scan.md](scanners/telnet-scan.md) |
| 5 | **SMTP Scan** | Busca servidores de correo SMTP (puerto 25). | [scanners/smtp-scan.md](scanners/smtp-scan.md) |
| 6 | **DNS Scan** | Busca servidores DNS (puerto 53). | [scanners/dns-scan.md](scanners/dns-scan.md) |
| 7 | **HTTP Scan** | Busca servidores web HTTP (puerto 80). | [scanners/http-scan.md](scanners/http-scan.md) |
| 8 | **HTTPS Scan** | Busca servidores web HTTPS (puerto 443). | [scanners/https-scan.md](scanners/https-scan.md) |
| 9 | **RDP Scan** | Busca servidores de escritorio remoto RDP (puerto 3389). | [scanners/rdp-scan.md](scanners/rdp-scan.md) |

---

## ⚔️ Attacks

Herramientas ofensivas. **Inyectan tráfico** para manipular redes o clientes. Solo para auditorías autorizadas.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **Beacon Spam List** | Emite beacons falsos con SSIDs de una lista predefinida. | [attacks/beacon-spam-list.md](attacks/beacon-spam-list.md) |
| 2 | **Beacon Spam Random** | Emite beacons falsos con SSIDs aleatorios. | [attacks/beacon-spam-random.md](attacks/beacon-spam-random.md) |
| 3 | **Funny SSID Beacon** | Beacons con SSIDs graciosos predefinidos. | [attacks/funny-ssid-beacon.md](attacks/funny-ssid-beacon.md) |
| 4 | **Rick Roll Beacon** | Beacons con SSIDs de canciones de Rick Astley. | [attacks/rick-roll-beacon.md](attacks/rick-roll-beacon.md) |
| 5 | **Probe Req Flood** | Inunda el aire con probe requests falsos. | [attacks/probe-req-flood.md](attacks/probe-req-flood.md) |
| 6 | **Evil Portal** | Levanta un portal captive falso para phishing. | [attacks/evil-portal.md](attacks/evil-portal.md) |
| 7 | **Deauth Flood** | Inunda con tramas de desautenticación a todos los clientes. | [attacks/deauth-flood.md](attacks/deauth-flood.md) |
| 8 | **AP Clone Spam** | Clona un AP legítimo para atraer clientes. | [attacks/ap-clone-spam.md](attacks/ap-clone-spam.md) |
| 9 | **Deauth Targeted** | Desautentica solo a un cliente específico. | [attacks/deauth-targeted.md](attacks/deauth-targeted.md) |
| 10 | **Karma** | Responde a probe requests haciéndose pasar por la red buscada. | [attacks/karma.md](attacks/karma.md) |
| 11 | **Bad Msg** | Envía tramas 802.11 malformadas a todos. | [attacks/bad-msg.md](attacks/bad-msg.md) |
| 12 | **Bad Msg Targeted** | Igual pero a un cliente específico. | [attacks/bad-msg-targeted.md](attacks/bad-msg-targeted.md) |
| 13 | **Assoc Sleep** | Fuerza a los clientes a dormir (ahorro de energía). | [attacks/assoc-sleep.md](attacks/assoc-sleep.md) |
| 14 | **Assoc Sleep Targ** | Igual pero a un cliente específico. | [attacks/assoc-sleep-targ.md](attacks/assoc-sleep-targ.md) |
| 15 | **SAE Commit Flood** | Inunda con tramas SAE Commit (WPA3). | [attacks/sae-commit-flood.md](attacks/sae-commit-flood.md) |
| 16 | **Channel Switch** | Fuerza a los clientes a cambiar de canal. | [attacks/channel-switch.md](attacks/channel-switch.md) |
| 17 | **Quiet Time** | Silencia el aire interrumpiendo transmisiones. | [attacks/quiet-time.md](attacks/quiet-time.md) |

---

## ⚙️ General

Configuración, utilidades y gestión del dispositivo.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **Generate SSIDs** | Genera una lista de SSIDs aleatorios para usar en ataques. | [general/generate-ssids.md](general/generate-ssids.md) |
| 2 | **Select Probe SSIDs** | Selecciona qué SSIDs usar en los probe requests. | [general/select-probe-ssids.md](general/select-probe-ssids.md) |
| 3 | **Add SSIDs** | Añade SSIDs manualmente a la lista. | [general/add-ssids.md](general/add-ssids.md) |
| 4 | **Clear SSIDs** | Borra la lista de SSIDs guardada. | [general/clear-ssids.md](general/clear-ssids.md) |
| 5 | **Clear APs** | Borra la lista de Puntos de Acceso detectados. | [general/clear-aps.md](general/clear-aps.md) |
| 6 | **Clear Stations** | Borra la lista de clientes detectados. | [general/clear-stations.md](general/clear-stations.md) |
| 7 | **Select EP HTML File** | Elige el HTML que usa el Evil Portal. | [general/select-ep-html.md](general/select-ep-html.md) |
| 8 | **Select APs** | Selecciona APs específicos para ataques dirigidos. | [general/select-aps.md](general/select-aps.md) |
| 9 | **View AP Info** | Muestra información detallada de un AP seleccionado. | [general/view-ap-info.md](general/view-ap-info.md) |
| 10 | **Select Stations** | Selecciona clientes específicos para ataques dirigidos. | [general/select-stations.md](general/select-stations.md) |
| 11 | **Join Wifi** | Conecta el Marauder a una red WiFi. | [general/join-wifi.md](general/join-wifi.md) |
| 12 | **Join Saved Wifi** | Conecta a una red guardada previamente. | [general/join-saved-wifi.md](general/join-saved-wifi.md) |
| 13 | **Start AP** | Convierte el Marauder en Punto de Acceso. | [general/start-ap.md](general/start-ap.md) |
| 14 | **Host AP Info** | Muestra info del AP que está levantando el Marauder. | [general/host-ap-info.md](general/host-ap-info.md) |
| 15 | **Set MACs** | Cambia las direcciones MAC del Marauder (spoofing). | [general/set-macs.md](general/set-macs.md) |
| 16 | **Shutdown WiFi** | Apaga el módulo WiFi del Marauder. | [general/shutdown-wifi.md](general/shutdown-wifi.md) |

---