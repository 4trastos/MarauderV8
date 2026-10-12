# 🛰️ Satellite View

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Satellite View** muestra una **vista gráfica de los satélites** visibles y su **intensidad de señal**. Es una representación visual tipo "radar" o "cielo" donde cada satélite aparece en su posición y con una barra de señal.

Útil para:

- **Diagnosticar** por qué no hay fix.
- **Optimizar** la posición del GPS (saber dónde están los satélites).
- **Ver** la calidad de la señal.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Info → Satellite View**.
3. Verás el gráfico en tiempo real.
4. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Vista** | Radar o barras | Radar |
| **Actualizar** | Frecuencia de refresco | 1 segundo |

---

## 📊 Qué genera

### En pantalla

```text
=== Satellite View ===
Vista: Radar
Satélites: 8 visibles, 6 usados

        N
        ▲
     ◄  ●  ►
        ●
        ▼
        S
```

Cada `●` es un satélite. Los que están en el centro (arriba) son los más altos en el cielo. La intensidad de la señal se muestra con el tamaño o color.

### Vista alternativa (barras)

```text
=== Satellite View ===
Satélites: 8 visibles, 6 usados

PRN 01  ████████░░  45 dB-Hz
PRN 02  ██████░░░░  38 dB-Hz
PRN 03  ██████████  50 dB-Hz
PRN 04  ████░░░░░░  28 dB-Hz
...
```

---

## 🎯 Para qué sirve

### 1. Diagnóstico de fix

Si no hay fix, mira cuántos satélites ves y su señal:

- **0 satélites** → el GPS no ve cielo (dentro de edificio, sótano).
- **1-3 satélites** → no hay fix 3D todavía.
- **4+ satélites** → fix 3D posible.

### 2. Optimizar la posición

Mira la vista radar para saber en qué dirección están los satélites. Si todos están al norte, orienta el GPS hacia el norte.

### 3. Ver la calidad de la señal

Los satélites con señal fuerte (>40 dB-Hz) dan mejor precisión.

### 4. Detectar interferencias

Si ves muchos satélites pero con señal débil, puede haber interferencias.

---

## ⚠️ Advertencias

- **Al aire libre:** el GPS necesita visibilidad de satélites.
- **Actualización:** la vista se actualiza cada 1 segundo.
- **Precisión:** la vista es aproximada. No es un planetario real.

---

## 🔗 Relacionado

- [GPS Info](gps-info.md) — info principal
- [GPS Status](gps-status.md) — estado del fix
- [GPS Data](gps-data.md) — datos en bruto
- [Wardrive GPS](../captura/wardrive-gps.md) — wardriving con GPS
