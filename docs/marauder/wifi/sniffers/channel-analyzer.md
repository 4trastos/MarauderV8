# 📡 Channel Analyzer

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Channel Analyzer** muestra un **gráfico en tiempo real de la energía WiFi** en cada canal. Es una representación visual de cuánta actividad hay en cada frecuencia, tanto de APs como de clientes.

Es la herramienta **diagnóstica** del Marauder: te dice **qué canales están saturados** y **cuáles están libres**. Útil para:

- Elegir el mejor canal para tu router.
- Diagnosticar problemas de WiFi lento.
- Detectar interferencias.
- Decidir en qué canal hacer un ataque (el menos saturado).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Channel Analyzer**.
3. Pulsa **Start**.
4. El Marauder empezará a escanear todos los canales y mostrará un gráfico de barras:
   - **Eje X**: canales (1-13 en 2.4 GHz, 36-165 en 5 GHz).
   - **Eje Y**: energía (RSSI acumulado o número de paquetes).
   - **Barras**: altura proporcional a la actividad.
5. Pulsa **Stop** cuando termines.
6. Si tienes SD, puedes guardar una captura del gráfico o los datos en bruto.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Banda** | 2.4 GHz, 5 GHz o ambas | Ambas |
| **Escala** | Lineal o logarítmica | Lineal |
| **Promedio** | Media móvil de N muestras | 10 |
| **Guardar** | Guardar datos en SD | No |

---

## 📊 Qué genera

### En pantalla

Un gráfico de barras tipo:

```text
Canal  Energía
  1    ████████░░░░░░░░  -45 dBm
  2    ███░░░░░░░░░░░░░  -65 dBm
  3    ██░░░░░░░░░░░░░░  -70 dBm
  4    █░░░░░░░░░░░░░░░  -75 dBm
  5    ██████████░░░░░░  -40 dBm
  6    ████████████████  -35 dBm  ← más saturado
  7