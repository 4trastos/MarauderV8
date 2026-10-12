# 📄 Select EP HTML File

[⬅️ Volver al índice General](README.md) · [Volver al índice WiFi](../README.md)

---

## 📝 Descripción

**Select EP HTML File** elige el **archivo HTML** que usará el ataque **Evil Portal**. El HTML es la página web falsa que se mostrará a los clientes que se conecten al AP falso.

Es una utilidad de **preparación**: no lanza el ataque, solo selecciona el HTML que usará.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Crea el HTML** en tu PC:
   - Imita el portal objetivo (login de WiFi, banco, red social, etc.).
   - Debe tener un formulario que envíe las credenciales a algún sitio.
   - Puede ser simple o complejo (CSS, JS, imágenes).

2. **Cópialo a la SD**:
   - Crea la carpeta `/portals/` en la SD.
   - Copia el HTML como `index.html` dentro de `/portals/`.

3. **Inserta la SD en el Marauder**.

### Desde el menú del Marauder

1. Enciende el Marauder.
2. Navega hasta **WiFi → General → Select EP HTML File**.
3. Verás una lista con los HTML disponibles en `/portals/`.
4. Selecciona el que quieras usar.
5. Pulsa **Save**.
6. El HTML queda seleccionado para el próximo **Evil Portal**.

### Parámetros configurables

| Parámetro | Descripción | Valor por defecto |
|---|---|---|
| **HTML** | Archivo a usar | `index.html` |
| **Carpeta** | Carpeta de HTMLs | `/portals/` |

---

## 📊 Qué genera

### En pantalla

```text
=== Select EP HTML File ===
Carpeta: /portals/

Disponibles:
[x] index.html
[ ] google-login.html
[ ] facebook-login.html
[ ] router-admin.html

Seleccionado: index.html
```

No genera archivos. Solo selecciona uno existente.

---

## 🎯 Para qué sirve

### 1. Preparar Evil Portal

Antes de lanzar un **Evil Portal**, necesitas seleccionar el HTML que se mostrará a las víctimas.

### 2. Múltiples portales

Si tienes varios HTML (Google, Facebook, router, etc.), puedes cambiar entre ellos según el objetivo.

### 3. Pruebas A/B

Puedes probar distintos HTML y ver cuál captura más credenciales.

---

## ⚠️ Advertencias

- **SD obligatoria:** el HTML debe estar en la SD. Sin SD, no hay HTML.
- **Formato:** el HTML debe ser válido y autocontenido (o con recursos en la misma carpeta).
- **Tamaño:** HTMLs muy grandes pueden tardar en cargar.
- **Legalidad:** hacer phishing con HTMLs falsos es **delito**. Solo en auditorías autorizadas.
- **Ética:** no uses HTMLs que imiten bancos o servicios reales. Es delito grave.

---

## 🔗 Relacionado

- [Evil Portal](../attacks/evil-portal.md) — ataque que usa este HTML
- [Start AP](start-ap.md) — levanta el AP que muestra el HTML
- [AP Clone Spam](../attacks/ap-clone-spam.md) — combinación con Evil Portal
