# 🌊 Deauth Flood

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Deauth Flood** envía **tramas de desautenticación** (deauth) de forma **masiva** a **todos los clientes** de un AP (o de todos los APs visibles). A diferencia de **Deauth Targeted** (que va a un cliente concreto), este ataque inunda el aire para **tumbar toda la red**.

El resultado: **todos los clientes se desconectan** simultáneamente y, si tienen la red guardada, intentan reconectarse. En ese proceso, se generan **múltiples handshakes** que puedes capturar.

Es un ataque **muy invasivo** y **fácil de detectar**. Solo tiene sentido en:

- Tu propia red (pruebas de estrés).
- Auditorías autorizadas por escrito.
- Laboratorios aislados.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea las redes** con **WiFi → Sniffers → Scan AP/STA** para identificar:
   - El AP objetivo (BSSID).
   - El canal del AP.
   - Los clientes conectados (si quieres dirigirlo).

2. **Estate en el mismo canal** que el AP objetivo.

3. **Ten la SD insertada** para guardar el pcap con los handshakes.

### Desde el menú del Marauder

1. Navega hasta **WiFi → Attacks → Deauth Flood**.
2. Selecciona el **AP objetivo** (o elige "todos").
3. Configura el **número de tramas** por cliente (por defecto: 50).
4. Configura el **intervalo** entre tramas (por defecto: 10 ms).
5. Pulsa **Start**.
6. El Marauder enviará deauths masivos durante el tiempo configurado.
7. **Inmediatamente** ve a **WiFi → Sniffers → EAPOL/PMKID Scan** y captura los handshakes.

### Flujo completo

```text
1. Scan AP/STA          → identificar AP y clientes
2. Seleccionar AP       → guardar BSSID
3. Deauth Flood         → tumbar toda la red
4. EAPOL/PMKID Scan     → capturar múltiples handshakes
5. Guardar pcap         → en /pcap de la SD
6. Procesar con Hashcat → hcxpcapngtool + hashcat
```

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **AP objetivo** | BSSID del AP (o "todos") | Todos |
| **Número de tramas** | Cuántas deauth por cliente | 50 |
| **Intervalo** | Tiempo entre tramas (ms) | 10 |
| **Duración** | Tiempo total del flood | 10 segundos |
| **Canal** | Canal donde inyectar | El del AP |

---

## 📊 Qué genera

**Nada visible en la SD** (el deauth no genera archivos). Lo que genera es una **reacción masiva**:

1. Todos los clientes del AP se desconectan.
2. Todos intentan reconectarse automáticamente.
3. Se generan **múltiples handshakes** simultáneos.
4. El **EAPOL/PMKID Scan** los captura todos.

El resultado final es un `.pcap` en `/pcap/` con **varios handshakes** de la misma red.

### Verificar que el flood funcionó

En la pantalla del Marauder:

```text
Deauth flood started
Target: FA:8F:CA:61:05:78 (all clients)
Sent: 500/500 frames
```

Si los clientes se reconectan, verás en el EAPOL/PMKID Scan:

```text
EAPOL handshake captured! (multiple)
AP: FA:8F:CA:61:05:78
Clients: 3C:5A:B4:12:34:56, A4:83:E7:11:22:33, F0:18:98:AA:BB:CC
```

---

## 🎯 Diferencias con Deauth Targeted

| Aspecto | Deauth Flood | Deauth Targeted |
|---|---|---|
| **Objetivo** | Todos los clientes | Un cliente específico |
| **Precisión** | Baja | Alta |
| **Impacto** | Alto (toda la red cae) | Mínimo (solo un cliente) |
| **Detección** | Fácil (muchos clientes caen) | Difícil |
| **Handshakes** | Múltiples a la vez | Uno a la vez |
| **Legalidad** | Delito claro | Zona gris |
| **Uso típico** | Pruebas de estrés | Forzar handshake puntual |

**En la práctica:**

- **Para forzar un handshake:** usa **Deauth Targeted**. Más limpio, más preciso, menos detectable.
- **Para capturar muchos handshakes de golpe:** usa **Deauth Flood** (solo en tu red).
- **Para tumbar una red:** usa **Deauth Flood** (solo con autorización).

---

## ⚠️ Advertencias

- **Legalidad:** un deauth flood a una red ajena es **delito grave**. En España, art. 197 bis y 264 del Código Penal. Multas de hasta 300.000€ y penas de prisión.
- **Detección:** los APs modernos con **WIDS/WIPS** detectan floods de deauth y alertan al administrador. En entornos empresariales, te detectarán en segundos.
- **PMF (802.11w):** las redes con **Protected Management Frames** ignoran las tramas de deauth. El ataque no funciona.
- **WPA3 (SAE):** aunque el deauth funcione, el handshake WPA3 no se puede crackear con diccionarios de la misma forma que WPA2.
- **Saturación:** enviar miles de deauths puede saturar el espectro y afectar a **otras redes cercanas**.
- **Batería:** un flood consume mucha energía. El Marauder puede calentarse y agotar la batería rápido.
- **Persistencia:** si el AP tiene **protección contra deauth** (PMF, WIPS), el ataque falla tras 1-2 intentos.

### Casos en los que NO funciona

| Escenario | Por qué |
|---|---|
| Red con **802.11w (PMF)** | Clientes ignoran deauth |
| Red con **WPA3 (SAE)** | Handshake diferente, no crackeable con diccionario |
| AP con **WIDS/WIPS** | Detecta y bloquea el ataque |
| Clientes **sin la red guardada** | No se reconectan |
| Clientes **en modo pasivo** | No emiten probes, no se reconectan solos |

---

## 🔗 Relacionado

- [Deauth Targeted](deauth-targeted.md) — versión dirigida, más limpia
- [EAPOL/PMKID Scan](../sniffers/eapol-pmkid.md) — para capturar handshakes tras el flood
- [Scan AP/STA](../sniffers/scan-ap-sta.md) — para identificar AP y clientes antes del flood
- [Deauth Sniff](../sniffers/deauth.md) — para detectar floods en tu zona
- [Guía de conversión a Hashcat](../../../04-handshake.md)
- [Guía de uso de Hashcat](../../../05-wordlists.md)