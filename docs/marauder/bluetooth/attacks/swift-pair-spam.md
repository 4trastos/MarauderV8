# 🪟 Swift Pair Spam

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Swift Pair Spam** es una variante de **BLE Spam** que emite anuncios **simulando dispositivos Microsoft Swift Pair** (ratones, teclados, auriculares). El objetivo es **saturar los dispositivos Windows** cercanos, que muestran notificaciones de "Nuevo dispositivo encontrado" sin parar.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Attacks → Swift Pair Spam**.
3. Configura el **tipo de dispositivo** a simular (ratón, teclado, auriculares).
4. Configura el **intervalo** entre anuncios.
5. Pulsa **Start**.
6. El Marauder inundará el aire con anuncios Swift Pair falsos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Dispositivo** | Tipo a simular | Ratón |
| **Intervalo** | Tiempo entre anuncios | 20 ms |
| **Duración** | Tiempo total | Sin límite |

---

## 📊 Qué genera

### En pantalla

```text
=== Swift Pair Spam ===
Dispositivo: Ratón
Intervalo: 20 ms

Anuncios enviados: 5000
```

### En el aire

Miles de anuncios Swift Pair falsos. Los dispositivos Windows cercanos muestran notificaciones sin parar.

---

## 🎯 Para qué sirve

### 1. Pruebas de resistencia Windows

Ver cómo se comporta un Windows cuando hay cientos de dispositivos Swift Pair falsos.

### 2. Demostraciones

Mostrar el impacto de Swift Pair Spam en una presentación.

### 3. Investigación

Estudiar cómo Windows maneja anuncios BLE maliciosos.

### 4. Molestar (con permiso)

Es un ataque **molesto** pero no destructivo.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el espectro BLE es **interferencia**. Delito.
- **Detección:** fácil de detectar.
- **Impacto:** puede **saturar** Windows con notificaciones.
- **Alcance:** limitado (~10-30 metros).
- **Batería:** el spam consume mucha energía.
- **Ética:** no uses Swift Pair Spam contra dispositivos ajenos. Es delito.

---

## 🔗 Relacionado

- [BLE Spam](ble-spam.md) — variante genérica
- [Sour Apple](sour-apple.md) — variante Apple
- [Samsung Spam](samsung-spam.md) — variante Samsung
- [Google Spam](google-spam.md) — variante Google
- [Xiaomi Spam](xiaomi-spam.md) — variante Xiaomi
