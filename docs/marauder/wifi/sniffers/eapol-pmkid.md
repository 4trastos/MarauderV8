# 📡 EAPOL/PMKID Scan

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**EAPOL/PMKID Scan** es la herramienta principal del Marauder para capturar **handshakes WPA/WPA2** y **PMKIDs**. Es el primer paso de cualquier auditoría WiFi, porque sin este material no se puede intentar recuperar la contraseña.

- **EAPOL** = *Extensible Authentication Protocol over LAN*. Son los 4 mensajes del *4-Way Handshake* que se intercambian cuando un cliente se conecta a una red WPA/WPA2.
- **PMKID** = *Pairwise Master Key Identifier*. Es un identificador que el AP envía en el primer mensaje de asociación. Permite atacar la contraseña **sin necesidad del handshake completo**.

Ambos se exportan a un archivo `.pcap` que luego se procesa con herramientas como `hcxpcapngtool`, `aircrack-ng` o `hashcat`.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **tarjeta SD insertada** (formateada en FAT32).
2. Navega hasta **WiFi → Sniffers → EAPOL/PMKID Scan**.
3. Elige el **canal** donde está la red objetivo (o usa *Scan AP* primero para localizarla).
4. Pulsa **Start** para comenzar la captura.
5. Espera a que aparezca un handshake o un PMKID:
   - Si aparece un **EAPOL handshake**, verás un mensaje en pantalla.
   - Si aparece un **PMKID**, también se notifica.
6. Pulsa **Stop** cuando tengas lo que necesitas.
7. El archivo `.pcap` se guarda automáticamente en la carpeta `/pcap` de la SD.

### Forzar la captura de un handshake

Si nadie se conecta o reconecta a la red mientras capturas, no se genera handshake. Para forzarlo:

1. Ve a **WiFi → Attacks → Deauth Targeted**.
2. Selecciona el AP objetivo y un cliente conectado.
3. Lanza un **deauth** al cliente.
4. El cliente se reconectará automáticamente, generando el handshake.
5. Vuelve a **EAPOL/PMKID Scan** y captura durante la reconexión.

> ⚠️ **Solo para tu red o redes autorizadas.** Un deauth a redes ajenas es delito.

### Desde la línea de comandos (opcional)

Si prefieres lanzarlo desde terminal (con el Marauder conectado por USB):

```bash
# Capturar 60 segundos en el canal 6
python3 marauder_cli.py --eapol --channel 6 --duration 60 --output mi_captura.pcap
```

> La CLI del Marauder no es oficial; depende del firmware. Consulta la wiki de tu versión.

---

## 📊 Qué genera

Un archivo **`.pcap`** en la carpeta `/pcap` de la SD, con un nombre tipo:

```text
eapol_0.pcap
eapol_1.pcap
...
```

El archivo contiene:

- **Tramas de gestión** (beacons, probes, auth, assoc) de todas las redes visibles
- **Mensajes EAPOL** de los handshakes capturados
- **PMKIDs** de los APs que los han enviado

### Análisis del pcap con `hcxpcapngtool`

Para convertir el pcap a formato Hashcat:

```bash
hcxpcapngtool -o handshake.hc22000 eapol_0.pcap
```

Salida típica:

```text
EAPOL messages (total)...................: 58
EAPOL M1 messages (total)................: 50
EAPOL M2 messages (total)................: 1
EAPOL M3 messages (total)................: 6
EAPOL M4 messages (total)................: 1
EAPOL pairs (best).......................: 1
EAPOL pairs written to 22000 hash file...: 1
PMKID (total)............................: 6
PMKID written to 22000 hash file.........: 3
```

- **`EAPOL M2 messages`**: si es ≥1, tienes handshake.
- **`EAPOL pairs (best)`**: número de handshakes completos y válidos.
- **`PMKID written`**: número de PMKIDs válidos.

### Análisis con `aircrack-ng`

Alternativa más rápida para ver si el pcap sirve:

```bash
aircrack-ng eapol_0.pcap
```

Salida típica:

```text
1 potential targets

      BSSID              ESSID                     Encryption
  FA:8F:CA:61:05:78  MiFibra-BB6F              WPA (1 handshake)
```

Si ves `1 handshake`, el pcap es válido.

---

## 🎯 Diferencias entre EAPOL y PMKID

| Aspecto | EAPOL (Handshake) | PMKID |
|---|---|---|
| **Cuándo se captura** | Cuando un cliente se conecta/reconecta | Cuando un cliente se asocia por primera vez |
| **Mensajes necesarios** | Los 4 (M1-M4) o al menos M1+M2 | Solo el primer mensaje de asociación |
| **Facilidad de captura** | Necesita forzar reconexión (deauth) | Se captura pasivamente |
| **Tiempo de captura** | Segundos (con deauth) o esperar | Instantáneo si hay clientes conectándose |
| **Formato Hashcat** | `WPA*02*` | `WPA*01*` |
| **Compatibilidad** | Universal | Requiere que el AP lo soporte |

**En la práctica:** captura ambos si puedes. El archivo `.hc22000` contiene los dos, y Hashcat los ataca con el mismo modo `-m 22000`.

---

## ⚠️ Advertencias

- **Legalidad:** solo puedes capturar handshakes de **tu propia red** o de redes con **autorización explícita por escrito**.
- **Deauth:** forzar la reconexión con deauth es **ilegal** en redes ajenas (interferencia de telecomunicaciones).
- **Canal:** si capturas en el canal equivocado, no verás los handshakes. Asegúrate de estar en el canal del AP objetivo.
- **Tiempo:** si no hay actividad, no hay handshake. Puedes esperar horas sin resultado.
- **Interferencias:** en zonas muy saturadas, la captura puede fallar. Prueba en distintos canales.
- **Almacenamiento:** los `.pcap` pueden ocupar varios MB. Limpia la SD periódicamente.

---

## 🔗 Relacionado

- [Beacon Sniff](beacon.md) — para descubrir redes y sus canales antes de capturar
- [Deauth Sniff](deauth.md) — para detectar si alguien está lanzando deauths en tu zona
- [Scan AP/STA](scan-ap-sta.md) — para identificar clientes conectados al AP
- [Deauth Targeted](../attacks/deauth-targeted.md) — para forzar la reconexión de un cliente
- [Wardrive](wardrive.md) — para capturar con GPS y subir a WiGLE
- [Guía de conversión a Hashcat](../../../04-handshake.md)
- [Guía de uso de Hashcat](../../../05-wordlists.md)
- [Guía de Aircrack-ng](../../../06-aircrack.md)