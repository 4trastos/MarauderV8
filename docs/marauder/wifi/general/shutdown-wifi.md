# 📡 Shutdown WiFi

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Shutdown WiFi** apaga el **módulo WiFi** del Marauder. Es una utilidad de **ahorro de energía** y **privacidad**: cuando el WiFi está apagado, el Marauder:

- **No emite** ninguna señal WiFi.
- **No escucha** ninguna señal WiFi.
- **Consume menos batería**.
- **No es detectable** por otros dispositivos WiFi.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Shutdown WiFi**.
3. El Marauder te pedirá **confirmación**.
4. Pulsa **Yes** para apagar el WiFi.
5. El módulo WiFi queda apagado.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Confirmación** | Pedir confirmación | Sí |
| **BT** | Apagar también Bluetooth | No |

---

## 📊 Qué genera

### En pantalla

```text
=== Shutdown WiFi ===
Estado actual: Activo

¿Apagar el módulo WiFi?
[Yes]  [No]

WiFi apagado.
```

No genera archivos. Solo apaga el módulo.

---

## 🎯 Para qué sirve

### 1. Ahorro de batería

El WiFi consume mucha energía. Si no lo estás usando, apágalo para extender la batería.

### 2. Privacidad

Si no quieres que el Marauder emita nada (ni beacons, ni probes), apaga el WiFi.

### 3. Evitar detección

Si alguien está escaneando la zona, no verá al Marauder si el WiFi está apagado.

### 4. Modo "solo Bluetooth"

Si quieres usar solo Bluetooth (BLE Scan, AirTag Sniffer, etc.), puedes apagar el WiFi.

### 5. Preparar para reinicio

Antes de reiniciar el Marauder, puedes apagar el WiFi para asegurarte de que no queda nada activo.

---

## ⚠️ Advertencias

- **Irreversible sin reinicio:** una vez apagado, el WiFi no se vuelve a encender hasta que reinicies el Marauder (o uses un comando específico).
- **Confirmación:** el Marauder pide confirmación.
- **Pérdida de estado:** si tenías capturas o escaneos en curso, se cancelan.
- **Bluetooth:** por defecto, solo apaga el WiFi. Si quieres apagar también el Bluetooth, marca la opción.

---

## 🔗 Relacionado

- [Start AP](start-ap.md) — para encender un AP
- [Join WiFi](join-wifi.md) — para conectarte a una red
- [Generate SSIDs](generate-ssids.md) — antes de apagar, guarda lo que necesites
- [Bluetooth](../../bluetooth/) — si quieres usar solo Bluetooth