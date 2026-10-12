# 📡 Funny SSID Beacon

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Funny SSID Beacon** emite beacons falsos con **SSIDs graciosos** predefinidos. Es una variante de **Beacon Spam List** con un propósito más **humorístico** que técnico.

Los SSIDs suelen ser frases cortas, chistes o referencias culturales.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Funny SSID Beacon**.
3. Configura el **intervalo** entre beacons.
4. Pulsa **Start**.
5. El Marauder emitirá beacons con SSIDs graciosos.
6. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Lista SSIDs** | Lista de SSIDs graciosos | Lista por defecto |
| **Intervalo** | Tiempo entre beacons | 100 ms |
| **Canal** | Canal donde emitir | 1 |

---

## 📊 Qué genera

### En pantalla

```text
=== Funny SSID Beacon ===
SSIDs: 20
Intervalo: 100 ms

Emitiendo:
FBI Surveillance Van
Pretty Fly for a WiFi
Tell My WiFi Love Her
...
Beacons enviados: 500
```

### En el aire

Redes con nombres como:

- `FBI Surveillance Van`
- `Pretty Fly for a WiFi`
- `Tell My WiFi Love Her`
- `Drop It Like It's Hotspot`
- `The LAN Before Time`

Los dispositivos cercanos las listan como disponibles, con un toque de humor.

---

## 🎯 Para qué sirve

### 1. Demostraciones

Mostrar el concepto de beacon spam de forma **entretenida**.

### 2. Eventos y conferencias

En charlas de seguridad, es un clásico.

### 3. Pruebas de saturación

Igual que Beacon Spam List, pero con nombres más divertidos.

### 4. Confusión de dispositivos

Algunos dispositivos pueden intentar conectarse a SSIDs que coinciden con redes guardadas.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Beacon Spam List. **Delito** en redes ajenas.
- **Detección:** fácil de detectar.
- **Saturación:** puede afectar a otras redes cercanas.
- **Alcance:** limitado (~10-30 metros).
- **Contenido:** algunos SSIDs pueden ser ofensivos. Úsalos con cabeza.

---

## 🔗 Relacionado

- [Beacon Spam List](beacon-spam-list.md) — versión seria
- [Beacon Spam Random](beacon-spam-random.md) — versión aleatoria
- [Rick Roll Beacon](rick-roll-beacon.md) — versión con Rick Astley
- [Detect MultiSSID](../sniffers/detect-multissid.md) — detector de este ataque
