# 📡 Rick Roll Beacon

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Rick Roll Beacon** emite beacons falsos con **SSIDs de canciones de Rick Astley**. Es la versión más **meme** de Beacon Spam.

Los SSIDs suelen ser fragmentos de la letra de `Never Gonna Give You Up` y otras canciones.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Rick Roll Beacon**.
3. Configura el **intervalo** entre beacons.
4. Pulsa **Start**.
5. El Marauder emitirá beacons con SSIDs de Rick Astley.
6. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Lista SSIDs** | Lista de SSIDs de Rick | Lista por defecto |
| **Intervalo** | Tiempo entre beacons | 100 ms |
| **Canal** | Canal donde emitir | 1 |

---

## 📊 Qué genera

### En pantalla

```text
=== Rick Roll Beacon ===
SSIDs: 10
Intervalo: 100 ms

Emitiendo:
Never Gonna Give You Up
Never Gonna Let You Down
Never Gonna Run Around
...
Beacons enviados: 250
```

### En el aire

Redes con nombres como:

- `Never Gonna Give You Up`
- `Never Gonna Let You Down`
- `Never Gonna Run Around`
- `And Desert You`
- `Rick Astley WiFi`

Los dispositivos cercanos las listan como disponibles, y quien las vea se lleva un Rick Roll.

---

## 🎯 Para qué sirve

### 1. Demostraciones

Mostrar el concepto de beacon spam con un toque **meme**.

### 2. Eventos y conferencias

Es un clásico en charlas de seguridad y hackathons.

### 3. Pruebas de saturación

Igual que Beacon Spam List, pero con nombres reconocibles.

### 4. Diversión

Si eres fan de Rick Astley, este es tu ataque.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Beacon Spam List. **Delito** en redes ajenas.
- **Detección:** fácil de detectar.
- **Saturación:** puede afectar a otras redes cercanas.
- **Alcance:** limitado (~10-30 metros).
- **Humor:** no todo el mundo lo pillará. Pero los que sí, lo agradecerán.

---

## 🔗 Relacionado

- [Beacon Spam List](beacon-spam-list.md) — versión seria
- [Beacon Spam Random](beacon-spam-random.md) — versión aleatoria
- [Funny SSID Beacon](funny-ssid-beacon.md) — versión con SSIDs graciosos
- [Detect MultiSSID](../sniffers/detect-multissid.md) — detector de este ataque
