# 🗑️ Clear Stations

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Clear Stations** borra **toda la lista de Estaciones (STAs)**, es decir, los **clientes** (móviles, portátiles, tablets) detectados por el Marauder. Es una utilidad de **limpieza**.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Clear Stations**.
3. El Marauder te pedirá **confirmación**.
4. Pulsa **Yes** para borrar la lista.
5. La lista de clientes queda vacía.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Confirmación** | Pedir confirmación | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Clear Stations ===
Lista actual: 12 STAs

¿Borrar todas las STAs?
[Yes]  [No]

Lista borrada.
STAs actuales: 0
```

No genera archivos. Solo borra la lista.

---

## 🎯 Para qué sirve

### 1. Limpiar antes de un nuevo escaneo

Si vas a escanear clientes nuevos, borra los antiguos.

### 2. Liberar memoria

En zonas densas, la lista de clientes puede crecer. Borrarla libera RAM.

### 3. Evitar confusión

Si tienes clientes de una zona anterior mezclados con los de la actual, bórralos.

---

## ⚠️ Advertencias

- **Irreversible:** una vez borrada, la lista no se recupera.
- **Confirmación:** el Marauder pide confirmación.
- **Dependencias:** si tenías ataques dirigidos a clientes de esa lista (Deauth Targeted, Assoc Sleep Targ, etc.), dejarán de funcionar hasta que vuelvas a escanear.

---

## 🔗 Relacionado

- [Scan AP/STA](../sniffers/scan-ap-sta.md) — escanea clientes nuevos
- [Clear APs](clear-aps.md) — borra la lista de APs
- [Select Stations](select-stations.md) — selecciona clientes objetivo
