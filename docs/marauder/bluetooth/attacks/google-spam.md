# 🔵 Google Spam

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Google Spam** es una variante de **BLE Spam** que emite anuncios **simulando dispositivos Google Fast Pair** (auriculares, altavoces, etc.). El objetivo es **saturar los dispositivos Android** cercanos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → Google Spam**.
3. Configura el **tipo de dispositivo** a simular.
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder inundará el aire con anuncios Google falsos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Dispositivo** | Tipo a simular | Auriculares |
| **Intervalo** | Tiempo entre anuncios | 20 ms |
| **Duración** | Tiempo total | Sin límite |

---

## 📊 Qué genera

### En pantalla

```text
=== Google Spam ===
Dispositivo: Auriculares
Intervalo: 20 ms

Anuncios enviados: 5000
```

### En el aire

Miles de anuncios Google falsos. Los dispositivos Android cercanos muestran notificaciones de "Nuevo dispositivo encontrado".

---

## 🎯 Para qué sirve

### 1. Pruebas de resistencia Android

Ver cómo se comporta un Android cuando hay cientos de dispositivos Google falsos.

### 2. Demostraciones

Mostrar el impacto de Google Spam en una presentación.

### 3. Investigación

Estudiar cómo Android maneja anuncios BLE maliciosos.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el espectro BLE es **interferencia**. Delito.
- **Detección:** fácil de detectar.
- **Impacto:** puede **saturar** dispositivos Android.
- **Alcance:** limitado (~10-30 metros).
- **Batería:** el spam consume mucha energía.
- **Ética:** no uses Google Spam contra dispositivos ajenos.

---

## 🔗 Relacionado

- [BLE Spam](ble-spam.md) — variante genérica
- [Sour Apple](sour-apple.md) — variante Apple
- [Swift Pair Spam](swift-pair-spam.md) — variante Windows
- [Samsung Spam](samsung-spam.md) — variante Samsung
- [Xiaomi Spam](xiaomi-spam.md) — variante Xiaomi
```

---

## 📄 `docs/marauder/bluetooth/attacks/xiaomi-spam.md`

```markdown
# 🟠 Xiaomi Spam

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Xiaomi Spam** es una variante de **BLE Spam** que emite anuncios **simulando dispositivos Xiaomi** (Mi Band, Redmi Buds, etc.). El objetivo es **saturar los dispositivos Xiaomi** cercanos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → Xiaomi Spam**.
3. Configura el **tipo de dispositivo** a simular.
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder inundará el aire con anuncios Xiaomi falsos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Dispositivo** | Tipo a simular | Mi Band |
| **Intervalo** | Tiempo entre anuncios | 20 ms |
| **Duración** | Tiempo total | Sin límite |

---

## 📊 Qué genera

### En pantalla

```text
=== Xiaomi Spam ===
Dispositivo: Mi Band
Intervalo: 20 ms

Anuncios enviados: 5000
```

### En el aire

Miles de anuncios Xiaomi falsos. Los dispositivos Xiaomi cercanos intentan conectarse y se saturan.

---

## 🎯 Para qué sirve

### 1. Pruebas de resistencia Xiaomi

Ver cómo se comporta un dispositivo Xiaomi cuando hay cientos de dispositivos falsos.

### 2. Demostraciones

Mostrar el impacto de Xiaomi Spam en una presentación.

### 3. Investigación

Estudiar cómo Xiaomi maneja anuncios BLE maliciosos.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el espectro BLE es **interferencia**. Delito.
- **Detección:** fácil de detectar.
- **Impacto:** puede **saturar** dispositivos Xiaomi.
- **Alcance:** limitado (~10-30 metros).
- **Batería:** el spam consume mucha energía.
- **Ética:** no uses Xiaomi Spam contra dispositivos ajenos.

---

## 🔗 Relacionado

- [BLE Spam](ble-spam.md) — variante genérica
- [Sour Apple](sour-apple.md) — variante Apple
- [Swift Pair Spam](swift-pair-spam.md) — variante Windows
- [Samsung Spam](samsung-spam.md) — variante Samsung
- [Google Spam](google-spam.md) — variante Google
```

---

## 📄 `docs/marauder/bluetooth/attacks/ble-disconnect.md`

```markdown
# 🔌 BLE Disconnect

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Disconnect** fuerza la **desconexión** de dispositivos BLE conectados. Envía tramas de desconexión BLE a los dispositivos, forzándolos a romper la conexión con su dispositivo emparejado.

Es útil para:

- **Interrumpir** conexiones BLE.
- **Forzar reconexiones** (y capturar el proceso).
- **Pruebas de estrés** de dispositivos BLE.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea dispositivos BLE** con **BLE Scan**.
2. Identifica la **MAC** del dispositivo a desconectar.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → BLE Disconnect**.
3. Introduce la **MAC** del dispositivo.
4. Pulsa **Start**.
5. El Marauder enviará tramas de desconexión.
6. El dispositivo se desconectará.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **MAC** | MAC del dispositivo | Ninguna |
| **Nº de tramas** | Cuántas enviar | 10 |
| **Intervalo** | Tiempo entre tramas | 100 ms |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Disconnect ===
Objetivo: DE:AD:BE:EF:12:34
Nº tramas: 10
Intervalo: 100 ms

Tramas enviadas: 10
Dispositivo desconectado.
```

No genera archivos. Solo envía tramas.

---

## 🎯 Para qué sirve

### 1. Interrupción de conexión

Interrumpir la conexión BLE de un dispositivo (auriculares, wearable, etc.).

### 2. Forzar reconexión

Al desconectar, el dispositivo intenta reconectarse. Puedes capturar ese proceso con **BLE Sniff**.

### 3. Pruebas de estrés

Ver cómo se comporta un dispositivo cuando se le desconecta repetidamente.

### 4. Base para ataques

Al desconectar, puedes hacerte pasar por el dispositivo emparejado (**BLE Replay**).

---

## ⚠️ Advertencias

- **Legalidad:** desconectar un dispositivo ajeno es **interferencia**. Delito.
- **Detección:** los WIDS/WIPS detectan tramas de desconexión anómalas.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos dispositivos se reconectan automáticamente. Otros requieren intervención manual.
- **Ética:** no uses BLE Disconnect contra dispositivos ajenos.

---

## 🔗 Relacionado

- [BLE Sniff](../sniffers/ble-sniff.md) — captura anuncios BLE
- [BLE Replay](ble-replay.md) — reproduce anuncios capturados
- [BT Tracker](../sniffers/bt-tracker.md) — rastrea un dispositivo
