# ¿Cómo saber si tu `.pcap` sirve? (El Handshake)

[Volver al índice](../README.md)

---

**sí, necesitas que ese PCAP contenga el tráfico del *Handshake* completo** para poder descifrarlo con un diccionario, y **no necesitas ningún archivo adicional**, solo un buen diccionario (`wordlists`).

Un archivo `.pcap` capturado por un sniffer guarda todo el tráfico de radiofrecuencia que escucha. Si en el momento de la captura ningún dispositivo se conectó o reconoció a la red, el archivo solo tendrá tramas vacías y **no servirá**.

Para que un diccionario funcione, el archivo `.pcap` **debe contener obligatoriamente el intercambio de 4 mensajes (*4-Way Handshake*)** entre un cliente y el router.

Puedes comprobarlo rápidamente en tu Ubuntu con `aircrack-ng` (viene en el paquete `aircrack-ng`):

```bash
sudo apt install aircrack-ng -y
aircrack-ng xxxxxx.pcap

```

* **Si el resultado muestra una lista de redes y dice *"1 handshake"* (o similar):** ¡Perfecto! Tienes el paquete necesario.

```text
1 potential targets

      BSSID              ESSID                     Encryption
  FA:8F:CA:61:05:78  MiFibra-BB6F              WPA (1 handshake)
```

* **Si dice *"0 handshake"*:** Significa que la captura no cogió la conexión y tendrás que volver a capturar. Puedes acelerarlo forzando una desconexión o desautenticación si estás probando con tus propios equipos (ver [Deauth Targeted](marauder/wifi/attacks/deauth-targeted.md)).

```text
1 potential targets

      BSSID              ESSID                     Encryption
  FA:8F:CA:61:05:78  MiFibra-BB6F              WPA (0 handshake)
```


---

## 🎯 Verificación completa con hcxpcapngtool

Para más detalle, usa `hcxpcapngtool`:

```bash
hcxpcapngtool -o handshake.hc22000 xxxxxx.pcap
```

**Salida esperada (éxito):**

```text
EAPOL messages (total)...................: 58
EAPOL M1 messages (total)................: 50
EAPOL M2 messages (total)................: 1
EAPOL M3 messages (total)................: 6
EAPOL M4 messages (total)................: 1
EAPOL pairs (best).......................: 1
EAPOL pairs written to 22000 hash file...: 1
```

- **`EAPOL M2 messages ≥ 1`** → hay al menos un M2 (el mensaje clave).
- **`EAPOL pairs (best) ≥ 1`** → hay al menos un handshake completo y válido.
- **`EAPOL pairs written to 22000`** → se ha escrito al archivo Hashcat.

Si ves **`1`** en los tres campos, el pcap sirve. ✅

---

## 📊 Interpretación del análisis

Cuando analizas un pcap con `hcxpcapngtool`, obtienes un resumen con toda la información relevante. Estos son los campos que **realmente importan**:

### Datos clave

| Campo | Significado |
|---|---|
| **packets inside** | Paquetes totales capturados |
| **ESSID (total unique)** | Nº de redes distintas detectadas |
| **EAPOL messages (total)** | Mensajes EAPOL capturados en total |
| **EAPOL M1 / M2 / M3 / M4** | Mensajes tipo 1/2/3/4 |
| **EAPOL pairs (best)** | **Handshakes completos y válidos** ← el clave |
| **EAPOL M32E2 (authorized)** | Handshake autorizado (la contraseña usada era correcta) |
| **EAPOL pairs written to 22000** | Handshakes exportados a `.hc22000` |
| **PMKID (total)** | PMKIDs capturados |
| **PMKID (best)** | PMKIDs válidos |
| **PMKID written to 22000** | PMKIDs exportados a `.hc22000` |

### Interpretación práctica

| Pregunta | Respuesta |
|---|---|
| ¿El pcap sirve para crackear? | **Sí**, si `EAPOL pairs (best) ≥ 1` o `PMKID written ≥ 1` |
| ¿Sirve para descifrar tráfico en Wireshark? | **Parcialmente**, podrás descifrar datos pero no verás el proceso de conexión completo |
| ¿Cuántos handshakes válidos? | El valor de `EAPOL pairs (best)` |
| ¿Cuántos PMKIDs? | El valor de `PMKID written to 22000` |
| ¿Se puede atacar con Hashcat? | **Sí**, modo `22000` |

### Avisos no bloqueantes

| Aviso | Impacto |
|---|---|
| `very basic format` | El pcap es clásico, no pcapng. No afecta al cracking |
| `radiotap header is missing` | Sin info de frecuencia/calidad. No afecta al cracking |
| `missing frames: proberequest` | No hay probe requests. Dificulta recuperar PSK en algunos casos |
| `missing frames: authentication/association` | No hay proceso de conexión completo. Solo afecta a Wireshark, no a Hashcat |

---

## 🎯 Diferencia entre EAPOL y PMKID

| Aspecto | EAPOL (Handshake) | PMKID |
|---|---|---|
| **Cuándo se captura** | Cuando un cliente se conecta/reconecta | Cuando un cliente se asocia por primera vez |
| **Mensajes necesarios** | Los 4 (M1-M4) o al menos M1+M2 | Solo el primer mensaje de asociación |
| **Facilidad de captura** | Necesita forzar reconexión (deauth) | Se captura pasivamente |
| **Formato Hashcat** | `WPA*02*` | `WPA*01*` |
| **Compatibilidad** | Universal | Requiere que el AP lo soporte |

**En la práctica:** captura ambos si puedes. El archivo `.hc22000` contiene los dos, y Hashcat los ataca con el mismo modo `-m 22000`.

---

## 🎯 Siguiente paso

Si el pcap sirve, puedes:

1. **Convertirlo a formato Hashcat** (si no lo has hecho):
   ```bash
   hcxpcapngtool -o handshake.hc22000 xxxxxx.pcap
   ```
2. **Crackear con Hashcat** (ver [Hashcat para atacar](09-hashcat-para-atacar.md)).
3. **Analizar el tráfico** con Wireshark (ver [Análisis con Wireshark](10-wireshark.md)).

---

## 🔗 Relacionado

- [Captura de paquetes PCAP](03-captura-pcap.md) — flujo completo de captura
- [El Diccionario (Wordlist)](05-wordlists.md)
- [Lanzar el ataque de comprobación con Aircrack-ng](06-aircrack.md)
- [Lanzar el ataque Hashcat](09-hashcat-para-atacar.md)
- [📊 Análisis con Wireshark](10-wireshark.md)
- [EAPOL/PMKID Scan (Marauder)](marauder/wifi/sniffers/eapol-pmkid.md)
- [Deauth Targeted (Marauder)](marauder/wifi/attacks/deauth-targeted.md)