# 🛰️ GPS Info

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Info** muestra la **información principal** del módulo GPS:

- **Satélites visibles** y **usados** en el fix.
- **Coordenadas** (latitud, longitud).
- **Altitud**.
- **Velocidad**.
- **Precisión** (HDOP).
- **Hora UTC**.
- **Estado del fix**.

Es la herramienta de **diagnóstico** del GPS: te dice si el módulo está funcionando y si tiene fix.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Info → GPS Info**.
3. Verás la información en tiempo real.
4. Espera a tener fix (puede tardar 30 segundos a varios minutos).
5. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Actualizar** | Refrescar info | Sí |
| **Intervalo** | Frecuencia de refresco | 1 segundo |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Info ===
Fix:         3D
Satélites:   8 visibles, 6 usados
Latitud:     40.4168 N
Longitud:    3.7038 W
Altitud:     650 m
Velocidad:   0.5 km/h
Precisión:   ±3 m (HDOP 1.2)
Hora UTC:    12:35:01
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Verificar que el GPS funciona

Antes de hacer wardriving, comprueba con **GPS Info** que el GPS tiene fix.

### 2. Ver la calidad del fix

El número de satélites y el HDOP te dicen si el fix es bueno:

| Satélites | HDOP | Calidad |
|---|---|---|
| < 4 | > 5 | Mala (sin fix 3D) |
| 4-6 | 2-5 | Aceptable |
| 6-8 | 1-2 | Buena |
| > 8 | < 1 | Excelente |

### 3. Diagnóstico de problemas

Si no hay fix:

- Verifica que el GPS está conectado.
- Verifica que está al aire libre (no dentro de un edificio).
- Espera más tiempo (el fix inicial puede tardar varios minutos).

### 4. Base para Wardrive

Antes de lanzar un **Wardrive**, verifica con **GPS Info** que tienes fix.

---

## ⚠️ Advertencias

- **GPS obligatorio:** sin módulo GPS conectado, esta función no muestra nada.
- **Al aire libre:** el GPS necesita visibilidad de satélites. Dentro de edificios no tendrá fix.
- **Tiempo de fix:** el primer fix (cold start) puede tardar 30 segundos a varios minutos.
- **Precisión:** el HDOP te dice la precisión. Cuanto menor, mejor.

---

## 🔗 Relacionado

- [GPS Data](gps-data.md) — datos en bruto NMEA
- [GPS Status](gps-status.md) — estado del fix
- [Satellite View](satellite-view.md) — vista gráfica de satélites
- [Wardrive GPS](../captura/wardrive-gps.md) — wardriving con GPS
