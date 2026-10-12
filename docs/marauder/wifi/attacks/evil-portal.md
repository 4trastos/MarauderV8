# 🎣 Evil Portal

[⬅️ Volver al índice Attacks](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Evil Portal** levanta un **portal captive falso** para hacer **phishing**. Cuando un cliente se conecta a un AP controlado por el Marauder, se le muestra una página web que **imita** a un portal legítimo (login de WiFi, banco, red social, etc.) para robar sus credenciales.

Es el ataque más **peligroso** del Marauder: no ataca la red, ataca a las **personas**.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Prepara el HTML** del portal:
   - Crea un archivo `index.html` que imite el portal objetivo.
   - Cópialo a la SD en `/portals/`.
   - Selecciónalo en **General → Select EP HTML File**.

2. **Configura el AP falso**:
   - SSID: el nombre de la red que quieres imitar.
   - Canal: el mismo que la red original.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → Attacks → Evil Portal**.
3. Selecciona el **HTML** a usar.
4. Selecciona el **SSID** del AP falso.
5. Pulsa **Start**.
6. El Marauder levanta un AP falso con portal captive.
7. Los clientes que se conecten verán tu HTML falso.
8. Las credenciales que introduzcan se guardan en la SD.
9. Pulsa **Stop** para detener.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **HTML** | Página a mostrar | `index.html` |
| **SSID** | Nombre del AP falso | `FreeWiFi` |
| **Canal** | Canal donde emitir | 1 |
| **Guardar** | Guardar credenciales en SD | Sí |

---

## 📊 Qué genera

### En pantalla

```text
=== Evil Portal ===
HTML: index.html
SSID: FreeWiFi
Canal: 1

Estado: Activo
Clientes conectados: 2
Credenciales capturadas: 1
```

### En la SD

Un archivo `.txt` con las credenciales:

```text
Timestamp,IP,Username,Password
2026-10-11 12:35:01,192.168.4.2,admin,password123
```

---

## 🎯 Para qué sirve

### 1. Auditorías de concienciación

Demostrar a los empleados de una empresa lo fácil que es caer en un phishing WiFi.

### 2. Formación en seguridad

En cursos de ciberseguridad, mostrar el ataque en vivo.

### 3. Pruebas de penetración autorizadas

En un pentest, capturar credenciales para demostrar vulnerabilidades.

### 4. Investigación

Estudiar cómo los usuarios interactúan con portales captive falsos.

---

## ⚠️ Advertencias

- **Legalidad:** hacer phishing a personas es **delito grave**. En España, art. 248 (estafa) y 197 bis (acceso ilícito). Multas y prisión.
- **Ética:** incluso con autorización escrita, hacer phishing a personas reales es **muy delicado**. Asegúrate de tener permiso explícito.
- **Detección:** los portales captive falsos son detectables (certificado, HTML sospechoso).
- **Alcance:** limitado (~10-30 metros).
- **Credenciales:** las credenciales capturadas son **información sensible**. No las uses, no las compartas, bórralas tras la auditoría.
- **Responsabilidad:** si alguien usa este ataque para phishing real, es **delito**. No lo hagas.

---

## 🔗 Relacionado

- [AP Clone Spam](ap-clone-spam.md) — para imitar el AP original
- [Karma](karma.md) — para responder a probes con el SSID correcto
- [Select EP HTML](../general/select-ep-html.md) — para elegir el HTML
- [Start AP](../general/start-ap.md) — para levantar el AP
