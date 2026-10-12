# 📡 Packet Monitor

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Packet Monitor** es la versión **avanzada** de Packet Count. Mientras que Packet Count solo muestra contadores, Packet Monitor muestra:

- **Contadores por tipo de trama** (como Packet Count).
- **Gráfico de barras** con la proporción de cada tipo.
- **Histórico temporal** (línea de evolución).
- **Estadísticas adicionales** (paquetes/segundo, tamaño medio, etc.).

Es la herramienta de **análisis temporal**: te dice no solo **qué** hay, sino **cómo evoluciona** a lo largo del tiempo.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Packet Monitor**.
3. Pulsa **Start**.
4. El Marauder mostrará:
   - Contadores numéricos por tipo (como Packet Count).
   - Gráfico de barras con la proporción.
   - Línea temporal de los últimos N segundos.
   - Paquetes/segundo actuales.
5. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal** | Canal donde escuchar | Actual |
| **Ventana temporal** | Segundos de histórico | 30 |
| **Escala** | Lineal o logarítmica | Lineal |
| **Guardar** | Guardar en SD | No |

---

## 📊 Qué genera

### En pantalla

```text
=== Packet Monitor ===
Canal: 6

Tipo                Contador    Proporción
Beacon              1247        ████████░░░░░░░░  14.7%
Probe Request       342         ██░░░░░░░░░░░░░░  4.0%
Probe Response      189         █░░░░░░░░░░░░░░░  2.2%
Authentication      12          ░░░░░░░░░░░░░░░░  0.1%
Association         8           ░░░░░░░░░░░░░░░░  0.1%
Data                4521        ████████████████  53.3%
QoS Data            2103        ███████░░░░░░░░░  24.8%
EAPOL               6           ░░░░░░░░░░░░░░░░  0.1%
Deauth              0           ░░░░░░░░░░░░░░░░  0.0%
Otros               47          ░░░░░░░░░░░░░░░░  0.6%
------------------------
TOTAL               8475        100.0%
PPS                 234.5

Últimos 30 segundos:
Beacon   ▁▂▃▄▅▆▇█▇▆▅▄▃▂▁▂▃▄▅▆▇█▇▆▅▄▃▂▁
Data     ████████████████████████████████
EAPOL    ▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁
```

### En la SD (opcional)

Un archivo `.csv` con el histórico:

```text
Timestamp,Beacon,ProbeReq,ProbeResp,Auth,Assoc,Data,QoS,EAPOL,Deauth,Total
12:35:00,1200,340,180,10,8,4500,2100,5,0,8343
12:35:01,1247,342,189,12,8,4521,2103,6,0,8475
12:35:02,1250,345,190,12,8,4530,2110,6,0,8451
...
```

---

## 🎯 Para qué sirve

### 1. Análisis temporal del tráfico

**Packet Count** te da un snapshot. **Packet Monitor** te da la **evolución**:

- ¿Cuándo hay más tráfico?
- ¿Cuándo ocurren los EAPOL?
- ¿Hay picos de Deauth?

Útil para:

- Entender patrones de uso de una red.
- Detectar ataques en el tiempo.
- Planificar capturas en el momento óptimo.

### 2. Detección de ataques en el tiempo

Si ves un pico de **Deauth** en la línea temporal, confirma un ataque. Si ves un pico de **EAPOL**, hay reconexiones (puede ser un ataque de deauth o una caída legítima).

### 3. Diagnóstico de rendimiento

El **PPS** (paquetes por segundo) te dice cuánta actividad hay:

- **PPS bajo** (< 100) → red tranquila.
- **PPS medio** (100-1000) → uso normal.
- **PPS alto** (> 1000) → red saturada o ataque.

### 4. Elegir el mejor momento para capturar

Si quieres capturar un handshake, necesitas que haya **EAPOL**. **Packet Monitor** te dice cuándo ocurren:

- Si ves picos de EAPOL cada X minutos → hay reconexiones periódicas.
- Si no ves EAPOL → nadie se conecta, tendrás que forzar un deauth.

### 5. Documentar el espectro

Si necesitas **documentar** cómo evoluciona el espectro WiFi en una ubicación (para una auditoría, un informe, una denuncia), **Packet Monitor** te da los datos en CSV.

---

## 🎯 Diferencias con Packet Count

| Aspecto | Packet Monitor | Packet Count |
|---|---|---|
| **Formato** | Gráfico + histórico + contadores | Solo contadores |
| **Detalle** | Proporción + evolución temporal | Números absolutos |
| **PPS** | Sí | No |
| **Guardar** | CSV con histórico | Snapshot |
| **Uso** | Análisis temporal | Diagnóstico rápido |
| **Complejidad** | Media | Baja |

**En la práctica:** empieza con **Packet Count** para un vistazo rápido. Si necesitas más, pasa a **Packet Monitor**.

---

## ⚠️ Advertencias

- **Canal único:** igual que Packet Count, solo ve el canal actual.
- **Consumo:** el gráfico y el histórico consumen más CPU. La batería dura menos.
- **Ventana temporal:** el histórico es limitado (por defecto, 30 segundos). Para más, configura ventanas más largas.
- **Tipos de trama:** algunos firmwares agrupan tipos. Otros los separan. Comprueba el tuyo.
- **Almacenamiento:** si guardas el CSV, el archivo puede crecer rápido. Un monitor de 1 hora puede generar 1-5 MB.

---

## 🔗 Relacionado

- [Packet Count](packet-count.md) — versión simple, sin histórico
- [Channel Analyzer](channel-analyzer.md) — para ver saturación por canal
- [Channel Summary](channel-summary.md) — para datos numéricos por canal
- [Deauth Sniff](deauth.md) — para confirmar ataques de deauth
- [EAPOL/PMKID Scan](eapol-pmkid.md) — para capturar handshakes