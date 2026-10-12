# Análisis con Wireshark

[⬅️ Volver al índice](../README.md)

---

## ¿Qué es Wireshark?

**Wireshark** es el analizador de protocolos de red más usado del mundo. Permite:

- **Capturar** tráfico en vivo.
- **Abrir** archivos `.pcap` y `.pcapng`.
- **Filtrar** paquetes por cualquier campo.
- **Descifrar** tráfico WPA/WPA2 si tienes la clave.
- **Analizar** protocolos en detalle.

En este documento nos centramos en el **análisis de capturas WiFi** con Wireshark.

---

## ¿Por qué usar Wireshark?

Aunque no hayas crackeado la contraseña, Wireshark te sirve para:

1. **Analizar el handshake** en detalle (los 4 mensajes EAPOL).
2. **Ver beacons** de todas las redes capturadas.
3. **Identificar fabricantes** por OUI.
4. **Analizar probe requests** de dispositivos cercanos.
5. **Descifrar tráfico** si consigues la clave.
6. **Documentar** una captura para una auditoría.

---

## Instalación de Wireshark en Ubuntu

Abre la terminal e instala la herramienta:

```bash
sudo apt update
sudo apt install wireshark -y
```

*(Opcional: Durante la instalación, si pregunta si los usuarios no superusuarios deben poder capturar paquetes, selecciona "Sí" y añade tu usuario al grupo `wireshark`:*

```bash
sudo usermod -aG wireshark $USER
```

*Cierra sesión y vuelve a entrar para que el cambio tenga efecto.)*

---

## Abrir una captura

1. Copia el archivo `.pcap` generado por la tarjeta SD a tu equipo Ubuntu.
2. Abre el archivo en Wireshark:

```bash
wireshark /ruta/a/tu/archivo.pcap
```

O desde la interfaz gráfica:
- **File → Open** → selecciona el `.pcap`.

---

## 🔍 Filtros útiles en Wireshark

### Filtros básicos

| Filtro | Qué muestra |
|---|---|
| **`eapol`** | Los 4 mensajes del handshake WPA |
| **`wlan.fc.type_subtype == 0x08`** | Beacons (APs emitiéndose) |
| **`wlan.fc.type_subtype == 0x04`** | Probe requests (clientes buscando redes) |
| **`wlan.fc.type_subtype == 0x05`** | Probe responses (APs respondiendo) |
| **`wlan.fc.type_subtype == 0x0b`** | Authentication |
| **`wlan.fc.type_subtype == 0x0c`** | Deauthentication |
| **`wlan.addr == XX:XX:XX:XX:XX:XX`** | Tráfico de una MAC específica |
| **`wlan.ssid == "MiFibra-BB6F"`** | Tráfico de una red específica |
| **`ip`** | Tráfico IP (solo visible si está descifrado) |
| **`arp`** | Tráfico ARP (solo visible si está descifrado) |
| **`dns`** | Tráfico DNS (solo visible si está descifrado) |
| **`http`** | Tráfico HTTP (solo visible si está descifrado) |

### Filtros avanzados

```text
# Handshake de una red específica
eapol && wlan.addr == FA:8F:CA:61:05:78

# Handshake de un cliente específico
eapol && wlan.addr == 3C:5A:B4:12:34:56

# Beacons en el canal 6
wlan.fc.type_subtype == 0x08 && wlan_radio.channel == 6

# Redes WPA3 (SAE)
wlan.rsn.akm_suites == 0x000008

# Redes WPA2 (PSK)
wlan.rsn.akm_suites == 0x000002
```

---

## ¿Qué buscar en Wireshark (sin la contraseña)?

Incluso sin saber la clave, el `.pcap` es una **mina de oro** para aprender. Abre tu `eapol_0.pcap` y prueba estos filtros:

### 1. `eapol` — El handshake

Este es el **filtro clave**. Aislará solo los 4 mensajes del handshake. Si los ves, el proceso de autenticación está capturado.

En los detalles del paquete (panel inferior), expande **802.1X Authentication** para ver campos como:

- **Replay Counter**: debe seguir la secuencia `1, 1, 2, 2`.
- **Key Nonce**: el número aleatorio (ANonce del AP, SNonce del cliente).
- **Key MIC**: el código de integridad (clave para el cracking).
- **Key Data**: los datos cifrados (GTK, etc.).

### 2. `wlan.fc.type_subtype == 0x08` — Beacons

Este filtro muestra solo las **Beacons** (balizas) del router. Ahí puedes ver:

- **SSID**
- **Canal**
- **Auth Key Management (AKM) Suite**:
  - Si ves `SAE (SHA256)` → tu red usa **WPA3**.
  - Si ves `PSK` → tu red usa **WPA2**.

> ⚠️ **WPA3 no se puede descifrar con la contraseña** usando este método porque usa un intercambio de claves diferente. Si ves `SAE`, el plan de descifrado no funciona.

### 3. `ip` o `arp` o `dhcp` — Antes de descifrar

Aplica este filtro **antes** de poner la contraseña. Verás que **no aparece nada**. Esto te demuestra que el tráfico IP está **cifrado** y es ilegible sin la clave.

---

## ¿Cómo usar la contraseña en Wireshark?

Si Hashcat (o Aircrack-ng) encuentra la contraseña, este es el proceso para ver el tráfico descifrado:

### Método 1: `wpa-pwd` (más simple)

