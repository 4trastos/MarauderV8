
# 📶 Wifi Captura de paquetes PCAP

[⬅️ Volver al índice](../README.md)

---

Un **archivo PCAP** (abreviatura de *Packet Capture*) es un formato estándar que contiene la grabación de todo el tráfico de datos transmitido a través de una red inalámbrica o de cable durante un periodo de tiempo. Funciona esencialmente como un "registro" o "vídeo" de lo que ha viajado por el aire: direcciones MAC, tramas de gestión y paquetes de datos.

En el contexto de la seguridad Wi-Fi, los archivos PCAP son fundamentales para analizar protocolos de red y entender el funcionamiento de intercambios de autenticación como el **WPA Handshake**.

---

## Flujo completo de captura

Antes de entrar en detalle, este es el flujo que seguiremos para conseguir un `.pcap` útil:

```text
1. Preparar el Marauder (SD, firmware)
2. Escanear redes       → Beacon Sniff / Scan AP/STA
3. Identificar el AP    → anotar BSSID y canal
4. Identificar clientes → anotar MACs
5. Capturar handshake   → EAPOL/PMKID Scan
6. (Si no hay) forzar   → Deauth Targeted
7. Verificar el pcap    → aircrack-ng
8. Transferir al PC     → copiar a ~/Documents/.../pcap/
```

Cada paso se detalla a continuación.

---

## Paso 1: Preparar el Marauder

### 1.1. Tarjeta SD

- **Formatea la SD en FAT32** si no lo está.
- Crea las carpetas:
  ```text
  /pcap/       → donde se guardan los .pcap
  /logs/       → donde se guardan los logs
  /wordlists/  → diccionarios (opcional)
  ```
- **Inserta la SD** en el Marauder.

### 1.2. Firmware

- Asegúrate de tener el **firmware actualizado** (ver [Instalar o Actualizar el Firmware](01-firmware.md)).
- Verifica con **Device → SD Status** que la SD se detecta bien.

### 1.3. WiFi del Marauder

- Reinicia el Marauder para asegurarte de que el módulo WiFi arranca limpio.
- (Opcional) **WiFi → General → Set MACs** si quieres cambiar la MAC antes de empezar.

---

## Paso 2: Escanear redes

### 2.1. Beacon Sniff (rápido, pasivo)

**Objetivo:** ver qué redes hay en tu zona.

1. Ve a **WiFi → Sniffers → Beacon Sniff**.
2. Pulsa **Start**.
3. Espera 30-60 segundos.
4. Verás la lista de redes con:
   - **SSID** (nombre de la red)
   - **BSSID** (MAC del AP)
   - **Canal**
   - **Cifrado** (Open, WEP, WPA, WPA2, WPA3)
   - **RSSI** (intensidad)
5. Pulsa **Stop**.
6. **Anota** el **BSSID** y el **canal** de tu red objetivo.

> 💡 **Tip:** si tienes muchas redes, filtra por tu SSID. Anota el **BSSID** (MAC), no solo el nombre, porque puede haber varias redes con el mismo SSID.

### 2.2. Scan AP/STA (más detallado)

**Objetivo:** ver qué clientes están conectados a tu AP.

1. Ve a **WiFi → Sniffers → Scan AP/STA**.
2. Pulsa **Start**.
3. Espera 30-60 segundos.
4. Verás:
   - **APs**: tu red con sus clientes.
   - **STAs**: los dispositivos conectados (móviles, portátiles).
5. Pulsa **Stop**.
6. **Anota** las **MACs de los clientes** conectados a tu AP.

> 💡 **Tip:** si no ves clientes, puede que estén en modo pasivo o aleatorizando MAC. Prueba a encender/apagar el WiFi de un móvil tuyo para forzar que aparezca.

---

## Paso 3: Capturar el handshake

### 3.1. EAPOL/PMKID Scan (primer intento)

**Objetivo:** capturar el handshake si alguien se conecta/reconecta.

