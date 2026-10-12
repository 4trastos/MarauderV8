# 📡 Select APs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Select APs** permite **seleccionar qué Puntos de Acceso** de la lista detectada se usarán en ataques dirigidos (Deauth Targeted, Assoc Sleep Targ, etc.) o en herramientas que requieran un AP objetivo.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. **Escanea las redes** con **Scan AP/STA** o **Beacon Sniff**.
3. Navega hasta **WiFi → General → Select APs**.
4. Verás la lista de APs detectados.
5. Marca/desmarca los APs que quieras seleccionar.
6. Pulsa **Save**.
7. Los APs seleccionados quedan disponibles para ataques dirigidos.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Selección** | APs marcados | Ninguno |
| **Guardar** | Guardar selección | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Select APs ===
Lista: 47 APs

[x] MiFibra-BB6F (FA:8F:CA:61:05:78, CH 6)
[ ] Movistar_5G (00:1A:2B:3C:4D:5E, CH 44)
[x] Vodafone-2.4G (3C:5A:B4:12:34:56, CH 1)
...

Seleccionados: 2/47
```

No genera archivos. Solo selecciona.

---

## 🎯 Para qué sirve

### 1. Ataques dirigidos

Si quieres hacer **Deauth Targeted** o **Assoc Sleep Targ** a un AP concreto, primero lo seleccionas aquí.

### 2. Filtro de objetivos

Si tienes 47 APs detectados pero solo te interesan 2, los seleccionas aquí para no confundirte.

### 3. Ataques múltiples

Puedes seleccionar varios APs y lanzar ataques contra todos ellos.

---

## ⚠️ Advertencias

- **Dependencia:** necesitas haber escaneado APs antes (con **Scan AP/STA** o **Beacon Sniff**).
- **Guardado:** si no guardas, la selección se pierde al reiniciar.
- **Uso:** esta herramienta no ataca. Solo prepara la lista.
- **Legalidad:** atacar APs ajenos es **delito**.

---

## 🔗 Relacionado

- [Scan AP/STA](../sniffers/scan-ap-sta.md) — escanea APs
- [View AP Info](view-ap-info.md) — ver info de un AP
- [Deauth Targeted](../attacks/deauth-targeted.md) — ataque que usa APs seleccionados
- [Deauth Flood](../attacks/deauth-flood.md) — ataque que usa APs seleccionados
