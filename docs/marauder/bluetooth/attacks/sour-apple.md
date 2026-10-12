# 🍎 Sour Apple

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Sour Apple** es una variante de **BLE Spam** que emite anuncios **simulando dispositivos Apple** (AirPods, AirTags, Apple TV, etc.). El objetivo es **saturar los dispositivos iOS** cercanos, que intentan conectarse a los dispositivos falsos.

Es un ataque **muy efectivo** contra iPhone y iPad: los dispositivos Apple se vuelven lentos o crashean.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → Sour Apple**.
3. Configura el **tipo de dispositivo** a simular (AirPods, AirTag, Apple TV, etc.).
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder inundará el aire con anuncios Apple falsos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Dispositivo** | Tipo a simular | AirPods |
| **Intervalo** | Tiempo entre anuncios | 20 ms |
| **Duración** | Tiempo total | Sin límite |

---

## 📊 Qué genera

### En pantalla

```text
=== Sour Apple ===
Dispositivo: AirPods
Intervalo: 20 ms

Anuncios enviados: 5000
```

### En el aire

Miles de anuncios Apple falsos. Los dispositivos iOS cercanos intentan conectarse y se saturan.

---

## 🎯 Para qué sirve

### 1. Pruebas de resistencia iOS

Ver cómo se comporta un iPhone cuando hay cientos de AirPods falsos.

### 2. Demostraciones

Mostrar el impacto de Sour Apple en una presentación.

### 3. Investigación

Estudiar cómo iOS maneja anuncios BLE maliciosos.

### 4. Base para ataques dirigidos

Si quieres atacar un iPhone concreto, Sour Apple es una opción.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el espectro BLE es **interferencia**. Delito.
- **Detección:** fácil de detectar.
- **Impacto:** puede **crashear** dispositivos iOS. Puede causar pérdida de datos.
- **Alcance:** limitado (~10-30 metros).
- **Batería:** el spam consume mucha energía.
- **Ética:** no uses Sour Apple contra dispositivos ajenos. Es delito y puede causar daños.

---

## 🔗 Relacionado

- [BLE Spam](ble-spam.md) — variante genérica
- [Swift Pair Spam](swift-pair-spam.md) — variante Windows
- [Samsung Spam](samsung-spam.md) — variante Samsung
- [Google Spam](google-spam.md) — variante Google
- [Xiaomi Spam](xiaomi-spam.md) — variante Xiaomi
