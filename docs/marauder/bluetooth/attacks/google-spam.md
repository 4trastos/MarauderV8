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
