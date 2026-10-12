# 🔵 Bluetooth — Menú completo del Marauder v8

[⬅️ Volver al índice Marauder](../README.md)

---

Guía completa de todas las funciones Bluetooth del ESP32 Marauder v8.

El módulo Bluetooth del Marauder se centra en **Bluetooth Low Energy (BLE)**, el protocolo que usan dispositivos como AirTags, Flippers, wearables, sensores y muchos periféricos modernos. No cubre Bluetooth Clásico (BR/EDR) de forma nativa.

## 📑 Índice

- [🔍 Sniffers](#-sniffers)
- [📡 Scanners](#-scanners)
- [⚔️ Attacks](#️-attacks)
- [⚙️ General](#️-general)

---

## 🔍 Sniffers

Herramientas de captura pasiva.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **BLE Scan** | Escaneo general de dispositivos BLE cercanos. | [sniffers/ble-scan.md](sniffers/ble-scan.md) |
| 2 | **BLE Sniff** | Captura anuncios BLE y los vuelca a pcap. | [sniffers/ble-sniff.md](sniffers/ble-sniff.md) |
| 3 | **AirTag Sniffer** | Detecta Apple AirTags por su firma BLE. | [sniffers/airtag-sniffer.md](sniffers/airtag-sniffer.md) |
| 4 | **Flipper Sniffer** | Detecta Flipper Zero por su firma BLE. | [sniffers/flipper-sniffer.md](sniffers/flipper-sniffer.md) |
| 5 | **BT Info** | Info del adaptador Bluetooth del Marauder. | [sniffers/bt-info.md](sniffers/bt-info.md) |
| 6 | **BT Tracker** | Rastrea un dispositivo BLE por su MAC. | [sniffers/bt-tracker.md](sniffers/bt-tracker.md) |

---

## 📡 Scanners

Herramientas activas de descubrimiento BLE.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **BLE Scan (activo)** | Envía scan requests para más info. | [scanners/ble-scan-activo.md](scanners/ble-scan-activo.md) |
| 2 | **BLE Service Scan** | Enumera servicios GATT de un dispositivo. | [scanners/ble-service-scan.md](scanners/ble-service-scan.md) |
| 3 | **BLE Characteristic Scan** | Lee características de un servicio GATT. | [scanners/ble-characteristic-scan.md](scanners/ble-characteristic-scan.md) |

---

## ⚔️ Attacks

Herramientas ofensivas BLE. **Solo para auditorías autorizadas.**

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **BLE Spam** | Inunda con anuncios BLE falsos. | [attacks/ble-spam.md](attacks/ble-spam.md) |
| 2 | **Sour Apple** | Simula anuncios Apple para saturar iOS. | [attacks/sour-apple.md](attacks/sour-apple.md) |
| 3 | **Swift Pair Spam** | Anuncios Microsoft Swift Pair. | [attacks/swift-pair-spam.md](attacks/swift-pair-spam.md) |
| 4 | **Samsung Spam** | Anuncios falsos de Samsung. | [attacks/samsung-spam.md](attacks/samsung-spam.md) |
| 5 | **Google Spam** | Anuncios falsos de Google Fast Pair. | [attacks/google-spam.md](attacks/google-spam.md) |
| 6 | **Xiaomi Spam** | Anuncios falsos de Xiaomi. | [attacks/xiaomi-spam.md](attacks/xiaomi-spam.md) |
| 7 | **BLE Disconnect** | Fuerza desconexión de dispositivos BLE. | [attacks/ble-disconnect.md](attacks/ble-disconnect.md) |
| 8 | **BLE Replay** | Reproduce anuncios BLE capturados. | [attacks/ble-replay.md](attacks/ble-replay.md) |

---

## ⚙️ General

Configuración y utilidades del módulo Bluetooth.

| # | Función | Descripción | Doc |
|---|---|---|---|
| 1 | **BT Enable** | Activa el módulo Bluetooth. | [general/bt-enable.md](general/bt-enable.md) |
| 2 | **BT Disable** | Desactiva el módulo Bluetooth. | [general/bt-disable.md](general/bt-disable.md) |
| 3 | **Set BT MAC** | Cambia la MAC del adaptador Bluetooth. | [general/set-bt-mac.md](general/set-bt-mac.md) |
| 4 | **Set BT Name** | Cambia el nombre BLE del Marauder. | [general/set-bt-name.md](general/set-bt-name.md) |
| 5 | **Clear BT Devices** | Borra la lista de dispositivos BLE. | [general/clear-bt-devices.md](general/clear-bt-devices.md) |
| 6 | **BT Log** | Exporta los datos BLE capturados a SD. | [general/bt-log.md](general/bt-log.md) |
| 7 | **BT Status** | Muestra el estado del módulo Bluetooth. | [general/bt-status.md](general/bt-status.md) |

---

## ⚠️ Uso legal

Las funciones de **Attacks** (especialmente `BLE Spam`, `Sour Apple`, `Swift Pair Spam`, etc.) pueden:

- **Interferir con dispositivos de terceros** (móviles, auriculares, wearables).
- **Saturar el espectro BLE** de una zona.
- **Ser consideradas interferencia intencionada** según la legislación de telecomunicaciones.

Úsalas **solo** en:

- Tu propio entorno controlado
- Laboratorios aislados
- Pruebas de resistencia autorizadas

En España, el uso indebido puede infringir la **Ley 11/2022 General de Telecomunicaciones** y el **Código Penal** (art. 264 sobre daños informáticos).

---

## 🔗 Relacionado

- [Repositorio oficial del ESP32 Marauder](https://github.com/justcallmekoko/ESP32Marauder)
- [Wiki oficial — Bluetooth](https://github.com/justcallmekoko/ESP32Marauder/wiki/Bluetooth)
- [Especificación Bluetooth SIG](https://www.bluetooth.com/specifications/specs/)