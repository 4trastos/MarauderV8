# 📱 Samsung Spam

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Samsung Spam** es una variante de **BLE Spam** que emite anuncios **simulando dispositivos Samsung** (Galaxy Buds, Galaxy Watch, etc.). El objetivo es **saturar los dispositivos Samsung** cercanos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → Samsung Spam**.
3. Configura el **tipo de dispositivo** a simular (Buds, Watch).
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder inundará el aire con anuncios Samsung falsos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Dispositivo** | Tipo a simular | Galaxy Buds |
| **Intervalo** | Tiempo entre anuncios | 20 ms |
| **Duración** | Tiempo total | Sin límite |

---

## 📊 Qué genera

### En pantalla

```text
=== Samsung Spam ===
Dispositivo: Galaxy Buds
Intervalo: 20 ms

Anuncios enviados: 5000
```

### En el aire

Miles de anuncios Samsung falsos. Los dispositivos Samsung cercanos intentan conectarse y se saturan.

---

## 🎯 Para qué sirve

### 1. Pruebas de resistencia Samsung

Ver cómo se comporta un Galaxy cuando hay cientos de dispositivos Samsung falsos.

### 2. Demostraciones

Mostrar el impacto de Samsung Spam en una presentación.

### 3. Investigación

Estudiar cómo Samsung maneja anuncios BLE maliciosos.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el espectro BLE es **interferencia**. Delito.
- **Detección:** fácil de detectar.
- **Impacto:** puede **saturar** dispositivos Samsung.
- **Alcance:** limitado (~10-30 metros).
- **Batería:** el spam consume mucha energía.
- **Ética:** no uses Samsung Spam contra dispositivos ajenos.

---

## 🔗 Relacionado

- [BLE Spam](ble-spam.md) — variante genérica
- [Sour Apple](sour-apple.md) — variante Apple
- [Swift Pair Spam](swift-pair-spam.md) — variante Windows
- [Google Spam](google-spam.md) — variante Google
- [Xiaomi Spam](xiaomi-spam.md) — variante Xiaomi
