# 🛰️ GPS Baud Rate

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Baud Rate** configura la **velocidad de comunicación UART** entre el Marauder y el módulo GPS. Los módulos GPS típicos usan:

- **9600 baud** (NEO-6M por defecto).
- **38400 baud** (algunos módulos).
- **115200 baud** (módulos modernos).

Si el baud rate no coincide con el del módulo, no verás datos o verás caracteres corruptos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Info → GPS Baud Rate**.
3. Selecciona el baud rate correcto para tu módulo.
4. Pulsa **Save**.
5. Verifica con **GPS Data** que ves sentencias NMEA legibles.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Baud rate** | 9600, 19200, 38400, 57600, 115200 | 9600 |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Baud Rate ===
Actual: 9600

[9600]  [19200]  [38400]  [57600]  [115200]

Seleccionado: 38400
Guardado.
```

No genera archivos. Solo cambia la configuración.

---

## 🎯 Para qué sirve

### 1. Compatibilidad con el módulo GPS

Cada módulo GPS tiene un baud rate por defecto. Si no coincide, no funciona.

### 2. Diagnóstico de comunicación

Si ves caracteres corruptos en **GPS Data**, prueba con otro baud rate.

### 3. Módulos modernos

Algunos módulos modernos (NEO-M8N, ZED-F9P) usan baud rates más altos para mayor velocidad.

---

## 🎯 Baud rates típicos

| Módulo | Baud rate por defecto |
|---|---|
| **NEO-6M** | 9600 |
| **NEO-7M** | 9600 |
| **NEO-M8N** | 9600 o 38400 |
| **ZED-F9P** | 38400 o 115200 |
| **L80** | 9600 |
| **ATGM336H** | 9600 |

---

## ⚠️ Advertencias

- **Configuración del módulo:** algunos módulos se pueden configurar para usar otro baud rate. Consulta el datasheet.
- **Persistencia:** el cambio se guarda en la configuración del Marauder.
- **Comunicación:** si el baud rate no coincide, no verás datos.

---

## 🔗 Relacionado

- [GPS Data](gps-data.md) — verifica la comunicación
- [GPS Info](gps-info.md) — info principal
- [Set GPS Pins](../config/set-gps-pins.md) — configura los pines
