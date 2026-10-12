# 🌊 SAE Commit Flood

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**SAE Commit Flood** inunda el aire con **tramas SAE Commit** falsas. SAE (*Simultaneous Authentication of Equals*) es el protocolo de autenticación de **WPA3**. Al inundar con SAE Commits, se saturan los APs WPA3 cercanos.

Es un ataque **específico para WPA3**. A diferencia de los ataques contra WPA2, este no busca capturar handshakes, sino **saturar** el AP.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → SAE Commit Flood**.
3. Configura el **intervalo** entre tramas.
4. Pulsa **Start**.
5. El Marauder enviará SAE Commits a todos los APs WPA3 cercanos.
6. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Intervalo** | Tiempo entre tramas | 10 ms |
| **Canal** | Canal donde emitir | 1 |
| **Objetivo** | AP específico o todos | Todos |

---

## 📊 Qué genera

### En pantalla

```text
=== SAE Commit Flood ===
Intervalo: 10 ms
Canal: 1

Tramas enviadas: 5000
APs afectados: 2
```

### En el aire

Miles de SAE Commits. Los APs WPA3 cercanos tienen que procesar cada uno, saturándose.

---

## 🎯 Para qué sirve

### 1. Saturación de APs WPA3

Los APs WPA3 tienen que procesar cada SAE Commit. Si reciben miles por segundo, se saturan y dejan de responder a los legítimos.

### 2. Pruebas de estrés

Ver cómo se comporta un AP WPA3 bajo un flood de SAE Commits.

### 3. Investigación

Estudiar el comportamiento de WPA3 bajo ataques de saturación.

### 4. Demostraciones

Mostrar el impacto de un SAE Commit Flood en una presentación.

---

## ⚠️ Advertencias

- **Legalidad:** igual que otros floods. **Delito** en redes ajenas.
- **Detección:** los WIDS/WIPS detectan SAE Commits anómalos.
- **Alcance:** limitado (~10-30 metros).
- **Impacto:** algunos APs WPA3 ignoran SAE Commits de MACs desconocidas.
- **WPA3 específico:** solo afecta a redes WPA3. Las WPA2 son inmunes.

---

## 🔗 Relacionado

- [SAE Commit](../sniffers/sae-commit.md) — sniffer de SAE Commits
- [Deauth Flood](deauth-flood.md) — ataque similar pero para WPA2
- [Beacon Spam List](beacon-spam-list.md) — ataque de saturación similar
