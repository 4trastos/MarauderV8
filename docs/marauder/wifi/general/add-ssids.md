# 📡 Add SSIDs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Add SSIDs** permite **añadir SSIDs manualmente** a la lista del Marauder. Útil cuando quieres usar SSIDs específicos (el de tu red, el de una red objetivo, nombres concretos) en lugar de generarlos aleatoriamente.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Add SSIDs**.
3. Escribe el SSID que quieras añadir (máx. 32 caracteres).
4. Pulsa **Add**.
5. Repite para añadir más SSIDs.
6. Pulsa **Save** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **SSID** | Nombre a añadir | Ninguno |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Add SSIDs ===
Lista actual: 50 SSIDs

Nuevo SSID: MiFibra-BB6F
[Add]

Lista actualizada:
...
MiFibra-BB6F
```

### En la SD

Un archivo `.txt` con la lista completa:

```text
a8f3k2l9
Zx7QmP4v
...
MiFibra-BB6F
```

---

## 🎯 Para qué sirve

### 1. Añadir SSIDs reales

Si quieres hacer **Karma** o **Evil Portal** contra una red concreta, añade su SSID aquí.

### 2. Añadir SSIDs personalizados

Si tienes nombres específicos que quieres usar en un ataque, añádelos manualmente.

### 3. Añadir SSIDs de un diccionario

Si tienes una lista de SSIDs en un archivo, puedes añadirlos uno a uno (o importarlos, según firmware).

---

## ⚠️ Advertencias

- **Longitud máxima:** 32 caracteres (límite de 802.11).
- **Charset:** algunos caracteres especiales pueden no aceptarse.
- **Guardado:** si no guardas, los SSIDs se pierden al reiniciar.
- **Ética:** añadir SSIDs de redes ajenas para atacarlas es **delito**.

---

## 🔗 Relacionado

- [Generate SSIDs](generate-ssids.md) — genera SSIDs aleatorios
- [Clear SSIDs](clear-ssids.md) — borra la lista
- [Select Probe SSIDs](select-probe-ssids.md) — selecciona qué SSIDs usar
- [Beacon Spam List](../attacks/beacon-spam-list.md) — usa los SSIDs añadidos
