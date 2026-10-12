# 📡 Select Stations

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Select Stations** permite **seleccionar qué Estaciones (clientes)** de la lista detectada se usarán en ataques dirigidos (Deauth Targeted, Assoc Sleep Targ, Bad Msg Targeted, etc.).

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. **Escanea las redes** con **Scan AP/STA**.
3. Navega hasta **WiFi → General → Select Stations**.
4. Verás la lista de clientes detectados.
5. Marca/desmarca los clientes que quieras seleccionar.
6. Pulsa **Save**.
7. Los clientes seleccionados quedan disponibles para ataques dirigidos.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Selección** | Clientes marcados | Ninguno |
| **Guardar** | Guardar selección | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Select Stations ===
Lista: 12 STAs

[x] 3C:5A:B4:12:34:56 (AP: MiFibra-BB6F, RSSI: -65)
[ ] A4:83:E7:11:22:33 (AP: Movistar_5G, RSSI: -70)
[x] F0:18:98:AA:BB:CC (AP: MiFibra-BB6F, RSSI: -68)
...

Seleccionados: 2/12
```

No genera archivos. Solo selecciona.

---

## 🎯 Para qué sirve

### 1. Ataques dirigidos

Si quieres hacer **Deauth Targeted** o **Assoc Sleep Targ** a un cliente concreto, primero lo seleccionas aquí.

### 2. Filtro de objetivos

Si tienes 12 clientes detectados pero solo te interesan 2, los seleccionas aquí.

### 3. Ataques múltiples

Puedes seleccionar varios clientes y lanzar ataques contra todos ellos.

---

## ⚠️ Advertencias

- **Dependencia:** necesitas haber escaneado clientes antes (con **Scan AP/STA**).
- **MAC randomization:** muchos clientes usan MAC aleatoria. Verás MACs que empiezan por `FA`, `F2`, etc.
- **Guardado:** si no guardas, la selección se pierde al reiniciar.
- **Uso:** esta herramienta no ataca. Solo prepara la lista.
- **Legalidad:** atacar clientes ajenos es **delito**.

---

## 🔗 Relacionado

- [Scan AP/STA](../sniffers/scan-ap-sta.md) — escanea clientes
- [Select APs](select-aps.md) — selecciona APs objetivo
- [Deauth Targeted](../attacks/deauth-targeted.md) — ataque dirigido
- [Assoc Sleep Targ](../attacks/assoc-sleep-targ.md) — ataque dirigido
