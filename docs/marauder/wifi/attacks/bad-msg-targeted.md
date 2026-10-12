# 💥 Bad Msg Targeted

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Bad Msg Targeted** es como **Bad Msg**, pero envía las tramas malformadas a **un dispositivo específico** en lugar de a todos. Es menos invasivo y más preciso.

Útil cuando quieres atacar un dispositivo concreto sin afectar a los demás.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Escanea las redes** con **Scan AP/STA** para identificar el dispositivo objetivo.
2. Anota su **MAC** y el **canal** donde está.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Bad Msg Targeted**.
3. Selecciona el **dispositivo objetivo** (MAC).
4. Configura el **tipo de trama malformada**.
5. Configura el **intervalo** entre tramas.
6. Pulsa **Start**.
7. El Marauder enviará tramas malformadas solo al objetivo.
8. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Objetivo** | MAC del dispositivo | Ninguno |
| **Tipo** | Tipo de trama malformada | Varios |
| **Intervalo** | Tiempo entre tramas | 100 ms |
| **Canal** | Canal donde emitir | El del objetivo |

---

## 📊 Qué genera

### En pantalla

```text
=== Bad Msg Targeted ===
Objetivo: 3C:5A:B4:12:34:56
Tipo: Malformed association request
Intervalo: 100 ms
Canal: 6

Tramas enviadas: 5000
```

### En el aire

Miles de tramas malformadas, todas dirigidas al objetivo. Solo ese dispositivo las procesa.

---

## 🎯 Para qué sirve

### 1. Ataque dirigido

Si quieres atacar un dispositivo concreto sin afectar a los demás.

### 2. Pruebas de vulnerabilidad

Estudiar si un dispositivo específico es vulnerable a Bad Msg.

### 3. Interrupción selectiva

Interrumpir la conexión de un dispositivo sin afectar a los demás.

### 4. Investigación

Analizar la respuesta de un dispositivo específico a tramas malformadas.

---

## ⚠️ Advertencias

- **Legalidad:** igual que Bad Msg. **Delito** si es dispositivo ajeno.
- **Daños:** puede **crashear** el dispositivo objetivo.
- **Detección:** más difícil que Bad Msg (solo afecta a uno).
- **Alcance:** limitado (~10-30 metros).
- **Ética:** no uses Bad Msg Targeted contra dispositivos ajenos. Es delito.

---

## 🔗 Relacionado

- [Bad Msg](bad-msg.md) — versión no dirigida
- [Deauth Targeted](deauth-targeted.md) — ataque dirigido similar
- [Scan AP/STA](../sniffers/scan-ap-sta.md) — para identificar el objetivo
