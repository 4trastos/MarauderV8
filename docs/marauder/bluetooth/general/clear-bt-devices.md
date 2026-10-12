# 🗑️ Clear BT Devices

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Clear BT Devices** borra **toda la lista de dispositivos BLE** detectados por el Marauder. Es una utilidad de **limpieza**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → General → Clear BT Devices**.
3. El Marauder te pedirá **confirmación**.
4. Pulsa **Yes** para borrar la lista.
5. La lista queda vacía.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Confirmación** | Pedir confirmación | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Clear BT Devices ===
Lista actual: 12 dispositivos

¿Borrar todos?
[Yes]  [No]

Lista borrada.
Dispositivos actuales: 0
```

No genera archivos. Solo borra la lista.

---

## 🎯 Para qué sirve

### 1. Limpiar antes de un nuevo escaneo

Si vas a escanear una zona nueva, borra los dispositivos antiguos.

### 2. Liberar memoria

En zonas densas, la lista puede crecer a cientos. Borrarla libera RAM.

### 3. Evitar confusión

Si tienes dispositivos de una zona anterior mezclados con los de la actual, bórralos.

---

## ⚠️ Advertencias

- **Irreversible:** una vez borrada, la lista no se recupera.
- **Confirmación:** el Marauder pide confirmación.
- **Dependencias:** si tenías ataques dirigidos a dispositivos de esa lista, dejarán de funcionar.

---

## 🔗 Relacionado

- [BLE Scan](../sniffers/ble-scan.md) — escanea dispositivos nuevos
- [BT Log](bt-log.md) — exporta los datos antes de borrar
- [BT Status](bt-status.md) — estado del módulo
