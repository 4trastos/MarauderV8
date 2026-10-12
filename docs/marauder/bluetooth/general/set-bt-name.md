# 📡 Set BT Name

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Set BT Name** cambia el **nombre BLE** del Marauder. Es el nombre que aparece cuando otros dispositivos escanean BLE y ven al Marauder.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → General → Set BT Name**.
3. Introduce el **nombre** nuevo (máx. 20 caracteres).
4. Pulsa **Save**.
5. El nombre se aplica (o al reiniciar, según firmware).

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Nombre** | Nombre BLE | `Marauder` |

---

## 📊 Qué genera

### En pantalla

```text
=== Set BT Name ===
Nombre actual: Marauder
Nombre nuevo:  MiMarauder

[Save]
```

No genera archivos. El cambio es en memoria.

---

## 🎯 Para qué sirve

### 1. Identificación

Si tienes varios Marauders, puedes ponerles nombres distintos para distinguirlos.

### 2. Camuflaje

Si quieres que el Marauder no sea reconocible, ponle un nombre genérico (`ESP32`, `BLE_Device`, etc.).

### 3. Suplantación

Si quieres hacerte pasar por otro dispositivo, usa su nombre.

### 4. Pruebas

Si estás probando apps BLE, puedes cambiar el nombre para ver cómo reaccionan.

---

## ⚠️ Advertencias

- **Legalidad:** suplantar el nombre de un dispositivo ajeno es **delito**.
- **Longitud:** máximo 20 caracteres.
- **Persistencia:** algunos firmwares no guardan el nombre tras reiniciar.
- **Detección:** los sistemas modernos detectan nombres duplicados.

---

## 🔗 Relacionado

- [BT Info](../sniffers/bt-info.md) — info del módulo
- [Set BT MAC](set-bt-mac.md) — cambia la MAC
- [BT Status](bt-status.md) — estado del módulo
