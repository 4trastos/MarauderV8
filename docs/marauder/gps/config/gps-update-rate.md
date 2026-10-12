# 🛰️ GPS Update Rate

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Update Rate** configura la **frecuencia de actualización** del GPS: cuántas veces por segundo el módulo envía su posición.

Los rates típicos son:

- **1 Hz** (1 vez por segundo): por defecto, suficiente para wardriving.
- **5 Hz** (5 veces por segundo): para movimiento rápido (coche, bici).
- **10 Hz** (10 veces por segundo): para aplicaciones de alta precisión.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Config → GPS Update Rate**.
3. Selecciona el rate:
   - **1 Hz**, **5 Hz**, **10 Hz**.
4. Pulsa **Save**.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Update rate** | 1, 5, 10 Hz | 1 Hz |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Update Rate ===
Actual: 1 Hz

[1 Hz]  [5 Hz]  [10 Hz]

Seleccionado: 5 Hz
Guardado.
```

No genera archivos. Solo cambia la configuración.

---

## 🎯 Para qué sirve

### 1. Movimiento rápido

Si te mueves en coche o bici, un rate más alto captura más puntos por segundo.

### 2. Precisión

Para análisis detallados, un rate alto da más datos.

### 3. Ahorro de batería

Un rate bajo consume menos energía.

### 4. Compatibilidad

Algunos módulos GPS no soportan rates altos. Consulta el datasheet.

---

## 🎯 Rates típicos según uso

| Uso | Rate recomendado |
|---|---|
| **Wardriving a pie** | 1 Hz |
| **Wardriving en bici** | 1-5 Hz |
| **Wardriving en coche** | 5 Hz |
| **Senderismo** | 1 Hz |
| **Carreras** | 5-10 Hz |
| **Alta precisión** | 10 Hz |

---

## ⚠️ Advertencias

- **Módulos GPS:** no todos soportan rates altos. Los NEO-6M suelen soportar 1-5 Hz. Los NEO-M8N soportan hasta 10 Hz.
- **Batería:** un rate alto consume más energía.
- **Almacenamiento:** un rate alto genera más datos. El log crece más rápido.
- **Persistencia:** el cambio se guarda en la configuración del Marauder.

---

## 🔗 Relacionado

- [GPS Info](../info/gps-info.md) — verifica el rate
- [Wardrive GPS](../captura/wardrive-gps.md) — usa el rate
- [GPS Track Log](../captura/gps-track-log.md) — usa el rate
