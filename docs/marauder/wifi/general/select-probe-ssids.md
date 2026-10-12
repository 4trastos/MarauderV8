# 📡 Select Probe SSIDs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Select Probe SSIDs** permite seleccionar **qué SSIDs de la lista** se usarán en los **probe requests** que emite el Marauder. No todos los SSIDs generados tienen por qué usarse; esta herramienta filtra cuáles sí.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Select Probe SSIDs**.
3. Verás la lista de SSIDs disponibles (generados con **Generate SSIDs** o añadidos con **Add SSIDs**).
4. Marca/desmarca los SSIDs que quieras usar.
5. Pulsa **Save**.
6. Los SSIDs seleccionados se usarán en **Probe Req Flood**, **Karma** y otras herramientas que emitan probes.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Selección** | SSIDs marcados | Todos |
| **Guardar** | Guardar selección | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Select Probe SSIDs ===
Lista: 50 SSIDs

[x] MiFibra-BB6F
[x] Movistar_5G
[ ] Vodafone-2.4G
[x] FreeWiFi
[ ] HackMe
...

Seleccionados: 3/50
```

### En la SD (opcional)

Un archivo `.txt` con los SSIDs seleccionados:

```text
MiFibra-BB6F
Movistar_5G
FreeWiFi
```

---

## 🎯 Para qué sirve

### 1. Filtrar probes

Si solo quieres que el Marauder emita probes para **redes concretas** (las de tu casa, por ejemplo), usa esta herramienta.

### 2. Ataques dirigidos

Para un ataque **Karma** o **Evil Portal**, solo quieres responder a probes de SSIDs concretos. Aquí los seleccionas.

### 3. Ahorro de recursos

Emitir 500 probes por segundo consume más batería que emitir 10. Selecciona solo los necesarios.

---

## ⚠️ Advertencias

- **Dependencia:** necesitas tener SSIDs en la lista (con **Generate SSIDs** o **Add SSIDs**).
- **Guardado:** si no guardas, la selección se pierde al reiniciar el Marauder.
- **Uso:** esta herramienta no emite nada. Solo configura la lista.

---

## 🔗 Relacionado

- [Generate SSIDs](generate-ssids.md) — genera la lista
- [Add SSIDs](add-ssids.md) — añade SSIDs manualmente
- [Probe Req Flood](../attacks/probe-req-flood.md) — usa los SSIDs seleccionados
- [Karma](../attacks/karma.md) — usa los SSIDs seleccionados
