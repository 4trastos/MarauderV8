# 🛰️ GPS Enable

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Enable** **activa el módulo GPS** del Marauder. Es necesario para usar cualquier función GPS.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Config → GPS Enable**.
3. Pulsa **Enable**.
4. El módulo GPS se activa.
5. Verifica con **GPS Info** que funciona.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Enable** | Activar GPS | Sí |
| **Baud rate** | Velocidad UART | 9600 |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Enable ===
Estado: Inactivo

[Enable]

Estado: Activo
Esperando fix...
```

No genera archivos. Solo activa el módulo.

---

## 🎯 Para qué sirve

### 1. Activar GPS

Si el módulo estaba apagado (**GPS Disable**), lo vuelves a encender.

### 2. Preparar para uso

Antes de usar cualquier función GPS, asegúrate de que está activo.

### 3. Diagnóstico

Si el GPS no funciona, **GPS Enable** te dice si el módulo está activo.

---

## ⚠️ Advertencias

- **GPS obligatorio:** necesitas un módulo GPS externo conectado.
- **Baud rate:** asegúrate de que coincide con el del módulo.
- **Al aire libre:** el GPS necesita visibilidad de satélites para el fix.

---

## 🔗 Relacionado

- [GPS Disable](gps-disable.md) — desactiva el GPS
- [GPS Info](../info/gps-info.md) — verifica el estado
- [Set GPS Pins](set-gps-pins.md) — configura los pines