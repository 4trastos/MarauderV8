# 📡 Beacon Spam Random

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Beacon Spam Random** es como **Beacon Spam List**, pero genera **SSIDs aleatorios** en lugar de usar una lista predefinida. Cada beacon tiene un SSID distinto, generado aleatoriamente.

El resultado es un **caos total** en el espectro: cientos de redes con nombres sin sentido aparecen y desaparecen constantemente.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Beacon Spam Random**.
3. Configura la **longitud** de los SSIDs (por defecto: 8-32 caracteres).
4. Configura el **intervalo** entre beacons (por defecto: 100 ms).
5. Pulsa **Start**.
6. El Marauder emitirá beacons con SSIDs aleatorios.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Longitud SSID** | Caracteres del SSID | 8-32 |
| **Charset** | Caracteres a usar | Alfanuméricos |
| **Intervalo** | Tiempo entre beacons | 100 ms |
| **Canal** | Canal donde emitir | 1 |

---

## 📊 Qué genera

### En pantalla

```text
=== Beacon Spam Random ===
Longitud SSID: 8-32
Intervalo: 100 ms
Canal: 1

Emitiendo:
a8f3k2l9
Zx7QmP4v
9jK2nB5c
...
Beacons enviados: 1250
```

### En el aire

Cientos de redes con nombres aleatorios. Los dispositivos cercanos las listan como disponibles, pero como cambian constantemente, es imposible conectarse.

---

## 🎯 Para qué sirve

### 1. Pruebas de estrés

Ver cómo se comporta un dispositivo cuando hay cientos de redes aleatorias apareciendo y desapareciendo.

### 2. Demostraciones

Mostrar el caos que puede generar un beacon spam aleatorio.

### 3. Confusión de escáneres

Los escáneres de red (como **Beacon Sniff**) se saturan con tantos SSIDs.

### 4. Evitar detección

A diferencia de **Beacon Spam List** (que usa SSIDs reconocibles), los SSIDs aleatorios son más difíciles de filtrar.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Beacon Spam List. **Delito** en redes ajenas.
- **Detección:** más difícil que Beacon Spam List, pero detectable.
- **Saturación:** puede afectar a otras redes cercanas.
- **Alcance:** limitado (~10-30 metros).
- **Almacenamiento en dispositivos:** algunos dispositivos pueden saturarse y volverse lentos.

---

## 🔗 Relacionado

- [Beacon Spam List](beacon-spam-list.md) — versión con lista predefinida
- [Funny SSID Beacon](funny-ssid-beacon.md) — versión con SSIDs graciosos
- [Rick Roll Beacon](rick-roll-beacon.md) — versión con Rick Astley
- [Detect MultiSSID](../sniffers/detect-multissid.md) — detector de este ataque