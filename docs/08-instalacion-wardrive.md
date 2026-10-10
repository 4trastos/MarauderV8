# 🛠️ Instalación de Wardrive Tracker

[⬅️ Anterior: Wardrive Tracker](07-wardrive.md) · [Volver al índice](../README.md)

---

Guía paso a paso para instalar y ejecutar **Wardrive Tracker** en Ubuntu (probado en Ubuntu 24.04 con Python 3.12).

## 📋 Requisitos previos

- **Ubuntu** 22.04 o superior (o cualquier distro con Python 3.11+)
- **Python 3.11+** y `pip`
- **Git**
- Conexión a internet (para clonar el repo y cargar los tiles del mapa)

### Comprobar versiones

```bash
python3 --version    # debe ser 3.11 o superior
git --version
```

Si falta algo:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv python3-full git -y
```

---

## 📥 Paso 1: Clonar el repositorio

Sitúate en la carpeta donde quieras tener el proyecto y clona el repo:

```bash
cd ~/Documents/MY_PROJECTS/Cyber_DavGalle
git clone https://github.com/afsh4ck/Wardrive-Tracker.git
```

Git creará una carpeta con el **nombre del repositorio**, no con el que tú hayas puesto en el comando:

```text
Cloning into 'Wardrive-Tracker'...
```

### Verificar la estructura

```bash
cd Wardrive-Tracker
ls -la
```

Deberías ver algo como:

```text
app.py
requirements.txt
README.md
static/
templates/
tools/
wardrive/
.gitignore
```

---

## 🐍 Paso 2: Crear el entorno virtual

Ubuntu 24.04 (Python 3.12) **bloquea `pip install` global** por PEP 668. La solución correcta es un **entorno virtual** aislado dentro del proyecto.

### Crear el venv

Desde dentro de la carpeta del proyecto:

```bash
python3 -m venv .venv
```

Si te da un error tipo `ensurepip is not available`, instala primero:

```bash
sudo apt install python3-venv python3-full
```

Y repite el comando anterior.

### Activar el entorno

```bash
source .venv/bin/activate
```

Sabrás que funcionó porque el prompt cambia:

```text
(.venv) usuario@equipo:~/Documents/MY_PROJECTS/Cyber_DavGalle/Wardrive-Tracker$
```

> ⚠️ **Importante:** el `source` hay que ejecutarlo **cada vez** que abras una terminal nueva. No es permanente.

---

## 📦 Paso 3: Instalar dependencias

Con el venv activado:

```bash
pip install -r requirements.txt
```

Salida esperada (aproximada):

```text
Collecting Flask
Collecting scapy
...
Successfully installed Flask-X.X.X blinker-X.X.X click-X.X.X itsdangerous-X.X.X jinja2-X.X.X markupsafe-X.X.X scapy-X.X.X werkzeug-X.X.X
```

Si ves `Successfully installed`, todo ha ido bien.

> ⚠️ **No uses `--break-system-packages`** aunque Ubuntu te lo sugiera. Puede romper paquetes del sistema. El venv es la forma correcta.

---

## 🚀 Paso 4: Arrancar la aplicación

```bash
python app.py
```

Salida esperada:

```text
 * Serving Flask app 'app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 509-079-495
```

La app está escuchando **solo en localhost**. Ábrela en el navegador:

```text
http://127.0.0.1:5000
```

### ⚠️ No cierres la terminal

Mientras la app corre, esa terminal queda ocupada. Para detenerla: `Ctrl + C`. Si la cierras, la app se para.

---

## 🎯 Paso 5: Probar la aplicación

### Opción A: Con la captura de ejemplo

El repo incluye un generador de captura simulada (redes WiFi + BLE con coordenadas ficticias alrededor de Madrid).

Abre una **segunda terminal** (sin cerrar la primera) y ejecuta:

```bash
cd ~/Documents/MY_PROJECTS/Cyber_DavGalle/Wardrive-Tracker
source .venv/bin/activate
python tools/make_sample.py
```

Esto crea la captura en `sample_data/`. En la interfaz web, pulsa el botón **Cargar ejemplo**.

### Opción B: Con tu propia captura

En la interfaz web, pulsa **Subir captura** (o arrastra el archivo sobre el mapa). Formatos aceptados:

- **PCAP**: `.pcap`, `.pcapng`, `.cap`
- **Log WigleWifi CSV**: `.log`, `.csv`, `.txt` (ESP32 Marauder, Kismet, WiGLE…)

Tamaño máximo: **200 MB**.

---

## 🔧 Uso habitual (para próximas sesiones)

Cada vez que quieras arrancar la app:

```bash
cd ~/Documents/MY_PROJECTS/Cyber_DavGalle/Wardrive-Tracker
source .venv/bin/activate
python app.py
```

Y abrir `http://127.0.0.1:5000`.

Para salir del venv:

```bash
deactivate
```

---

## 🛡️ Paso 6 (opcional): Añadir `.venv` al `.gitignore`

Si vas a subir tu copia a tu propio repo, evita subir el entorno virtual (ocupa cientos de MB):

```bash
echo ".venv/" >> .gitignore
echo "__pycache__/" >> .gitignore
echo "*.pyc" >> .gitignore
echo "sample_data/" >> .gitignore
```

---

## 🐛 Solución de problemas

### Error: `externally-managed-environment`

**Causa:** intentaste `pip install` fuera del venv (PEP 668).

**Solución:** activa el venv con `source .venv/bin/activate` y repite.

### Error: `cd: wardrive_tracker: No such file or directory`

**Causa:** el repo se clona con el nombre `Wardrive-Tracker`, no `wardrive_tracker`.

**Solución:**

```bash
ls -d */ | grep -i wardrive    # ver el nombre real
cd Wardrive-Tracker            # usar el nombre correcto
```

### Error: `No module named venv` o `ensurepip is not available`

**Causa:** falta el paquete `python3-venv` en el sistema.

**Solución:**

```bash
sudo apt install python3-venv python3-full
```

### Error: `Address already in use` (puerto 5000 ocupado)

**Causa:** otra app está usando el puerto 5000.

**Solución:** arranca en otro puerto:

```bash
python app.py --port 5001
```

Y abre `http://127.0.0.1:5001`.

### El mapa aparece en blanco o sin tiles

**Causa:** falta conexión a internet. Leaflet carga los tiles desde servidores online.

**Solución:** comprueba tu conexión.

### Error 500 al subir un PCAP

**Causa:** captura corrupta o formato no soportado.

**Solución:** revisa el traceback en la terminal donde corre Flask y pégame el error.

---

## 📚 Recursos relacionados

- [Documentación oficial de Flask](https://flask.palletsprojects.com/)
- [Repositorio de Wardrive Tracker](https://github.com/afsh4ck/Wardrive-Tracker)
- [PEP 668 — Entornos gestionados externamente](https://peps.python.org/pep-0668/)
- [Guía de venv en Python](https://docs.python.org/3/library/venv.html)