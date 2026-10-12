# 📡 BT Status

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BT Status** muestra el **estado actual** del módulo Bluetooth del Marauder:

- **Activo/Inactivo**.
- **MAC** actual.
- **Nombre** BLE.
- **Conexiones** activas.
- **Errores** recientes.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → General → BT Status**.
3. Verás el estado actual.
4. Pulsa **Refresh** para actualizar.
5. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Refresh** | Actualizar estado | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BT Status ===
Estado:      Activo
MAC:         DE:AD:BE:EF:12:34
Nombre:      Marauder
Conexiones:  0
Errores:     0

Última actualización: 12:35:01
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Diagnóstico

Si el Bluetooth no funciona, **BT Status** te dice si el módulo está activo.

### 2. Ver conexiones activas

Si tienes dispositivos BLE conectados al Marauder (por ejemplo, en BLE Service Scan), aquí los ves.

### 3. Ver errores

Si hay errores recientes, **BT Status** los lista.

### 4. Documentación

Si necesitas documentar el estado del Marauder, **BT Status** te da los datos.

---

## ⚠️ Advertencias

- **Dependencia:** el módulo Bluetooth debe estar activo.
- **Actualización:** pulsa **Refresh** para datos frescos.

---

## 🔗 Relacionado

- [BT Info](../sniffers/bt-info.md) — info del módulo
- [BT Enable](bt-enable.md) — activa el Bluetooth
- [BT Disable](bt-disable.md) — desactiva el Bluetooth