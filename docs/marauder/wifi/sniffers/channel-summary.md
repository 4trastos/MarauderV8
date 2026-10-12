# 📡 Channel Summary

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Channel Summary** muestra un **resumen numérico** de la actividad WiFi por canal. A diferencia de **Channel Analyzer** (que muestra un gráfico), este presenta los datos en **formato tabla**, con más detalle:

- **Energía** (RSSI acumulado).
- **Número de APs** en cada canal.
- **Número de clientes** en cada canal.
- **Canales más saturados**.

Es la herramienta **documental** del Marauder: te da los datos en bruto para que los analices o los guardes.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Channel Summary**.
3. Pulsa **Start**.
4. El Marauder escaneará todos los canales y mostrará una tabla:
   - **Canal**
   - **Energía** (dBm)
   - **APs** (número)
   - **Clientes** (número)
   - **SSIDs** (lista)
5. Pulsa **Stop** cuando termines.
6. Si tienes SD, se guarda en `/logs/channel_XXXX.txt`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Banda** | 2.4 GHz, 5 GHz o ambas | Ambas |
| **Duración por canal** | Tiempo en cada canal | 500 ms |
| **Guardar** | Guardar en SD | Sí |
| **Formato** | Texto, CSV, JSON | Texto |

---

## 📊 Qué genera

### En pantalla

```text
=== Channel Summary ===
Canal  Energía  APs  Clientes  SSIDs
  1    -45      3    5         MiFibra, Movistar_5G, Vodafone-2.4G
  2    -65      1    2         (oculto)
  3    -70      1    1         FreeWiFi
  4    -75      0    0         —
  5    -40      5    8         MiFibra, Movistar_5G, Vodafone-2.4G, ...
  6    -35      8    12        MiFibra, Movistar_5G, Vodafone-2.4G, ...
  7    -48      4    6         MiFibra, Movistar_5G, ...
  8    -72      1    0         (oculto)
  9    -58      2    3         FreeWiFi, Vodafone-2.4G
 10    -52      3    4         MiFibra, Movistar_5G, ...
 11    -42      6    9         MiFibra, Movistar_5G, Vodafone-2.4G, ...
 12    -70      1    1         FreeWiFi
 13    -78      0    0         —
```

### En la SD

Un archivo `.txt` o `.csv`:

```text
Channel,Energy,APs,Clients,SSIDs
1,-45,3,5,"MiFibra,Movistar_5G,Vodafone-2.4G"
2,-65,1,2,"(hidden)"
3,-70,1,1,"FreeWiFi"
4,-75,0,0,""
5,-40,5,8,"MiFibra,Movistar_5G,Vodafone-2.4G,..."
6,-35,8,12,"MiFibra,Movistar_5G,Vodafone-2.4G,..."
...
```

---

## 🎯 Para qué sirve

### 1. Análisis documental del espectro

Si necesitas **documentar** el estado del espectro WiFi en una ubicación:

- **Channel Summary** te da los datos numéricos.
- Puedes exportarlos a CSV.
- Puedes graficarlos en Excel/Google Sheets.
- Puedes comparar distintos momentos del día.

### 2. Elegir el mejor canal (con datos)

**Channel Analyzer** te da una vista rápida. **Channel Summary** te da los datos exactos para decidir con criterio:

- Canal con menos APs.
- Canal con menos clientes.
- Canal con menos energía.

### 3. Detectar canales ocultos

Algunos APs emiten en canales raros (12, 13, 14). **Channel Summary** te los muestra.

### 4. Análisis de densidad de redes

Si haces wardriving, **Channel Summary** te da la densidad de redes por canal en cada ubicación. Útil para:

- Elegir el mejor canal para tu router.
- Entender la saturación de una zona.
- Documentar el espectro para auditorías.

### 5. Comparar antes/después

Si cambias la configuración de tu router, puedes hacer un **Channel Summary** antes y después para ver el impacto:

```text
Antes:  Canal 6 saturado (-35 dBm, 8 APs)
Después: Canal 11 libre (-55 dBm, 2 APs)
```

---

## 🎯 Diferencias con Channel Analyzer

| Aspecto | Channel Summary | Channel Analyzer |
|---|---|---|
| **Formato** | Tabla numérica | Gráfico de barras |
| **Detalle** | Energía + APs + clientes + SSIDs | Solo energía |
| **Tiempo real** | No, snapshot | Sí, actualización continua |
| **Guardar** | Sí, en CSV | Opcional |
| **Uso** | Documentar, analizar | Ver de un vistazo |
| **Exportar** | Fácil (CSV) | Difícil |

**En la práctica:** usa **Channel Analyzer** para ver de un vistazo qué canal está libre, y **Channel Summary** si necesitas los datos numéricos para documentar o analizar.

---

## ⚠️ Advertencias

- **Canales solapados:** en 2.4 GHz, los canales 1-13 se solapan. Un AP en el canal 6 afecta a los canales 4-8. Tenlo en cuenta al interpretar los datos.
- **5 GHz:** los canales de 5 GHz no se solapan (excepto en configuraciones especiales). El resumen es más limpio.
- **Actualización:** el Marauder no puede escuchar todos los canales a la vez. Salta de uno a otro, así que el resumen es un snapshot.
- **Clientes ocultos:** algunos clientes no aparecen porque no emiten probes. El número de clientes es una estimación mínima.
- **SSIDs ocultos:** los APs con SSID oculto aparecen como `(hidden)` o `(oculto)`.
- **Almacenamiento:** si guardas los datos, el log puede crecer rápido en zonas densas.

---

## 🔗 Relacionado

- [Channel Analyzer](channel-analyzer.md) — versión gráfica, más visual
- [Beacon Sniff](beacon.md) — para ver qué APs hay en cada canal
- [Scan AP/STA](scan-ap-sta.md) — para ver qué clientes hay en cada canal
- [EAPOL/PMKID Scan](eapol-pmkid.md) — para capturar en el canal elegido
- [Wardrive](wardrive.md) — para mapear el espectro con GPS