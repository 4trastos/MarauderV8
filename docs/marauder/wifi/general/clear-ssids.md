# 🗑️ Clear SSIDs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Clear SSIDs** borra **toda la lista de SSIDs** guardada en el Marauder. Es una utilidad de **limpieza**: te permite empezar de cero con una lista nueva.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Clear SSIDs**.
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
=== Clear SSIDs ===
Lista actual: 50 SSIDs

¿Borrar todos los SSIDs?
[Yes]  [No]

Lista borrada.
SSIDs actuales: 0
```

No genera archivos. Solo borra la lista.

---

## 🎯 Para qué sirve

### 1. Limpiar antes de un nuevo ataque

Si vas a hacer un ataque con SSIDs nuevos, borra los antiguos.

### 2. Liberar memoria

Aunque el impacto es mínimo, borrar listas grandes libera algo de RAM.

### 3. Privacidad

Si has añadido SSIDs de redes ajenas, bórralos para no dejar rastro.

---

## ⚠️ Advertencias

- **Irreversible:** una vez borrada, la lista no se recupera (a menos que la tengas guardada en SD).
- **Confirmación:** el Marauder pide confirmación para evitar borrados accidentales.
- **Dependencias:** si tenías ataques configurados con esa lista, dejarán de funcionar.

---

## 🔗 Relacionado

- [Generate SSIDs](generate-ssids.md) — genera una lista nueva
- [Add SSIDs](add-ssids.md) — añade SSIDs manualmente
- [Select Probe SSIDs](select-probe-ssids.md) — selecciona qué usar