1. Ve a **WiFi → Sniffers → EAPOL/PMKID Scan**.
2. Selecciona el **canal** de tu AP (anotado en el Paso 2).
3. Pulsa **Start**.
4. Espera. Si alguien se conecta o reconecta, verás en pantalla:
   ```text
   EAPOL handshake captured!
   AP: XX:XX:XX:XX:XX:XX
   Client: YY:YY:YY:YY:YY:YY
   ```
5. Si no pasa nada en 2-3 minutos, pasa al **Paso 4** (forzar reconexión).
6. Pulsa **Stop**.
7. El pcap se guarda en `/pcap/eapol_XXXX.pcap`.

### 3.2. ¿Qué hacer si no captura nada?

- **Verifica el canal**: si tu AP está en el canal 6 y estás escuchando el 1, no ves nada.
- **Verifica la distancia**: si estás muy lejos, no capturas los paquetes.
- **Verifica que hay clientes**: si nadie se conecta, no hay handshake.
- **Pasa al Paso 4**: forzar la reconexión con un deauth.

---

## Paso 4: Forzar reconexión (si no hay handshake)

### 4.1. Deauth Targeted

**Objetivo:** desconectar a un cliente para que se reconecte y genere el handshake.

1. Ve a **WiFi → Attacks → Deauth Targeted**.
2. Selecciona:
   - **AP objetivo**: tu AP (BSSID anotado en el Paso 2).
   - **Cliente objetivo**: un cliente tuyo (MAC anotada en el Paso 2).
3. Configura **10 tramas** de deauth.
4. Pulsa **Start**.
5. El cliente se desconectará.
6. **Inmediatamente** vuelve a **EAPOL/PMKID Scan** y captura durante 30-60 segundos.
7. El cliente se reconectará y generará el handshake.

> ⚠️ **Solo para tu propia red.** Un deauth a redes ajenas es delito (art. 197 bis y 264 CP).

### 4.2. Si el deauth no funciona

| Problema | Causa | Solución |
|---|---|---|
| El cliente no se reconecta | No tiene la red guardada | Usa otro cliente (tu móvil, tu portátil) |
| El deauth no llega | Estás lejos del cliente | Acércate al AP y al cliente |
| La red usa WPA3 | WPA3 no responde a deauth | WPA3 no es crackeable con Hashcat |
| La red usa PMF (802.11w) | Ignora las tramas de deauth | No hay forma de forzar reconexión |

---

## Paso 5: Verificar el pcap

Antes de pasar al análisis, verifica que el `.pcap` **sirve**. Ver [¿Cómo saber si tu `.pcap` sirve?](04-handshake.md) para el detalle completo.

**Resumen rápido:**

```bash
aircrack-ng eapol_0.pcap
```

- **Si dice `1 handshake`** → el pcap sirve ✅
- **Si dice `0 handshake`** → vuelve al Paso 3 o 4 ❌

---

## Paso 6: Transferir al PC

### 6.1. Extraer la SD

- Desmonta la SD de forma segura.
- Insértala en el PC.

### 6.2. Copiar el pcap

```bash
cp /media/tu_usuario/SD/pcap/eapol_0.pcap ~/Documents/oath/path/pcap/
```

### 6.3. Verificar

```bash
ls -lh ~/Documents/path/path/pcap/eapol_0.pcap
```

---

## ✅ Checklist rápido

```text
[ ] SD formateada en FAT32 con /pcap/ y /logs/
[ ] Firmware actualizado
[ ] Beacon Sniff → anotar BSSID y canal
[ ] Scan AP/STA → anotar MACs de clientes
[ ] EAPOL/PMKID Scan → capturar handshake
[ ] (Si no hay) Deauth Targeted → forzar reconexión
[ ] Verificar con aircrack-ng → "1 handshake"
[ ] Copiar pcap al PC
```

---

## 🎯 Errores comunes

| Error | Causa | Solución |
|---|---|---|
| `0 handshake` en aircrack-ng | No se capturó el handshake | Volver al Paso 3 o 4 |
| `Packets contained no EAPOL data` | El pcap no tiene EAPOL | Volver al Paso 3 |
| `No such file or directory` | El pcap no está en la ruta | Verificar la SD y la ruta |
| El pcap está vacío | El Marauder no capturó nada | Verificar el canal y la SD |
| El deauth no funciona | Red WPA3 o PMF | No hay solución, WPA3 no es crackeable |

