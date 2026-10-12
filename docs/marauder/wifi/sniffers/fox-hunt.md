# 📡 Fox Hunt

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Fox Hunt** es una herramienta de **localización física** de señales WiFi. Muestra la **intensidad de señal (RSSI)** de un objetivo en tiempo real, para que te muevas **hacia donde la señal es más fuerte** y localices físicamente el dispositivo.

El nombre viene del **"fox hunting"** radioaficionado: la práctica de localizar un transmisor oculto (el "zorro") usando un receptor direccional.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → Fox Hunt**.
3. Selecciona el **objetivo**:
   - **Por BSSID**: la MAC del AP que quieres localizar.
   - **Por SSID**: el nombre de la red.
   - **Por MAC de cliente**: la MAC de un dispositivo específico.
4. Pulsa **Start**.
5. El Marauder mostrará:
   - **RSSI actual** del objetivo.
   - **RSSI máximo** detectado.
   - **Gráfico de barras** con la intensidad.
   - **Indicador de "caliente/frío"**.
6. **Muévete físicamente** con el Marauder en la mano:
   - Si el RSSI sube → vas en la dirección correcta.
   - Si el RSSI baja → vas en la dirección equivocada.
7. Pulsa **Stop** cuando localices el objetivo.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Objetivo** | BSSID, SSID o MAC de cliente | Ninguno |
| **Canal** | Canal donde escuchar | El del objetivo |
| **Actualización** | Frecuencia de refresco (ms) | 500 |
| **Guardar** | Guardar en SD | No |

---

## 📊 Qué genera

### En pantalla

```text
=== Fox Hunt ===
Objetivo: FA:8F:CA:61:05:78 (MiFibra-BB6F)
Canal: 6

RSSI actual:   -45 dBm
RSSI máximo:   -38 dBm
RSSI mínimo:   -72 dBm

Intensidad:
████████████████████░░░░░░░░░░░░

Estado: 🔥 CALIENTE (estás cerca)

Últimas 20 lecturas:
-45 -43 -42 -40 -38 -39 -41 -44 -46 -48 -50 -52 -55 -58 -60 -62 -65 -68 -70 -72
```

- **Rojo / caliente** → estás cerca.
- **Amarillo / templado** → estás a media distancia.
- **Azul / frío** → estás lejos.

### En la SD (opcional)

Un archivo `.txt` con el histórico:

```text
Timestamp,RSSI,Latitude,Longitude
2026-10-11 12:35:01,-45,40.4168,-3.7038
2026-10-11 12:35:02,-43,40.4169,-3.7039
...
```

---

## 🎯 Para qué sirve

### 1. Localizar un AP específico

Si quieres saber **dónde está físicamente** un router:

- Selecciona su BSSID en **Fox Hunt**.
- Muévete por la zona.
- La señal más fuerte indica dónde está.

Útil para:

- Auditorías de red (saber dónde está cada AP).
- Detectar APs no autorizados.
- Verificar la cobertura de tu propia red.

### 2. Localizar un cliente específico

Si quieres saber **dónde está** un dispositivo (móvil, portátil):

- Selecciona su MAC en **Fox Hunt**.
- Muévete por la zona.
- La señal más fuerte indica dónde está.

Útil para:

- Encontrar un dispositivo perdido.
- Rastrear un dispositivo sospechoso.
- Localizar un Pwnagotchi o Pineapple detectado.

### 3. Detectar ataques de deauth

Si **Deauth Sniff** detecta un ataque, **Fox Hunt** te ayuda a localizar al atacante:

- Selecciona la MAC del atacante (BSSID suplantado).
- Muévete por la zona.
- La señal más fuerte indica dónde está.

### 4. Mapas de cobertura

Si haces wardriving, **Fox Hunt** te ayuda a mapear la cobertura de una red:

- Registra RSSI en cada punto.
- Genera un mapa de calor.

### 5. Búsqueda de Pwnagotchis / Pineapples

Si **Detect Pwnagotchi** o **Detect Pineapple** detecta uno, **Fox Hunt** te ayuda a localizarlo.

---

## 🎯 Técnicas de fox hunting

### 1. Método de "puntos cardinales"

1. Ve a un punto conocido.
2. Registra el RSSI.
3. Muévete 10 metros al norte → registra RSSI.
4. Muévete 10 metros al sur → registra RSSI.
5. Muévete 10 metros al este → registra RSSI.
6. Muévete 10 metros al oeste → registra RSSI.
7. La dirección con RSSI más alto es hacia donde está el objetivo.

### 2. Método de "triangulación"

1. Toma 3 puntos distintos.
2. Registra el RSSI en cada uno.
3. Con la distancia estimada (basada en RSSI), triangula la posición.

### 3. Método de "círculos concéntricos"

1. Camina en círculos alrededor de la zona.
2. Cuando el RSSI sube, estás cerca.
3. Cuando el RSSI baja, te alejas.
4. Repite hasta encontrar el punto exacto.

### 4. Método de "atenuación"

Si la señal es muy fuerte:

- **Apaga el WiFi** del dispositivo objetivo (si es tuyo).
- El RSSI cae a 0.
- Enciéndelo de nuevo.
- El punto donde reaparece es donde está.

---

## ⚠️ Advertencias

- **Reflexiones:** las señales WiFi se reflejan en paredes, muebles, personas. El RSSI más alto no siempre indica la dirección correcta.
- **Interferencias:** en zonas saturadas, el RSSI fluctúa mucho. Toma varias lecturas antes de decidir.
- **Canal:** el Marauder solo puede escuchar un canal a la vez. Si el objetivo cambia de canal, pierdes la señal.
- **Distancia:** el RSSI no es lineal con la distancia. A 1 metro puede ser -30 dBm, a 10 metros -60 dBm, a 100 metros -80 dBm.
- **Legalidad:** rastrear un dispositivo **ajeno** puede ser **invasión de privacidad**. Solo hazlo con dispositivos tuyos o con autorización.
- **Batería:** Fox Hunt consume mucha batería (WiFi + pantalla activa). Un rastreo de 1 hora agota el Marauder.

---

## 🔗 Relacionado

- [Detect Pwnagotchi](detect-pwnagotchi.md) — para detectar Pwnagotchis que luego rastrear
- [Detect Pineapple](detect-pineapple.md) — para detectar Pineapples que luego rastrear
- [Deauth Sniff](deauth.md) — para detectar ataques que luego rastrear
- [MAC Monitor](mac-monitor.md) — para vigilar MACs específicas
- [Scan AP/STA](scan-ap-sta.md) — para identificar objetivos antes de rastrear
