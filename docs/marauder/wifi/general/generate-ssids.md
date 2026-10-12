# 📡 Generate SSIDs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Generate SSIDs** genera una **lista de SSIDs aleatorios** que se pueden usar en ataques como **Beacon Spam List**, **Probe Req Flood**, **Evil Portal** o **Karma**. Los SSIDs se generan con longitud y charset configurables.

Es una utilidad de **preparación**: no emite nada por sí sola, solo crea la lista que luego usarán otras herramientas.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Generate SSIDs**.
3. Configura:
   - **Cantidad**: cuántos SSIDs generar (por defecto: 50).
   - **Longitud**: caracteres por SSID (por defecto: 8-32).
   - **Charset**: alfabético, alfanumérico, completo (con símbolos).
4. Pulsa **Generate**.
5. La lista se guarda en memoria (y opcionalmente en SD).
6. Ahora puedes usar esa lista en **Beacon Spam List** o **Probe Req Flood**.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Cantidad** | Nº de SSIDs a generar | 50 |
| **Longitud mínima** | Caracteres mínimos | 8 |
| **Longitud máxima** | Caracteres máximos | 32 |
| **Charset** | Alfabético / alfanumérico / completo | Alfanumérico |
| **Guardar** | Guardar en SD | No |

---

## 📊 Qué genera

### En pantalla

```text
=== Generate SSIDs ===
Cantidad: 50
Longitud: 8-32
Charset: alfanumérico

Generados:
a8f3k2l9
Zx7QmP4v
9jK2nB5c
...
Total: 50 SSIDs
```

### En la SD (opcional)

Un archivo `.txt`:

```text
a8f3k2l9
Zx7QmP4v
9jK2nB5c
...
```

---

## 🎯 Para qué sirve

### 1. Preparar Beacon Spam

Generar SSIDs únicos para un ataque de Beacon Spam que no use nombres reconocibles.

### 2. Preparar Probe Req Flood

Generar SSIDs para inundar con probes que buscan redes aleatorias.

### 3. Preparar Evil Portal

Generar SSIDs plausibles para un portal captive.

### 4. Pruebas de saturación

Generar cientos de SSIDs para saturar el espectro con nombres únicos.

---

## ⚠️ Advertencias

- **Uso:** esta herramienta no emite nada por sí sola. Solo genera la lista.
- **Almacenamiento:** si generas muchos SSIDs y los guardas, el archivo puede crecer.
- **Repetidos:** si generas muchos SSIDs con poca longitud, pueden repetirse. Aumenta la longitud mínima.

---

## 🔗 Relacionado

- [Beacon Spam List](../attacks/beacon-spam-list.md) — usa los SSIDs generados
- [Probe Req Flood](../attacks/probe-req-flood.md) — usa los SSIDs generados
- [Add SSIDs](add-ssids.md) — añadir SSIDs manualmente
- [Clear SSIDs](clear-ssids.md) — borrar la lista
