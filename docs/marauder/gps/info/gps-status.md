# 🛰️ GPS Status

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Status** muestra el **estado del fix** del GPS:

- **Sin fix**: el GPS no ha conseguido suficientes satélites.
- **Fix 2D**: posición horizontal (latitud, longitud), sin altitud.
- **Fix 3D**: posición completa (latitud, longitud, altitud).
- **DGPS**: fix con corrección diferencial (más preciso).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Info → GPS Status**.
3. Verás el estado actual.
4. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Actualizar** | Refrescar info | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Status ===
Fix:        3D
Satélites:  8 visibles, 6 usados
HDOP:       1.2
VDOP:       1.5
PDOP:       1.9
Tiempo sin fix: 00:00:00
Último fix: 12:34:56
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Verificar la calidad del fix

| Estado | Significado |
|---|---|
| **Sin fix** | No hay posición. Espera más tiempo. |
| **Fix 2D** | Posición horizontal. Altitud no disponible. |
| **Fix 3D** | Posición completa. Listo para wardriving. |
| **DGPS** | Posición con corrección. Máxima precisión. |

### 2. Diagnóstico

Si no hay fix, **GPS Status** te dice cuánto tiempo lleva sin fix y cuántos satélites ve.

### 3. Base para Wardrive

Antes de lanzar un **Wardrive**, verifica con **GPS Status** que tienes **fix 3D** como mínimo.

---

## ⚠️ Advertencias

- **Al aire libre:** el GPS necesita visibilidad de satélites.
- **Tiempo de fix:** el primer fix puede tardar 30 segundos a varios minutos.
- **DOP:** los valores DOP indican la precisión. Cuanto menores, mejor.

---

## 🔗 Relacionado

- [GPS Info](gps-info.md) — info principal
- [GPS Data](gps-data.md) — datos en bruto
- [Satellite View](satellite-view.md) — vista gráfica
- [Wardrive GPS](../captura/wardrive-gps.md) — wardriving con GPS