---

## ¿Qué es un WPA Handshake (4-Way Handshake)?

Cuando un dispositivo (como un teléfono o portátil) se conecta a un router Wi-Fi protegido con WPA2 o WPA3, ambos intercambian **4 mensajes clave** antes de permitir la navegación. Este proceso de 4 pasos se conoce como *4-Way Handshake*.

- **Su función:** Permite que el router y el cliente demuestren que conocen la contraseña correcta y deriven las claves de cifrado temporales para la sesión, **sin enviar la contraseña real por el aire**.
- **Contenido de la captura:** El archivo PCAP registrado por un sniffer (como la Marauder) guarda esos 4 mensajes. Dentro de ellos viajan números aleatorios (*nonces*) y un código de autenticación (*MIC*).

---

## Captura de paquetes (Handshakes / PCAP)

- Ve a **WiFi** > **Sniffers** > **EAPOL/PMKID Scan** (o **PKE / Handshake**).
- Al pulsar **Start**, el archivo `.pcap` se escribirá directamente en la carpeta `/pcap` de la tarjeta SD.

| | | | |
|:---:|:---:|:---:|:---:|
| <img src="../img/marauder_01.jpg" width="200"> | <img src="../img/marauder_02.jpg" width="200"> | <img src="../img/marauder_03.jpg" width="200"> | <img src="../img/marauder_04.jpg" width="200"> |
| Selección de menú | Modo sniffer | EAPOL/PMKID Scan | Capturando paquetes |

---

## Análisis defensivo y auditoría con Wireshark en Ubuntu

Para inspeccionar y analizar capturas PCAP en un entorno de laboratorio o auditoría de red propia, se utiliza **Wireshark**.

### 1. Instalación de Wireshark en Ubuntu

Abre la terminal e instala la herramienta:

```bash
sudo apt update
sudo apt install wireshark -y
```

*(Opcional: Durante la instalación, si pregunta si los usuarios no superusuarios deben poder capturar paquetes, selecciona "Sí" y añade tu usuario al grupo `wireshark` con `sudo usermod -aG wireshark $USER`).*

### 2. Inspeccionar la captura PCAP con Wireshark

1. Copia el archivo `.pcap` generado por la tarjeta SD a tu equipo Ubuntu.
2. Abre el archivo en Wireshark:

```bash
wireshark /ruta/a/tu/archivo.pcap
```

3. **Filtros útiles en Wireshark:**
   - Para ver únicamente los paquetes del intercambio de autenticación (*Handshake*):
     ```text
     eapol
     ```
   - Si deseas ver únicamente las tramas de gestión de una red o cliente específico por su dirección MAC:
     ```text
     wlan.addr == XX:XX:XX:XX:XX:XX
     ```

Si el filtro `eapol` muestra los 4 mensajes (o al menos los pares necesarios 1-2 o 2-3), significa que la captura del Handshake se ha realizado correctamente y está completa para su análisis.

---

## 🔗 Relacionado

- [¿Cómo saber si tu `.pcap` sirve? (El Handshake)](04-handshake.md)
- [El Diccionario (Wordlist)](05-wordlists.md)
- [Lanzar el ataque de comprobación con Aircrack-ng](06-aircrack.md)
- [Lanzar el ataque Hashcat](09-hashcat-para-atacar.md)
- [📊 Análisis con Wireshark](10-wireshark.md)
- [EAPOL/PMKID Scan (Marauder)](marauder/wifi/sniffers/eapol-pmkid.md)
- [Deauth Targeted (Marauder)](marauder/wifi/attacks/deauth-targeted.md)
- [Beacon Sniff (Marauder)](marauder/wifi/sniffers/beacon.md)
- [Scan AP/STA (Marauder)](marauder/wifi/sniffers/scan-ap-sta.md)