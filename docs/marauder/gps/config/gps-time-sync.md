# 🛰️ GPS Time Sync

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**GPS Time Sync** **sincroniza el reloj del Marauder** con la **hora UTC del GPS**. El GPS es una fuente de tiempo extremadamente precisa (basada en relojes atómicos de los satélites).

Útil para:

- **Timestamp preciso** en capturas.
- **Correlación** de logs con otras fuentes.
- **Análisis forense** con tiempos exactos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con el **módulo GPS conectado** y con **fix**.
2. Navega hasta **GPS → Config → GPS Time Sync**.
3. Pulsa **Sync**.
4. El Marauder sincronizará su reloj con el GPS.
5. Verás la hora actualizada.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Sync** | Sincronizar ahora | Sí |
| **Auto** | Sincronizar cada hora | No |
| **Zona horaria** | Ajuste local | UTC |

---

## 📊 Qué genera

### En pantalla

```text
=== GPS Time Sync ===
Hora antes: 2026-10-11 10:34:56
Hora GPS:   2026-10-11 12:35:01 UTC

[Sync]

Hora después: 2026-10-11 12:35:01 UTC
```

No genera archivos. Solo ajusta el reloj.

---

## 🎯 Para qué sirve

### 1. Timestamp preciso

Si haces capturas con GPS, los timestamps serán exactos.

### 2. Correlación de logs

Si combinas logs de varias fuentes, un reloj sincronizado ayuda a correlacionar.

### 3. Análisis forense

En un análisis forense, los tiempos exactos son cruciales.

### 4. Zona horaria

Si quieres que el Marauder use tu hora local, configura la zona horaria.

---

## ⚠️ Advertencias

- **Fix obligatorio:** sin fix GPS, no hay hora GPS que sincronizar.
- **UTC:** el GPS da hora UTC. Ajusta la zona horaria si quieres hora local.
- **Persistencia:** el reloj se sincroniza hasta que se reinicie el Marauder.

---

## 🔗 Relacionado

- [GPS Info](../info/gps-info.md) — verifica el fix
- [GPS Status](../info/gps-status.md) — estado del fix
- [Wardrive GPS](../captura/wardrive-gps.md) — usa timestamps GPS
