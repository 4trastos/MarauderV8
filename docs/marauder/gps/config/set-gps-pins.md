# 🛰️ Set GPS Pins

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Set GPS Pins** configura los **pines GPIO** que el Marauder usa para comunicarse con el módulo GPS por UART. Por defecto, el Marauder usa:

- **GPIO 16** como RX (recibe datos del GPS).
- **GPIO 17** como TX (envía datos al GPS).

Si tu módulo GPS está conectado a otros pines, o si tu firmware usa otros, puedes cambiarlos aquí.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **GPS → Config → Set GPS Pins**.
3. Configura:
   - **RX Pin**: pin por donde el Marauder recibe (debe ir al TX del GPS).
   - **TX Pin**: pin por donde el Marauder envía (debe ir al RX del GPS).
4. Pulsa **Save**.
5. Reinicia el Marauder si es necesario.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **RX Pin** | Pin RX del Marauder | GPIO 16 |
| **TX Pin** | Pin TX del Marauder | GPIO 17 |
| **Baud rate** | Velocidad UART | 9600 |

---

## 📊 Qué genera

### En pantalla

```text
=== Set GPS Pins ===
RX Pin: 16
TX Pin: 17

Nuevo RX: 26
Nuevo TX: 27

[Save]
```

No genera archivos. Solo cambia la configuración.

---

## 🎯 Para qué sirve

### 1. Compatibilidad con otros módulos

Si tienes varios módulos conectados, puedes asignar pines distintos al GPS.

### 2. Firmware personalizado

Si usas un firmware que usa otros pines, configúralos aquí.

### 3. Reparación

Si los pines por defecto están dañados o en uso, puedes cambiarlos.

---

## 🎯 Conexión típica

| Marauder | GPS (NEO-6M) |
|---|---|
| GPIO 16 (RX2) | TX del GPS |
| GPIO 17 (TX2) | RX del GPS |
| 3.3V | VCC |
| GND | GND |

> ⚠️ **Verifica el voltaje.** Algunos módulos GPS funcionan a 5V y otros a 3.3V.

---

## ⚠️ Advertencias

- **Configuración incorrecta:** si configuras mal los pines, el GPS no funcionará.
- **Persistencia:** el cambio se guarda en la configuración del Marauder.
- **Reinicio:** algunos firmwares requieren reiniciar tras cambiar los pines.
- **Voltaje:** verifica que el módulo GPS y el Marauder usan el mismo voltaje.

---

## 🔗 Relacionado

- [GPS Enable](gps-enable.md) — activa el GPS
- [GPS Baud Rate](../info/gps-baud-rate.md) — configura la velocidad
- [GPS Info](../info/gps-info.md) — verifica que funciona
