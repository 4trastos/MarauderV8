# 📡 SAE Commit

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**SAE Commit** captura el **intercambio inicial de WPA3** (SAE, *Simultaneous Authentication of Equals*). A diferencia de WPA2 (que usa un handshake de 4 mensajes), WPA3 usa un **intercambio SAE** basado en **criptografía de curva elíptica** (Dragonfly handshake).

**SAE Commit** captura los primeros mensajes de ese intercambio, que pueden usarse para:

- **Análisis forense** del protocolo WPA3.
- **Ataques de diccionario offline** (con herramientas específicas, no Hashcat estándar).
- **Detección** de intentos de conexión WPA3 en tu zona.

> ⚠️ **WPA3 no se puede crackear con Hashcat de la misma forma que WPA2.** El handshake SAE es resistente a ataques de diccionario offline por diseño. Esta herramienta es más para **análisis** que para **cracking**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada**.
2. Navega hasta **WiFi → Sniffers → SAE Commit**.
3. Selecciona el **canal** donde está la red WPA3 objetivo.
4. Pulsa **Start**.
5. El Marauder capturará los mensajes SAE Commit que se intercambien.
6. Verás en pantalla:
   - **BSSID** del AP.
   - **MAC del cliente**.
   - **Tipo de mensaje SAE** (Commit, Confirm).
   - **RSSI**.
7. Pulsa **Stop** cuando tengas lo que buscas.
8. El pcap se guarda en `/pcap/sae_XXXX.pcap`.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Canal** | Canal donde capturar | Actual |
| **Filtro BSSID** | Solo de un AP concreto | Ninguno |
| **Duración** | Tiempo máximo de captura | Sin límite |
| **Guardar** | Guardar pcap en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== SAE Commit ===
Canal: 6

Capturados:
BSSID               Cliente             Tipo      RSSI
FA:8F:CA:61:05:78   3C:5A:B4:12:34:56   Commit    -62
FA:8F:CA:61:05:78   3C:5A:B4:12:34:56   Confirm   -62
FA:8F:CA:61:05:78   A4:83:E7:11:22:33   Commit    -68
```

### En la SD

Un archivo `.pcap` con las tramas SAE:

```text
/pcap/sae_20261011_123456.pcap
```

### Análisis con `tshark`

```bash
# Ver los mensajes SAE
tshark -r sae_20261011_123456.pcap -Y "wlan.fc.type_subtype == 0x0b" -V
```

Los mensajes SAE son **Authentication** con algoritmo SAE (tipo 3).

---

## 🎯 Para qué sirve

### 1. Análisis forense de WPA3

Si estás estudiando WPA3, **SAE Commit** te da los datos en bruto:

- Cómo se inicia el intercambio.
- Qué campos incluye.
- Cómo se comporta el protocolo.

### 2. Detección de actividad WPA3

Si ves muchos SAE Commits en tu zona, hay dispositivos conectándose a redes WPA3. Útil para:

- Inventariar dispositivos WPA3.
- Detectar intentos de conexión.
- Auditar la adopción de WPA3.

### 3. Base para ataques avanzados

Aunque WPA3 **no se puede crackear con Hashcat estándar**, existen **ataques específicos** contra SAE:

- **Downgrade attack**: forzar al cliente a usar WPA2.
- **Side-channel attacks**: explotar debilidades de implementación.
- **Dragonblood**: ataques teóricos contra el handshake SAE.

**SAE Commit** te da los datos para investigar estos ataques.

### 4. Documentación de una red WPA3

Si administras una red WPA3, **SAE Commit** te da:

- Cuántos clientes se conectan.
- Cuándo se conectan.
- Desde dónde (con RSSI).

Útil para auditorías internas.

---

## 🎯 Por qué WPA3 no se puede crackear con Hashcat

| Aspecto | WPA2 | WPA3 |
|---|---|---|
| **Handshake** | 4-way handshake | SAE (Dragonfly) |
| **Base criptográfica** | PSK + HMAC | Curva elíptica (ECC) |
| **Ataque de diccionario offline** | **Sí** (con Hashcat) | **No** por diseño |
| **Forward secrecy** | No | Sí |
| **Resistencia a deauth** | No (vulnerable) | Sí (con PMF) |
| **Herramientas de cracking** | Hashcat, aircrack-ng | Limitadas (Dragonblood, etc.) |

**En resumen:** WPA3 está diseñado para **resistir** exactamente el tipo de ataque que haces con Hashcat contra WPA2. Por eso **SAE Commit** es más una herramienta de **análisis** que de **cracking**.

---

## ⚠️ Advertencias

- **WPA3 ≠ WPA2:** no esperes poder crackear WPA3 con Hashcat. No funciona así.
- **PMF:** WPA3 usa **Protected Management Frames** (802.11w), que impiden ataques de deauth. Si intentas forzar una reconexión con deauth, no funcionará.
- **Compatibilidad:** algunos APs usan **WPA2/WPA3 mixto** (WPA3-Transition). En ese caso, el handshake puede ser WPA2 y sí crackeable.
- **Canales:** el Marauder solo captura el canal actual. Cambia de canal para ver otras redes.
- **Legalidad:** capturar SAE Commits es **pasivo** y legal. Analizarlos es legal. Atacar WPA3 es delito si es red ajena.

---

## 🔗 Relacionado

- [EAPOL/PMKID Scan](eapol-pmkid.md) — para WPA2 (sí crackeable)
- [Beacon Sniff](beacon.md) — para identificar redes WPA3
- [Scan AP/STA](scan-ap-sta.md) — para ver clientes conectados
- [Guía de WPA3](https://www.wi-fi.org/discover-wi-fi/security) — info oficial
- [Dragonblood](https://wpa3.mathyvanhoef.com/) — investigación sobre vulnerabilidades de WPA3