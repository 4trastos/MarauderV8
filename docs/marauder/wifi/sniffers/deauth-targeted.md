# 🎯 Deauth Targeted

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Deauth Targeted** envía una **trama de desautenticación** (deauth) dirigida a **un cliente específico** de un Punto de Acceso. El cliente, al recibirla, cree que el AP lo ha expulsado y se **desconecta automáticamente**. Segundos después, si el cliente tiene la red guardada, **se reconecta** y en ese proceso se genera un **nuevo handshake WPA/WPA2** que puedes capturar.

Es la herramienta estándar para **forzar la captura de un handshake** cuando nadie se conecta o reconecta de forma natural.

> ⚠️ **Solo para tu propia red o redes con autorización explícita por escrito.** Un deauth a redes ajenas es **delito** en España (art. 197 bis y 264 CP) y en la mayoría de jurisdicciones.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea las redes** con **WiFi → Sniffers → Scan AP/STA** para identificar:
   - El AP objetivo (BSSID).
   - Los clientes conectados a ese AP (MACs de las STAs).
   - El canal del AP.

2. **Asegúrate de estar en el mismo canal** que el AP. El Marauder solo puede inyectar en el canal donde está escuchando.

3. **Ten la SD insertada** para guardar el pcap del handshake que captures.

### Desde el menú del Marauder

1. Navega hasta **WiFi → Attacks → Deauth Targeted**.
2. Selecciona el **AP objetivo** de la lista.
3. Selecciona el **cliente objetivo** (STA) al que quieres desautenticar.
4. Configura el **número de tramas** a enviar (por defecto: 10).
5. Pulsa **Start**.
6. El cliente se desconectará y, segundos después, se reconectará.
7. **Inmediatamente** ve a **WiFi → Sniffers → EAPOL/PMKID Scan** y captura el handshake.

### Flujo completo para capturar un handshake

```text
1. Scan AP/STA          → identificar AP y clientes
2. Seleccionar AP       → guardar BSSID
3. Seleccionar STA      → guardar MAC del cliente
4. Deauth Targeted      → forzar desconexión
5. EAPOL/PMKID Scan     → capturar handshake durante la reconexión
6. Guardar pcap         → en /pcap de la SD
7. Procesar con Hashcat → hcxpcapngtool + hashcat
```

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **AP objetivo** | BSSID del AP | Ninguno |
| **Cliente objetivo** | MAC del cliente | Ninguno |
| **Número de tramas** | Cuántas deauth enviar | 10 |
| **Intervalo** | Tiempo entre tramas (ms) | 100 |
| **Canal** | Canal donde inyectar | El del AP |

---

## 📊 Qué genera

**Nada visible en la SD.** El deauth no genera archivos. Lo que genera es una **reacción** en el cliente:

1. El cliente se desconecta del AP.
2. El cliente se reconecta automáticamente (si tiene la red guardada).
3. En la reconexión, se genera un **nuevo handshake WPA**.
4. Ese handshake lo captura el **EAPOL/PMKID Scan**, no el Deauth Targeted.

El resultado final es un archivo `.pcap` en `/pcap/` con el handshake forzado.

### Verificar que el deauth funcionó

En la pantalla del Marauder verás:

```text
Deauth sent: 10/10
Target: FA:8F:CA:61:05:78 → 3C:5A:B4:12:34:56
```

Si el cliente se reconecta, verás en el EAPOL/PMKID Scan:

```text
EAPOL handshake captured!
AP: FA:8F:CA:61:05:78
Client: 3C:5A:B4:12:34:56
```

---

## 🎯 Diferencias con Deauth Flood

| Aspecto | Deauth Targeted | Deauth Flood |
|---|---|---|
| **Objetivo** | Un cliente específico | Todos los clientes |
| **Precisión** | Alta | Baja |
| **Impacto** | Mínimo (solo un cliente) | Alto (toda la red) |
| **Legalidad** | Zona gris si es tu red | Delito claro |
| **Uso típico** | Forzar handshake | Interrumpir red |
| **Detección** | Difícil de detectar | Fácil (muchos clientes caen) |

**En la práctica:** usa siempre **Deauth Targeted** para forzar handshakes. Es menos invasivo, más preciso y más difícil de detectar. **Deauth Flood** solo tiene sentido en escenarios de caos o pruebas de estrés.

---

## ⚠️ Advertencias

- **Legalidad:** un deauth a una red ajena es **delito**. Solo puedes usarlo en tu propia red o con autorización escrita.
- **Detección:** muchas redes modernas (WPA3, 802.11w/PMF) **ignoran las tramas de deauth**. Si el cliente no se reconecta, puede ser por esto.
- **Canal:** si no estás en el canal del AP, el deauth no llega al cliente.
- **Distancia:** si estás demasiado lejos del cliente, la trama no le llega con suficiente potencia.
- **Reconexión:** si el cliente no tiene la red guardada, no se reconectará y no habrá handshake.
- **Interferencia:** en zonas muy saturadas, el deauth puede perderse entre el ruido.
- **Persistencia:** si el cliente no se reconecta tras 2-3 intentos, prueba a esperar unos minutos o cambiar de táctica.

### Casos en los que NO funciona

| Escenario | Por qué |
|---|---|
| Red con **WPA3 (SAE)** | El handshake es diferente, el deauth no fuerza reconexión útil |
| Red con **802.11w (PMF)** | El cliente ignora las tramas de deauth |
| Cliente **sin la red guardada** | No se reconecta automáticamente |
| Cliente **apagado o fuera de rango** | No recibe el deauth |
| AP con **detección de deauth** | Puede alertar al administrador |

---

## 🔗 Relacionado

- [EAPOL/PMKID Scan](../sniffers/eapol-pmkid.md) — para capturar el handshake tras el deauth
- [Scan AP/STA](../sniffers/scan-ap-sta.md) — para identificar AP y clientes antes del deauth
- [Deauth Flood](deauth-flood.md) — variante masiva (más invasiva)
- [Deauth Sniff](../sniffers/deauth.md) — para detectar si alguien está lanzando deauths en tu zona
- [Guía de conversión a Hashcat](../../../04-handshake.md)
- [Guía de uso de Hashcat](../../../05-wordlists.md)
