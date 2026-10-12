# 🌊 BLE Spam

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BLE Spam** inunda el aire con **anuncios BLE falsos**. Crea cientos de dispositivos BLE ficticios que aparecen en los escaneos de los dispositivos cercanos.

El objetivo es **saturar** el espectro BLE y **confundir** a los dispositivos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → BLE Spam**.
3. Configura el **tipo de anuncio** (genérico, Apple, Samsung, etc.).
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder inundará el aire con anuncios BLE falsos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Tipo** | Tipo de anuncio | Genérico |
| **Intervalo** | Tiempo entre anuncios | 20 ms |
| **Duración** | Tiempo total | Sin límite |

---

## 📊 Qué genera

### En pantalla

```text
=== BLE Spam ===
Tipo: Genérico
Intervalo: 20 ms

Anuncios enviados: 5000
```

### En el aire

Miles de anuncios BLE por segundo. Los dispositivos cercanos ven decenas de dispositivos ficticios.

---

## 🎯 Para qué sirve

### 1. Pruebas de saturación

Ver cómo se comportan los dispositivos BLE cuando hay cientos de anuncios falsos.

### 2. Demostraciones

Mostrar el impacto de un BLE Spam en una presentación.

### 3. Confusión de escáneres

Los escáneres BLE se saturan con tantos dispositivos.

### 4. Base para ataques dirigidos

Los ataques **Sour Apple**, **Swift Pair Spam**, etc. son variantes específicas de BLE Spam.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el espectro BLE es **interferencia**. Delito en España.
- **Detección:** fácil de detectar.
- **Saturación:** puede afectar a **otros dispositivos BLE** cercanos (auriculares, wearables).
- **Alcance:** limitado (~10-30 metros).
- **Batería:** el spam consume mucha energía.
- **Impacto:** algunos dispositivos pueden crashear o volverse lentos.

---

## 🔗 Relacionado

- [Sour Apple](sour-apple.md) — variante específica para iOS
- [Swift Pair Spam](swift-pair-spam.md) — variante para Windows
- [Samsung Spam](samsung-spam.md) — variante para Samsung
- [Google Spam](google-spam.md) — variante para Google Fast Pair
- [Xiaomi Spam](xiaomi-spam.md) — variante para Xiaomi
