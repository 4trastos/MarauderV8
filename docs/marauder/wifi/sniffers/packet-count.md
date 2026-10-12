# 📡 Packet Count

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Packet Count** es un contador **rápido y en tiempo real** de los paquetes 802.11 que el Marauder recibe, clasificados por **tipo de trama**. Es la herramienta de **diagnóstico más básica**: te dice si el aire está "vivo" y qué tipo de tráfico predomina.

No analiza contenido, no guarda pcaps, no interpreta nada. Solo **cuenta**. Útil para:

- Verificar que el módulo WiFi funciona.
- Comprobar si hay actividad en un canal.
- Diagnosticar capturas vacías.
- Decidir si merece la pena hacer un sniff más profundo.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Packet Count**.
3. Pulsa **Start**.
4. El Marauder empezará a contar paquetes por tipo:
   - **Beacon**
   - **Probe Request**
   - **Probe Response**
   - **Authentication**
   - **Association**
   - **Data**
   - **QoS Data**
   - **EAPOL**
   - **Deauth**
   - **Otros**
5. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal** | Canal donde escuchar | Actual |
| **Reset** | Reiniciar contadores | No |
| **Auto-reset** | Reset cada N segundos | No |

---

## 📊 Qué genera

### En pantalla

```text
=== Packet Count ===
Canal: 6

Tipo                Contador
Beacon              1247
Probe Request       342
Probe Response      189
Authentication      12
Association         8
Data                4521
QoS Data            2103
EAPOL               6
Deauth              0
Otros               47
------------------------
TOTAL               8475

Última actualización: 12:35:01
```

Los contadores se actualizan **varias veces por segundo**.

### En la SD (opcional)

No genera archivos por defecto. Si el firmware lo permite, se puede guardar un snapshot en `/logs/packet_count_XXXX.txt`.

---

## 🎯 Para qué sirve

### 1. Verificar que el WiFi funciona

Si acabas de encender el Marauder y no ves nada en **Beacon Sniff**, abre **Packet Count**:

- Si los contadores suben → el WiFi funciona, no hay redes cerca o estás en mal canal.
- Si todos están a 0 → problema de hardware o firmware.

### 2. Diagnosticar capturas vacías

Si lanzas un **EAPOL/PMKID Scan** y no capturas nada:

- Abre **Packet Count** en el mismo canal.
- Si no ves EAPOL, no hay actividad de handshake (nadie se conecta).
- Si ves EAPOL pero tu scan no los captura, problema de configuración.

### 3. Ver el "estado" de un canal

Cada tipo de trama indica algo:

| Trama | Qué indica |
|---|---|
| **Beacon** alto | Hay muchos APs cerca |
| **Probe Request** alto | Hay muchos clientes buscando redes |
| **Data** alto | Hay mucha actividad (streaming, descargas) |
| **EAPOL** alto | Hay conexiones/reconexiones ocurriendo |
| **Deauth** alto | Hay ataques en la zona (o APs reiniciando) |

### 4. Decidir el mejor canal

Si estás dudando entre dos canales para un sniff, abre **Packet Count** en cada uno:

- **Menos Data/Beacon** → canal más limpio.
- **Más EAPOL** → canal con más actividad de handshake (bueno para capturar).

### 5. Detección rápida de ataques

Si ves **Deauth** subiendo sin parar, alguien está atacando. Confírmalo con **Deauth Sniff**.

---

## 🎯 Diferencias con Packet Monitor

| Aspecto | Packet Count | Packet Monitor |
|---|---|---|
| **Formato** | Contadores numéricos | Gráfico + contadores |
| **Detalle** | Por tipo de trama | Por tipo + histórico |
| **Visualización** | Tabla | Barras + línea temporal |
| **Uso** | Diagnóstico rápido | Análisis temporal |
| **Guardar** | Opcional | Opcional |

**En la práctica:** **Packet Count** es para un vistazo rápido; **Packet Monitor** es para ver la evolución en el tiempo.

---

## ⚠️ Advertencias

- **Canal único:** el Marauder solo cuenta los paquetes del canal donde está. Cambia de canal para ver otros.
- **Contadores acumulativos:** los contadores no se reinician solos. Usa `Reset` para empezar de cero.
- **Tipos de trama:** algunos firmwares agrupan tipos (`Data` y `QoS Data` juntos). Otros los separan.
- **Sensibilidad:** en zonas muy saturadas, los contadores suben muy rápido. No te asustes si ves miles en segundos.
- **No distingue redes:** el contador es global, no por BSSID. Para eso, usa **Scan AP/STA**.

---

## 🔗 Relacionado

- [Packet Monitor](packet-monitor.md) — versión gráfica con histórico
- [Beacon Sniff](beacon.md) — para ver qué APs generan los beacons
- [EAPOL/PMKID Scan](eapol-pmkid.md) — para capturar handshakes
- [Channel Analyzer](channel-analyzer.md) — para ver saturación por canal
- [Deauth Sniff](deauth.md) — para confirmar ataques de deauth