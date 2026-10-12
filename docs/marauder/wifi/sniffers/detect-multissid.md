# 📡 Detect MultiSSID

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Detect MultiSSID** detecta cuando un **mismo dispositivo** está emitiendo **múltiples SSIDs diferentes**. Es una técnica usada por:

- **Routers mal configurados** que emiten varias redes (2.4 GHz + 5 GHz + invitados).
- **APs empresariales** con múltiples VLANs.
- **Atacantes** que usan **AP Clone Spam** o **Beacon Spam** para simular muchas redes desde una sola MAC.
- **Dispositivos comprometidos** que se hacen pasar por varias redes.

Es la herramienta **defensiva** contra uno de los ataques más comunes: el **beacon spam**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Detect MultiSSID**.
3. Pulsa **Start**.
4. El Marauder escaneará todos los canales y agrupará los beacons por **BSSID** (MAC del AP).
5. Si un BSSID emite **más de N SSIDs**, lo marca como sospechoso.
6. Verás en pantalla:
   - **BSSID**
   - **Número de SSIDs**
   - **Lista de SSIDs**
   - **Canal**
7. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Umbral** | Nº de SSIDs para alertar | 3 |
| **Canales** | Qué canales escanear | Todos |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== MultiSSID Detectados ===

BSSID               SSIDs  Canal  SSIDs
FA:8F:CA:61:05:78   5      6      MiFibra-BB6F, MiFibra-BB6F_5G, MiFibra-Guest, FreeWiFi, HackMe
3C:5A:B4:12:34:56   3      1      Vodafone-2.4G, Vodafone-Guest, Vodafone-IoT
00:1A:2B:3C:4D:5E   2      44     Movistar_5G, Movistar_Plus
```

- **5 SSIDs desde una MAC** → muy sospechoso (posible ataque).
- **3 SSIDs desde una MAC** → normal en routers con red de invitados.
- **2 SSIDs desde una MAC** → normal (2.4 GHz + 5 GHz).

### En la SD

Un archivo `.txt`:

```text
BSSID,SSIDs,Channel,SSID_List
FA:8F:CA:61:05:78,5,6,"MiFibra-BB6F,MiFibra-BB6F_5G,MiFibra-Guest,FreeWiFi,HackMe"
3C:5A:B4:12:34:56,3,1,"Vodafone-2.4G,Vodafone-Guest,Vodafone-IoT"
...
```

---

## 🎯 Para qué sirve

### 1. Detectar ataques de Beacon Spam

El ataque **Beacon Spam** emite cientos de beacons falsos con SSIDs distintos desde **una sola MAC**. **Detect MultiSSID** lo detecta:

- Si ves un BSSID con **20 SSIDs**, es un ataque.
- Si ves un BSSID con **5 SSIDs raros** (`FreeWiFi`, `HackMe`), es un ataque.

### 2. Detectar APs mal configurados

Algunos routers emiten múltiples SSIDs legítimamente:

- **2.4 GHz + 5 GHz** → 2 SSIDs.
- **Red principal + invitados + IoT** → 3-4 SSIDs.

**Detect MultiSSID** te ayuda a distinguir lo normal de lo sospechoso.

### 3. Inventario de APs

Si administras una red, **Detect MultiSSID** te dice cuántos SSIDs emite cada AP. Útil para:

- Detectar configuraciones no autorizadas.
- Documentar la red.
- Auditar la seguridad.

### 4. Detección de dispositivos comprometidos

Si un dispositivo de tu red empieza a emitir SSIDs raros, puede estar comprometido. **Detect MultiSSID** te avisa.

### 5. Base para análisis forense

Si detectas un ataque, **Detect MultiSSID** te da:

- La **MAC del atacante** (BSSID).
- Los **SSIDs falsos** que emite.
- El **canal** donde opera.

Con esa info, puedes:

- Localizarlo con **Fox Hunt**.
- Documentar el incidente.
- Denunciar.

---

## 🎯 Cómo distinguir un ataque de una configuración legítima

| Señal | Ataque | Legítimo |
|---|---|---|
| **Nº de SSIDs** | 5+ desde una MAC | 2-4 desde una MAC |
| **Nombres** | Raros (`FreeWiFi`, `HackMe`) | Coherentes (`MiFibra`, `MiFibra_5G`) |
| **Patrón** | Cambian constantemente | Estables |
| **Cifrado** | Open (sin cifrado) | WPA2/WPA3 |
| **RSSI** | Muy fuerte (estás cerca) | Variable |
| **Canal** | Salta entre canales | Fijo |

---

## ⚠️ Advertencias

- **Falsos positivos:** los routers modernos emiten muchos SSIDs legítimamente. Configura el umbral según tu entorno.
- **MAC spoofing:** un atacante puede cambiar su MAC para no ser detectado. En ese caso, verás la MAC spoofed, no la real.
- **Canales:** el Marauder escanea secuencialmente, así que puede perder algunos beacons si salta de canal muy rápido.
- **Detección:** si el atacante sabe que estás usando Detect MultiSSID, puede reducir el número de SSIDs para pasar desapercibido.
- **Legalidad:** escuchar beacons es **pasivo** y legal. Detectar ataques es defensivo y legal.

---

## 🔗 Relacionado

- [Beacon Sniff](beacon.md) — para ver todos los beacons
- [Beacon Spam List](../attacks/beacon-spam-list.md) — ataque que este detector identifica
- [Beacon Spam Random](../attacks/beacon-spam-random.md) — variante con SSIDs aleatorios
- [Fox Hunt](fox-hunt.md) — para localizar al atacante
- [Scan AP/STA](scan-ap-sta.md) — para análisis completo de APs