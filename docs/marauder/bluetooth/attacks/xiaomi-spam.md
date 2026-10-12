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