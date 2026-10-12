# 🔄 BLE Replay

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Replay** **reproduce anuncios BLE** capturados previamente con **BLE Sniff**. Es un ataque de **repetición**: el Marauder emite los mismos anuncios que un dispositivo legítimo, haciéndose pasar por él.

Es útil para:

- **Suplantar** un dispositivo BLE.
- **Engañar** a sistemas que confían en anuncios BLE.
- **Probar** la resistencia de sistemas a ataques de replay.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Captura anuncios BLE** con **BLE Sniff**.
2. El pcap se guarda en `/pcap/ble_XXXX.pcap`.
3. Extrae los anuncios que quieras reproducir.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → BLE Replay**.
3. Selecciona el **archivo** con los anuncios a reproducir.
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder reproducirá los anuncios capturados.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Archivo** | Pcap con anuncios | Ninguno |
| **Intervalo** | Tiempo entre anuncios | 100 ms |
| **Loop** | Repetir en bucle | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Replay ===
Archivo: ble_20261011_123456.pcap
Anuncios: 1250
Intervalo: 100 ms
Loop: Sí

Reproduciendo...
Anuncios enviados: 5000
```

### En el aire

Los mismos anuncios que capturaste, emitidos por el Marauder. Los dispositivos cercanos ven el dispositivo suplantado.

---

## 🎯 Para qué sirve

### 1. Suplantación de dispositivos

Hacer que el Marauder se haga pasar por un AirTag, un wearable, etc.

### 2. Pruebas de seguridad

Ver si un sistema detecta anuncios BLE duplicados.

### 3. Investigación

Estudiar cómo los sistemas manejan anuncios BLE repetidos.

### 4. Base para ataques avanzados

El replay puede combinarse con **BLE Disconnect** para simular un dispositivo completo.

---

## ⚠️ Advertencias

- **Legalidad:** suplantar un dispositivo ajeno es **delito**.
- **Detección:** algunos sistemas detectan anuncios duplicados.
- **Alcance:** limitado (~10-30 metros).
- **Dependencia:** necesitas haber capturado anuncios antes con **BLE Sniff**.
- **Ética:** no uses BLE Replay para suplantar dispositivos ajenos.

---

## 🔗 Relacionado

- [BLE Sniff](../sniffers/ble-sniff.md) — captura anuncios BLE
- [BLE Disconnect](ble-disconnect.md) — desconecta dispositivos
- [BT Tracker](../sniffers/bt-tracker.md) — rastrea un dispositivo
