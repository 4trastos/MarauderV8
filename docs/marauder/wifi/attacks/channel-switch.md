# 📡 Channel Switch

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Channel Switch** envía **tramas de cambio de canal** (Channel Switch Announcement, CSA) a los clientes cercanos. Los clientes, al recibirlas, **cambian de canal** siguiendo la instrucción, interrumpiendo su conexión con el AP original.

Es un ataque **menos conocido** que Deauth, pero igual de efectivo para interrumpir conexiones.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Channel Switch**.
3. Configura el **canal destino** (por defecto: 1).
4. Configura el **intervalo** entre tramas.
5. Pulsa **Start**.
6. El Marauder enviará CSAs a todos los clientes cercanos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal destino** | Canal al que cambiar | 1 |
| **Intervalo** | Tiempo entre tramas | 100 ms |
| **Canal actual** | Canal donde emitir | 1 |

---

## 📊 Qué genera

### En pantalla

```text
=== Channel Switch ===
Canal destino: 6
Intervalo: 100 ms
Canal actual: 1

Tramas enviadas: 5000
Clientes afectados: 3
```

### En el aire

Los clientes afectados cambian al canal 6, pero el AP original sigue en el canal 1. Resultado: los clientes se desconectan.

---

## 🎯 Para qué sirve

### 1. Interrupción de conexión

Interrumpir la conexión de todos los clientes de una red sin usar Deauth.

### 2. Base para otros ataques

Al interrumpir la conexión, puedes forzar reconexiones y capturar handshakes.

### 3. Pruebas de estrés

Ver cómo se comportan los clientes cuando reciben CSAs falsos.

### 4. Demostraciones

Mostrar el impacto de un Channel Switch en una presentación.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Deauth. **Delito** en redes ajenas.
- **Detección:** los WIDS/WIPS detectan CSAs anómalos.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos clientes ignoran CSAs de APs desconocidos. Otros cambian y se desconectan.
- **PMF:** los clientes con **Protected Management Frames** (802.11w) ignoran CSAs no autenticados.

---

## 🔗 Relacionado

- [Deauth Flood](deauth-flood.md) — ataque similar pero más agresivo
- [Quiet Time](quiet-time.md) — silenciar el aire
- [Assoc Sleep](assoc-sleep.md) — ataque similar
