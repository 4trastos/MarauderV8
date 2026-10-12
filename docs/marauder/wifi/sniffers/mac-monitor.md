# 📡 MAC Monitor

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**MAC Monitor** vigila **direcciones MAC específicas** y avisa cuando aparecen o desaparecen del aire. Es la herramienta de **seguimiento** del Marauder: te dice **si un dispositivo concreto está presente** en la zona, sin tener que buscarlo manualmente.

Útil para:

- **Rastrear** dispositivos específicos (tuyos o autorizados).
- **Vigilar** si un dispositivo no autorizado aparece en tu red.
- **Detectar** cuándo un dispositivo se conecta o desconecta.
- **Auditar** la presencia de dispositivos en una ubicación.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Sniffers → MAC Monitor**.
3. **Añade las MACs** que quieres vigilar:
   - Una por una, manualmente.
   - O importa una lista desde la SD.
4. Configura el **modo de alerta**:
   - **Presencia**: avisa cuando la MAC aparece.
   - **Ausencia**: avisa cuando la MAC desaparece.
   - **Ambos**.
5. Pulsa **Start**.
6. El Marauder escaneará todos los canales y comparará las MACs vistas con tu lista.
7. Cuando una MAC de la lista aparezca o desaparezca, verás una **alerta**.
8. Pulsa **Stop** cuando termines.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Lista de MACs** | MACs a vigilar | Ninguna |
| **Modo** | Presencia, ausencia o ambos | Ambos |
| **Canales** | Qué canales escanear | Todos |
| **Alerta** | Sonido, led, vibración | Sonido |
| **Guardar** | Guardar en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== MAC Monitor ===
Vigilando 3 MACs:
- 3C:5A:B4:12:34:56 (móvil de casa)
- A4:83:E7:11:22:33 (portátil)
- F0:18:98:AA:BB:CC (tablet)

Estado actual:
3C:5A:B4:12:34:56   ✅ Presente    RSSI: -62    Canal: 6
A4:83:E7:11:22:33   ❌ Ausente     —            —
F0:18:98:AA:BB:CC   ✅ Presente    RSSI: -70    Canal: 1

Historial de eventos:
12:35:01  3C:5A:B4:12:34:56  APARECIÓ  Canal: 6  RSSI: -62
12:35:05  A4:83:E7:11:22:33  DESAPARECIÓ
12:35:12  F0:18:98:AA:BB:CC  APARECIÓ  Canal: 1  RSSI: -70
```

### En la SD

Un archivo `.txt` con el historial:

```text
Timestamp,MAC,Event,Channel,RSSI
2026-10-11 12:35:01,3C:5A:B4:12:34:56,APARECIO,6,-62
2026-10-11 12:35:05,A4:83:E7:11:22:33,DESAPARECIO,,
2026-10-11 12:35:12,F0:18:98:AA:BB:CC,APARECIO,1,-70
```

---

## 🎯 Para qué sirve

### 1. Rastrear dispositivos específicos

El caso de uso principal. Si quieres saber **si un dispositivo está presente** en una zona:

- Añade su MAC a la lista.
- **MAC Monitor** te avisa cuando aparece.

Útil para:

- Vigilar a un familiar (con su consentimiento).
- Rastrear un dispositivo perdido.
- Auditar la presencia de dispositivos en una oficina.

### 2. Detectar dispositivos no autorizados

Si administras una red, puedes:

- Añadir las MACs **autorizadas** a la lista.
- Ver si aparece alguna **no autorizada**.

Útil para:

- Detectar intrusos en tu red.
- Auditar la seguridad de una oficina.
- Vigilar si alguien se conecta a tu red.

### 3. Auditar presencia de dispositivos

Si necesitas **documentar** qué dispositivos están presentes en una ubicación en un momento dado:

- **MAC Monitor** te da el historial.
- Puedes exportarlo a CSV.
- Puedes analizarlo en Excel/Sheets.

Útil para:

- Auditorías de oficina.
- Control de acceso.
- Análisis forense.

### 4. Rastrear Pwnagotchis / Pineapples

Si **Detect Pwnagotchi** o **Detect Pineapple** detecta uno, puedes añadir su MAC a **MAC Monitor** para vigilar si sigue en la zona.

### 5. Base para Fox Hunt

Si **MAC Monitor** detecta que una MAC está presente, puedes usar **Fox Hunt** para localizarla físicamente.

---

## 🎯 Diferencias con Fox Hunt

| Aspecto | MAC Monitor | Fox Hunt |
|---|---|---|
| **Objetivo** | Múltiples MACs | Una sola MAC/BSSID |
| **Tipo** | Presencia/ausencia | Localización física |
| **Salida** | Historial de eventos | RSSI en tiempo real |
| **Uso** | Vigilancia | Búsqueda |
| **Pantalla** | Lista + eventos | Gráfico de intensidad |

**En la práctica:**

- **MAC Monitor** te dice **si está**.
- **Fox Hunt** te dice **dónde está**.

Combínalos: primero **MAC Monitor** para confirmar presencia, luego **Fox Hunt** para localizar.

---

## ⚠️ Advertencias

- **Legalidad:** rastrear dispositivos **ajenos** sin consentimiento es **invasión de privacidad**. En España, art. 197 CP. Solo hazlo con dispositivos tuyos o con autorización escrita.
- **MAC randomization:** muchos móviles modernos usan **MAC aleatoria**. Si el dispositivo que rastreas usa MAC randomization, verás una MAC distinta cada vez y **MAC Monitor** no funcionará.
- **Canales:** el Marauder escanea secuencialmente, así que puede perder algunas apariciones si el dispositivo está en un canal que no está escuchando en ese momento.
- **Distancia:** solo detectas dispositivos a tu alcance. Si están lejos, no los ves.
- **Falsos positivos:** otros dispositivos pueden tener la misma MAC (raro, pero posible con spoofing).
- **Almacenamiento:** si vigilas muchas MACs durante mucho tiempo, el historial puede crecer rápido.

### Cómo evitar el problema de MAC randomization

- **Si el dispositivo es tuyo:** desactiva la MAC randomization en su configuración WiFi.
- **Si el dispositivo es de otro:** no puedes hacer nada. La MAC randomization es una medida de privacidad deliberada.

---

## 🔗 Relacionado

- [Fox Hunt](fox-hunt.md) — para localizar físicamente las MACs vigiladas
- [Scan AP/STA](scan-ap-sta.md) — para identificar MACs de clientes
- [Detect Pwnagotchi](detect-pwnagotchi.md) — para detectar Pwnagotchis
- [Detect Pineapple](detect-pineapple.md) — para detectar Pineapples
- [Deauth Sniff](deauth.md) — para detectar ataques de MACs vigiladas