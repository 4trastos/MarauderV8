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
  7    ████████░░░░░░░░  -48 dBm
  8    ██░░░░░░░░░░░░░░  -72 dBm
  9    ████░░░░░░░░░░░░  -58 dBm
 10    ██████░░░░░░░░░░  -52 dBm
 11    ████████████░░░░  -42 dBm
 12    ██░░░░░░░░░░░░░░  -70 dBm
 13    █░░░░░░░░░░░░░░░  -78 dBm
```

- **Barras altas** → canal saturado (muchos APs/clientes).
- **Barras bajas** → canal libre.

### En la SD (opcional)

Un archivo `.txt` con los datos numéricos:

```text
Channel  Energy  APs  Clients
1        -45     3    5
2        -65     1    2
3        -70     1    1
4        -75     0    0
5        -40     5    8
6        -35     8    12   ← más saturado
7        -48     4    6
...
```

---

## 🎯 Para qué sirve

### 1. Elegir el mejor canal para tu router

El caso de uso más común. Si tu WiFi va lento:

1. Abre **Channel Analyzer**.
2. Mira qué canal tiene menos actividad.
3. Cambia tu router a ese canal.

**Regla general en 2.4 GHz:** los canales **1, 6 y 11** son los únicos que no se solapan. Si uno está saturado, prueba otro.

### 2. Diagnosticar interferencias

Si tu WiFi se cae intermitentemente pero **Deauth Sniff** no detecta ataques, puede ser:

- **Microondas** (interfiere en 2.4 GHz).
- **Cámaras inalámbricas** (usan 2.4 GHz).
- **Auriculares Bluetooth** (2.4 GHz).
- **Vecinos con routers mal configurados** (canales solapados).

**Channel Analyzer** te muestra picos de energía que coinciden con esas interferencias.

### 3. Decidir el canal para un ataque

Si vas a hacer un **Deauth Flood** o un **EAPOL/PMKID Scan**, quieres estar en el canal del AP objetivo. Si el canal está saturado, el ataque será menos efectivo. **Channel Analyzer** te ayuda a elegir.

### 4. Análisis de espectro para wardriving

Si haces wardriving, **Channel Analyzer** te da una idea de la densidad de redes por canal en cada zona. Útil para:

- Elegir el mejor canal para tu router en casa.
- Entender por qué tu WiFi va mal en ciertos sitios.
- Documentar el espectro de una ubicación.

---

## 🎯 Diferencias con Channel Summary

| Aspecto | Channel Analyzer | Channel Summary |
|---|---|---|
| **Formato** | Gráfico de barras | Tabla numérica |
| **Tiempo real** | Sí, actualización continua | No, snapshot |
| **Uso** | Visual, rápido | Datos, análisis |
| **Guardar** | Opcional | Sí |
| **Detalle** | Solo energía | Energía + APs + clientes |

**En la práctica:** usa **Channel Analyzer** para ver de un vistazo qué canal está libre, y **Channel Summary** si necesitas los datos numéricos para documentar.

---

## ⚠️ Advertencias

- **Canales solapados:** en 2.4 GHz, los canales 1-13 se solapan entre sí. Un AP en el canal 6 afecta a los canales 4-8. Tenlo en cuenta al interpretar el gráfico.
- **5 GHz:** los canales de 5 GHz no se solapan (excepto en configuraciones especiales). El gráfico es más limpio.
- **Actualización:** el Marauder no puede escuchar todos los canales a la vez. Salta de uno a otro, así que el gráfico tiene un pequeño retardo.
- **Energía vs paquetes:** algunos firmwares muestran energía (RSSI acumulado), otros muestran número de paquetes. Son métricas distintas.
- **Falsos positivos:** un canal con mucha energía puede ser por un AP lejano emitiendo fuerte, no necesariamente por saturación.
- **Almacenamiento:** si guardas los datos, el log puede crecer rápido en zonas densas.

---

## 🔗 Relacionado

- [Channel Summary](channel-summary.md) — versión numérica, más detallada
- [Beacon Sniff](beacon.md) — para ver qué APs hay en cada canal
- [Scan AP/STA](scan-ap-sta.md) — para ver qué clientes hay en cada canal
- [EAPOL/PMKID Scan](eapol-pmkid.md) — para capturar en el canal elegido
- [Wardrive](wardrive.md) — para mapear el espectro con GPS