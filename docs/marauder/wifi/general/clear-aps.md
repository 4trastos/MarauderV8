# 🗑️ Clear APs

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Clear APs** borra **toda la lista de Puntos de Acceso (APs)** detectados por el Marauder. Es una utilidad de **limpieza**: te permite empezar de cero con un nuevo escaneo.

---

## ⚙️ Cómo se usa

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Clear APs**.
3. El Marauder te pedirá **confirmación**.
4. Pulsa **Yes** para borrar la lista.
5. La lista de APs queda vacía.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **Confirmación** | Pedir confirmación | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Clear APs ===
Lista actual: 47 APs

¿Borrar todos los APs?
[Yes]  [No]

Lista borrada.
APs actuales: 0
```

No genera archivos. Solo borra la lista.

---

## 🎯 Para qué sirve

### 1. Limpiar antes de un nuevo escaneo

Si vas a escanear una zona nueva, borra los APs antiguos.

### 2. Liberar memoria

En zonas densas, la lista de APs puede crecer a cientos. Borrarla libera RAM.

### 3. Evitar confusión

Si tienes APs de una zona anterior mezclados con los de la actual, bórralos.

---

## ⚠️ Advertencias

- **Irreversible:** una vez borrada, la lista no se recupera.
- **Confirmación:** el Marauder pide confirmación.
- **Dependencias:** si tenías ataques dirigidos a APs de esa lista, dejarán de funcionar hasta que vuelvas a escanear.

---

## 🔗 Relacionado

- [Scan AP/STA](../sniffers/scan-ap-sta.md) — escanea APs nuevos
- [Beacon Sniff](../sniffers/beacon.md) — escucha beacons
- [Clear Stations](clear-stations.md) — borra la lista de clientes
- [View AP Info](view-ap-info.md) — ver info de un AP
