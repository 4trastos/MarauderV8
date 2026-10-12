# 🛰️ GPS Disable

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Disable** **desactiva el módulo GPS** del Marauder. Útil para:

- **Ahorrar batería** cuando no usas GPS.
- **Evitar interferencias** con otros módulos.
- **Privacidad**: no registrar coordenadas.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **GPS → Config → GPS Disable**.
3. Pulsa **Disable**.
4. El módulo GPS se desactiva.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Disable** | Desactivar GPS | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Disable ===
Estado: Activo

[Disable]

Estado: Inactivo
```

No genera archivos. Solo desactiva el módulo.

---

## 🎯 Para qué sirve

### 1. Ahorro de batería

El GPS consume energía. Si no lo usas, apágalo.

### 2. Evitar interferencias

En algunos casos, el GPS puede interferir con otros módulos. Apagarlo ayuda.

### 3. Privacidad

Si no quieres registrar coordenadas, apaga el GPS.

### 4. Preparar para WiFi

Si vas a hacer un ataque WiFi, apaga el GPS para ahorrar batería.

---

## ⚠️ Advertencias

- **Irreversible sin GPS Enable:** una vez apagado, no se vuelve a encender hasta que uses **GPS Enable**.
- **Estado:** si tenías capturas en curso, se cancelan.

---

## 🔗 Relacionado

- [GPS Enable](gps-enable.md) — activa el GPS
- [GPS Info](../info/gps-info.md) — verifica el estado
- [Shutdown WiFi](../../wifi/general/shutdown-wifi.md) — apaga el WiFi
