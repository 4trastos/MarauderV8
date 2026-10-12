# 💥 Bad Msg

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Bad Msg** envía **tramas 802.11 malformadas** a todos los dispositivos cercanos. Las tramas malformadas pueden:

- **Confundir** al firmware de los dispositivos.
- **Crashear** drivers WiFi vulnerables.
- **Interrumpir** conexiones existentes.
- **Provocar** reinicios inesperados.

Es un ataque **muy agresivo** que puede causar daños a dispositivos vulnerables.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Bad Msg**.
3. Configura el **tipo de trama malformada** a enviar.
4. Configura el **intervalo** entre tramas.
5. Pulsa **Start**.
6. El Marauder enviará tramas malformadas a todos los dispositivos cercanos.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Tipo** | Tipo de trama malformada | Varios |
| **Intervalo** | Tiempo entre tramas | 100 ms |
| **Canal** | Canal donde emitir | 1 |

---

## 📊 Qué genera

### En pantalla

```text
=== Bad Msg ===
Tipo: Malformed beacon
Intervalo: 100 ms
Canal: 1

Tramas enviadas: 5000
```

### En el aire

Miles de tramas malformadas. Los dispositivos cercanos pueden:

- Ignorarlas (la mayoría).
- Tener problemas de conexión (algunos).
- Crashear (los más vulnerables).

---

## 🎯 Para qué sirve

### 1. Pruebas de estrés

Ver cómo se comportan dispositivos vulnerables a tramas malformadas.

### 2. Investigación de vulnerabilidades

Estudiar qué dispositivos son vulnerables a Bad Msg.

### 3. Interrupción de red

Si el objetivo es interrumpir una red, Bad Msg puede ser efectivo.

### 4. Demostraciones

Mostrar el impacto de tramas malformadas en una presentación de seguridad.

---

## ⚠️ Advertencias

- **Legalidad:** enviar tramas malformadas es **interferencia grave**. Delito.
- **Daños:** puede **crashear** dispositivos vulnerables. Si un dispositivo médico o industrial está cerca, podría causar daños.
- **Detección:** los WIDS/WIPS detectan tramas malformadas fácilmente.
- **Alcance:** limitado (~10-30 metros).
- **Ética:** no uses Bad Msg contra dispositivos que no son tuyos. Es delito y puede causar daños.

---

## 🔗 Relacionado

- [Bad Msg Targeted](bad-msg-targeted.md) — versión dirigida a un dispositivo
- [Deauth Flood](deauth-flood.md) — ataque similar pero con deauths
- [Quiet Time](quiet-time.md) — silenciar el aire
