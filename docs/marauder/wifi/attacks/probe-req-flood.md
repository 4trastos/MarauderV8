# 🌊 Probe Req Flood

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Probe Req Flood** inunda el aire con **probe requests falsos**. Los probe requests son las "preguntas" que hacen los dispositivos buscando redes conocidas. Al inundar el aire con miles de ellos, el atacante:

- **Satura** a los APs cercanos (tienen que procesar cada probe).
- **Confunde** a los sistemas de detección.
- **Oculta** los probe requests reales entre el ruido.
- **Consume** batería de los dispositivos cercanos.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Probe Req Flood**.
3. Selecciona la **lista de SSIDs** a buscar (o usa la por defecto).
4. Configura el **intervalo** entre probes (por defecto: 10 ms).
5. Pulsa **Start**.
6. El Marauder inundará el aire con probe requests.
7. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Lista SSIDs** | SSIDs a buscar | Lista por defecto |
| **Intervalo** | Tiempo entre probes | 10 ms |
| **Canal** | Canal donde emitir | 1 |
| **Aleatorio** | Orden aleatorio | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Probe Req Flood ===
SSIDs: 100
Intervalo: 10 ms
Canal: 1

Emitiendo:
Probe requests enviados: 5000
```

### En el aire

Miles de probe requests por segundo, todos con SSIDs distintos. Los APs cercanos se saturan procesando cada uno.

---

## 🎯 Para qué sirve

### 1. Saturación de APs

Un AP tiene que procesar cada probe request que recibe. Si recibe miles por segundo, se satura y deja de responder a los legítimos.

### 2. Confusión de sistemas de detección

Los WIDS/WIPS analizan probe requests para detectar dispositivos. Con miles de probes falsos, el análisis se vuelve imposible.

### 3. Ocultación de probes reales

Si estás haciendo un ataque y quieres ocultar tus probe requests reales, los falsos sirven de ruido.

### 4. Pruebas de estrés

Ver cómo se comporta una red bajo un flood de probes.

---

## ⚠️ Advertencias

- **Legalidad:** inundar el aire con probes falsos es **interferencia**. Delito en España.
- **Detección:** fácil de detectar (muchos probes desde una MAC).
- **Saturación:** puede afectar a **otras redes cercanas**.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** la mayoría de APs modernos ignoran probes anómalos, pero los antiguos se saturan.
- **Batería:** el flood consume mucha energía del Marauder.

---

## 🔗 Relacionado

- [Probe Request Sniff](../sniffers/probe-request.md) — sniffer de probes
- [Karma](karma.md) — ataque que responde a probes
- [Evil Portal](evil-portal.md) — portal captive que usa probes
- [Beacon Spam List](beacon-spam-list.md) — ataque similar con beacons
