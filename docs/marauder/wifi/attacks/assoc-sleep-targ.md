# 😴 Assoc Sleep Targ

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Assoc Sleep Targ** es como **Assoc Sleep**, pero envía las tramas de sleep a **un cliente específico** en lugar de a todos. Es menos invasivo y más preciso.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea las redes** con **Scan AP/STA** para identificar el cliente objetivo.
2. Anota su **MAC** y el **canal** donde está.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Assoc Sleep Targ**.
3. Selecciona el **cliente objetivo** (MAC).
4. Configura el **intervalo** entre tramas.
5. Pulsa **Start**.
6. El Marauder enviará tramas de sleep solo al objetivo.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Objetivo** | MAC del cliente | Ninguno |
| **Intervalo** | Tiempo entre tramas | 100 ms |
| **Canal** | Canal donde emitir | El del cliente |
| **Duración** | Tiempo de sleep | 10 segundos |

---

## 📊 Qué genera

### En pantalla

```text
=== Assoc Sleep Targ ===
Objetivo: 3C:5A:B4:12:34:56
Intervalo: 100 ms
Canal: 6
Duración: 10s

Tramas enviadas: 5000
```

### En el aire

El cliente afectado entra en modo sleep y deja de responder al AP. Su conexión se interrumpe temporalmente.

---

## 🎯 Para qué sirve

### 1. Ataque dirigido

Interrumpir la conexión de un cliente concreto sin afectar a los demás.

### 2. Pruebas de estrés

Ver cómo se comporta un cliente específico cuando entra en modo sleep forzado.

### 3. Base para otros ataques

Al interrumpir la conexión, puedes forzar reconexiones y capturar handshakes.

### 4. Investigación

Analizar la respuesta de un cliente específico a tramas de sleep.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Assoc Sleep. **Delito** si es cliente ajeno.
- **Detección:** más difícil que Assoc Sleep (solo afecta a uno).
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos clientes ignoran las tramas de sleep.
- **Ética:** no uses Assoc Sleep Targ contra dispositivos ajenos. Es delito.

---

## 🔗 Relacionado

- [Assoc Sleep](assoc-sleep.md) — versión no dirigida
- [Deauth Targeted](deauth-targeted.md) — ataque dirigido similar
- [Scan AP/STA](../sniffers/scan-ap-sta.md) — para identificar el objetivo