1. Ve a **Editar → Preferencias → Protocols → IEEE 802.11**.
2. Marca la casilla **"Enable decryption"** (Habilitar descifrado).
3. Haz clic en el botón **"Edit..."** junto a "Decryption Keys".
4. Pulsa el `+` para añadir una nueva clave.
5. En **Key type**, selecciona **`wpa-pwd`**.
6. En **Key**, escribe la contraseña y el SSID con este formato exacto:
   ```text
   tu_contraseña:MiFibra-BB6F
   ```
   (Sin espacios, con dos puntos en medio.)
7. Acepta todo y observa cómo, mágicamente, los paquetes que antes eran ilegibles ahora muestran direcciones IP, tráfico DNS, etc.

### Método 2: `wpa-psk` (si `wpa-pwd` falla)

Si el SSID tiene caracteres raros o `wpa-pwd` no funciona, usa el **PSK derivado** (64 caracteres hex).

**Generar el PSK:**

```bash
wpa_passphrase "MiSSID" "MiContraseña"
```

**Salida:**

```text
network={
	ssid="MiSSID"
	#psk="MiContraseña"
	psk=8b4c1a2f9e7d3c5b6a8f0e1d2c3b4a5f6e7d8c9b0a1f2e3d4c5b6a7f8e9d0c1b
}
```

**Añadir a Wireshark:**

1. **Editar → Preferencias → Protocols → IEEE 802.11 → Decryption keys → Edit**.
2. Añade nueva entrada:
   - **Key type**: `wpa-psk`
   - **Key**: pega los 64 caracteres hex.
3. **OK** en todo.

### Verificar que funciona

En la lista de paquetes, busca filtros como:

```text
dns || http || arp
```

Si ves protocolos como `DNS`, `TCP`, `HTTP`, `TLS`, `ARP`, `ICMP`, el descifrado ha funcionado. ✅

Si sigues viendo solo `802.11` con "Data" cifrada, el descifrado no ha funcionado. ❌

---

## 🔍 Análisis forense con `tshark`

`tshark` es la versión **CLI** de Wireshark. Perfecta para scripts y análisis automatizado.

### Comandos útiles

```bash
# Ver todos los paquetes EAPOL
tshark -r eapol_0.pcap -Y eapol

# Ver beacons con SSID, canal y cifrado
tshark -r eapol_0.pcap -Y "wlan.fc.type_subtype == 0x08" \
  -T fields -e wlan.bssid -e wlan.ssid -e wlan_radio.channel

# Contar tramas por tipo
tshark -r eapol_0.pcap -q -z io,phs

# Ver el detalle de un handshake
tshark -r eapol_0.pcap -Y eapol -V

# Seguir un flujo TCP (si está descifrado)
tshark -r eapol_0.pcap -q -z follow,tcp,ascii,0
```

### Ejemplo: extraer todos los SSIDs del pcap

```bash
tshark -r eapol_0.pcap -Y "wlan.fc.type_subtype == 0x08" \
  -T fields -e wlan.ssid | sort -u
```

### Ejemplo: ver handshakes de una red específica

```bash
tshark -r eapol_0.pcap -Y "eapol && wlan.addr == FA:8F:CA:61:05:78" -V
```

---

## Casos de uso

### 1. Analizar el handshake

- **Filtro**: `eapol`
- **Objetivo**: verificar que los 4 mensajes están presentes.
- **Qué buscar**: `Replay Counter` con secuencia `1, 1, 2, 2`.

### 2. Identificar redes WPA3

- **Filtro**: `wlan.rsn.akm_suites == 0x000008`
- **Objetivo**: detectar redes WPA3 (SAE).
- **Qué buscar**: `SAE (SHA256)` en los beacons.

### 3. Analizar tráfico descifrado

- **Filtro**: `dns || http || arp`
- **Objetivo**: ver qué hacen los dispositivos.
- **Qué buscar**: dominios consultados, páginas visitadas, IPs.

### 4. Documentar una captura

- **Filtro**: `eapol || wlan.fc.type_subtype == 0x08`
- **Objetivo**: crear un informe con las redes y handshakes.
- **Qué buscar**: SSIDs, BSSIDs, canales, cifrado.

### 5. Detectar deauths

- **Filtro**: `wlan.fc.type_subtype == 0x0c`
- **Objetivo**: ver si alguien está lanzando deauths.
- **Qué buscar**: tramas de deauth con `Reason Code 7`.

---

## ⚠️ Advertencias

- **Legalidad:** analizar tráfico de una red ajena sin autorización es **delito**.
- **WPA3:** Wireshark **no puede descifrar WPA3** con la contraseña. El handshake SAE es diferente.
- **PMF (802.11w):** las redes con PMF cifran los management frames. Algunos filtros no funcionarán.
- **Rendimiento:** pcap muy grandes (>100 MB) pueden ralentizar Wireshark. Usa `tshark` para análisis grandes.
- **Privacidad:** el tráfico descifrado puede contener información personal. No lo compartas.

---

## 🔗 Relacionado

- [¿Cómo saber si tu `.pcap` sirve?](04-handshake.md)
- [El Diccionario (Wordlist)](05-wordlists.md)
- [Lanzar el ataque de comprobación con Aircrack-ng](06-aircrack.md)
- [Lanzar el ataque Hashcat](09-hashcat-para-atacar.md)
- [Documentación oficial de Wireshark](https://www.wireshark.org/docs/)
- [Wiki de Wireshark — Filtros](https://wiki.wireshark.org/DisplayFilters)
- [Wiki de Wireshark — 802.11](https://wiki.wireshark.org/HowToDecrypt802.11)