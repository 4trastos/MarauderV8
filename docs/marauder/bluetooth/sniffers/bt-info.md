# 📡 BT Info

[⬅️ Volver al índice Bluetooth](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**BT Info** muestra **información del adaptador Bluetooth** del Marauder:

- **MAC** del adaptador.
- **Nombre** BLE.
- **Versión** de Bluetooth.
- **Estado** (activo/inactivo).
- **Firmware** del módulo.

Es una utilidad de **consulta**: no modifica nada, solo muestra datos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **Bluetooth → Sniffers → BT Info**.
3. Verás toda la información del adaptador.
4. Pulsa **Back** para volver.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Actualizar** | Refrescar info | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== BT Info ===
MAC:         DE:AD:BE:EF:12:34
Nombre:      Marauder
Versión:     Bluetooth 5.0
Estado:      Activo
Firmware:    1.2.3
```

No genera archivos. Solo muestra info en pantalla.

---

## 🎯 Para qué sirve

### 1. Ver la MAC del adaptador

Si necesitas la MAC del Marauder para configurar filtros en otro dispositivo.

### 2. Ver el nombre BLE

Si has cambiado el nombre con **Set BT Name**, aquí lo confirmas.

### 3. Diagnóstico

Si el Bluetooth no funciona, **BT Info** te dice si el módulo está activo.

### 4. Documentación

Si necesitas documentar la configuración del Marauder, **BT Info** te da los datos.

---

## ⚠️ Advertencias

- **Dependencia:** el módulo Bluetooth debe estar activo (**BT Enable**).
- **Actualización:** la info se actualiza cada vez que entras.

---

## 🔗 Relacionado

- [BT Enable](../general/bt-enable.md) — activa el Bluetooth
- [BT Disable](../general/bt-disable.md) — desactiva el Bluetooth
- [Set BT MAC](../general/set-bt-mac.md) — cambia la MAC
- [Set BT Name](../general/set-bt-name.md) — cambia el nombre
