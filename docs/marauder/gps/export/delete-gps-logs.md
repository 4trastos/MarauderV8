# 📤 Delete GPS Logs

[⬅️ Volver al índice GPS](../README.md) · [Volver al índice Marauder](../../README.md)

---

## 📝 Descripción

**Delete GPS Logs** borra **logs GPS** de la tarjeta SD. Puedes borrar:

- **Un log individual**.
- **Todos los logs** de un tipo.
- **Todos los logs** de GPS.

Es útil para:

- **Liberar espacio** en la SD.
- **Eliminar datos sensibles**.
- **Limpiar** después de una auditoría.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder con la **SD insertada**.
2. Navega hasta **GPS → Export → Delete GPS Logs**.
3. Selecciona:
   - **Un log individual**: navega y selecciona.
   - **Todos de un tipo**: selecciona el tipo.
   - **Todos**: borra todo.
4. Pulsa **Delete**.
5. Confirma.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Selección** | Log individual o tipo | Ninguno |
| **Confirmación** | Pedir confirmación | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Delete GPS Logs ===
Logs: 5

¿Borrar todos?
[Yes]  [No]

Logs borrados: 5
```

No genera archivos. Solo borra.

---

## 🎯 Para qué sirve

### 1. Liberar espacio

Si la SD está llena, **Delete GPS Logs** libera espacio.

### 2. Eliminar datos sensibles

Si has capturado datos sensibles (SSIDs, MACs), bórralos para no dejar rastro.

### 3. Limpiar después de una auditoría

Si has hecho una auditoría, borra los logs para no dejar evidencia.

### 4. Gestión de logs

Si tienes muchos logs antiguos, bórralos para mantener la SD ordenada.

---

## ⚠️ Advertencias

- **Irreversible:** una vez borrados, los logs no se recuperan.
- **Confirmación:** el Marauder pide confirmación para evitar borrados accidentales.
- **SD obligatoria:** sin SD, no hay logs que borrar.
- **Backup:** si quieres conservar algún log, cópialo al PC antes de borrar.

---

## 🔗 Relacionado

- [View SD Logs](view-sd-logs.md) — ver logs antes de borrar
- [Export WigleWifi](export-wiglewifi.md) — exportar antes de borrar
- [Export GPX](export-gpx.md) — exportar antes de borrar
- [Export KML](export-kml.md) — exportar antes de borrar