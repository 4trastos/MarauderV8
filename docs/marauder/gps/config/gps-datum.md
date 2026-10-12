# 🛰️ GPS Datum

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Datum** configura el **datum geodésico** que el GPS usa para calcular las coordenadas. Un datum es un **modelo matemático de la Tierra** que define cómo se traducen las señales de los satélites a coordenadas en la superficie.

El datum más común es **WGS84** (World Geodetic System 1984), que es el estándar global y el que usa el GPS por defecto.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado**.
2. Navega hasta **GPS → Config → GPS Datum**.
3. Selecciona el datum:
   - **WGS84** (estándar global, recomendado).
   - **NAD83** (Norteamérica).
   - **ETRS89** (Europa).
   - **Otros** según región.
4. Pulsa **Save**.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Datum** | Modelo geodésico | WGS84 |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Datum ===
Actual: WGS84

[WGS84]  [NAD83]  [ETRS89]  [Otros]

Seleccionado: WGS84
Guardado.
```

No genera archivos. Solo cambia la configuración.

---

## 🎯 Para qué sirve

### 1. Compatibilidad con mapas

Si usas mapas que usan un datum distinto a WGS84, ajusta el datum para que las coordenadas coincidan.

### 2. Precisión regional

En algunas regiones, un datum local da mayor precisión que WGS84.

### 3. Compatibilidad con herramientas

Algunas herramientas (SIG, GPS profesionales) requieren un datum específico.

---

## 🎯 Datums comunes

| Datum | Región | Uso |
|---|---|---|
| **WGS84** | Global | Estándar GPS, Google Maps, OpenStreetMap |
| **NAD83** | Norteamérica | EE.UU., Canadá |
| **ETRS89** | Europa | Unión Europea |
| **ED50** | Europa | Antiguo, todavía en uso |
| **SAD69** | Sudamérica | Brasil, Argentina |

---

## ⚠️ Advertencias

- **WGS84 es el estándar:** si no estás seguro, usa WGS84.
- **Cambio de datum:** cambiar el datum cambia las coordenadas. Asegúrate de que las herramientas que uses esperan el mismo datum.
- **Persistencia:** el cambio se guarda en la configuración del Marauder.

---

## 🔗 Relacionado

- [GPS Info](../info/gps-info.md) — verifica las coordenadas
- [Wardrive GPS](../captura/wardrive-gps.md) — usa el datum
- [Export GPX](../export/export-gpx.md) — exporta con el datum correcto
