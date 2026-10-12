# 😴 Assoc Sleep

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Assoc Sleep** envía **tramas de asociación con el bit de "sleep" activado** a los clientes cercanos. Los clientes, al recibirlas, entran en **modo de ahorro de energía** y dejan de responder a los APs, interrumpiendo su conexión.

Es un ataque **menos agresivo** que Deauth, pero igual de efectivo para interrumpir conexiones.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Assoc Sleep**.
3. Configura el **intervalo** entre tramas.
4. Pulsa **Start**.
5. El Marauder enviará tramas de sleep a todos los clientes cercanos.
6. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Intervalo** | Tiempo entre tramas | 100 ms |
| **Canal** | Canal donde emitir | 1 |
| **Duración** | Tiempo de sleep | 10 segundos |

---

## 📊 Qué genera

### En pantalla

```text
=== Assoc Sleep ===
Intervalo: 100 ms
Canal: 1
Duración: 10s

Tramas enviadas: 5000
Clientes afectados: 3
```

### En el aire

Los clientes afectados entran en modo sleep y dejan de responder al AP. Su conexión se interrumpe temporalmente.

---

## 🎯 Para qué sirve

### 1. Interrupción de conexión

Interrumpir la conexión de todos los clientes de una red sin usar Deauth.

### 2. Pruebas de estrés

Ver cómo se comportan los clientes cuando entran en modo sleep forzado.

### 3. Base para otros ataques

Al interrumpir la conexión, puedes forzar reconexiones y capturar handshakes.

### 4. Demostraciones

Mostrar el impacto de Assoc Sleep en una presentación.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Deauth. **Delito** en redes ajenas.
- **Detección:** los WIDS/WIPS detectan tramas de sleep anómalas.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos clientes ignoran las tramas de sleep. Otros entran en modo sleep y tardan en despertar.
- **Duración:** el sleep puede durar segundos o minutos, según el cliente.

---

## 🔗 Relacionado

- [Assoc Sleep Targ](assoc-sleep-targ.md) — versión dirigida
- [Deauth Flood](deauth-flood.md) — ataque similar pero más agresivo
- [Quiet Time](quiet-time.md) — silenciar el aire
