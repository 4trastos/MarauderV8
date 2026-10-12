# 📶 Join Saved WiFi

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Join Saved WiFi** conecta el Marauder a una **red WiFi previamente guardada**. Es la versión rápida de **Join WiFi**: no tienes que introducir la contraseña cada vez.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Conecta a la red** con **Join WiFi** y guarda la red.
2. La red se almacena en `/wifi/saved.txt` en la SD.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Join Saved WiFi**.
3. Verás la lista de redes guardadas.
4. Selecciona la red a la que quieres conectarte.
5. Pulsa **Connect**.
6. El Marauder se conectará automáticamente.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Red** | Red guardada a conectar | Ninguna |

---

## 📊 Qué genera

### En pantalla

```text
=== Join Saved WiFi ===
Redes guardadas:
- MiFibra-BB6F
- Movistar_5G
- Trabajo_WiFi

Seleccionada: MiFibra-BB6F

Conectando...
✅ Conectado
IP: 192.168.1.42
RSSI: -62 dBm
```

No genera archivos nuevos. Usa los existentes.

---

## 🎯 Para qué sirve

### 1. Conexión rápida

Si te conectas siempre a la misma red, no tienes que introducir la contraseña cada vez.

### 2. Múltiples redes

Si tienes varias redes guardadas (casa, trabajo, móvil), puedes elegir cuál usar.

### 3. Automatización

Para scripts o usos repetitivos, es más rápido que **Join WiFi**.

---

## ⚠️ Advertencias

- **Dependencia:** necesitas haber guardado alguna red antes con **Join WiFi**.
- **Contraseñas en SD:** las contraseñas se guardan **en texto plano** en `/wifi/saved.txt`. Si pierdes la SD, pierdes las contraseñas.
- **Seguridad:** no guardes contraseñas de redes ajenas. Es un riesgo.
- **Legalidad:** conectarte a redes guardadas sin autorización es **delito**.

---

## 🔗 Relacionado

- [Join WiFi](join-wifi.md) — conecta a una red nueva
- [Clear SSIDs](clear-ssids.md) — borra la lista de SSIDs (no afecta a las redes guardadas)
- [Start AP](start-ap.md) — alternativa: levantar tu propio AP