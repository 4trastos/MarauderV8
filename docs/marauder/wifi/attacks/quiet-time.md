# 🤫 Quiet Time

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Quiet Time** envía **tramas de "silencio"** (Quiet Time) a los dispositivos cercanos. Las tramas Quiet Time son una característica de 802.11 que permite al AP **silenciar temporalmente** a los clientes. Al usarlas maliciosamente, puedes **silenciar** el aire y detener las comunicaciones.

Es un ataque **muy específico** y poco conocido, pero efectivo en entornos controlados.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Quiet Time**.
3. Configura la **duración** del silencio (por defecto: 10 segundos).
4. Configura el **intervalo** entre tramas.
5. Pulsa **Start**.
6. El Marauder enviará tramas Quiet Time.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Duración** | Tiempo de silencio | 10 segundos |
| **Intervalo** | Tiempo entre tramas | 100 ms |
| **Canal** | Canal donde emitir | 1 |

---

## 📊 Qué genera

### En pantalla

```text
=== Quiet Time ===
Duración: 10s
Intervalo: 100 ms
Canal: 1

Tramas enviadas: 5000
Clientes afectados: 5
```

### En el aire

Los clientes afectados entran en modo "silencio" y no transmiten durante el tiempo indicado. La red se queda muda.

---

## 🎯 Para qué sirve

### 1. Interrupción total

Silenciar el aire durante un tiempo. Útil para interrumpir comunicaciones.

### 2. Pruebas de estrés

Ver cómo se comportan los clientes cuando entran en modo silencio.

### 3. Base para otros ataques

Al silenciar el aire, puedes:

- Forzar reconexiones.
- Capturar handshakes.
- Evitar detección.

### 4. Investigación

Estudiar el comportamiento de dispositivos bajo Quiet Time.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Deauth. **Delito** en redes ajenas.
- **Detección:** los WIDS/WIPS detectan Quiet Time anómalos.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos clientes ignoran Quiet Time. Otros entran en modo silencio y tardan en despertar.
- **PMF:** los clientes con **Protected Management Frames** (802.11w) ignoran Quiet Time no autenticados.

---

## 🔗 Relacionado

- [Deauth Flood](deauth-flood.md) — ataque similar pero más agresivo
- [Channel Switch](channel-switch.md) — ataque similar
- [Assoc Sleep](assoc-sleep.md) — ataque similar