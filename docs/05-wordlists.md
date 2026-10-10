# El Diccionario (Wordlist)

[Volver al índice](../README.md)

## Contenido:

 - [Descarga directa de rockyou.txt](#opción-1-descarga-directa-la-más-sencilla)
 - [Usar SecLists (mas completo)](#opción-2-usar-seclists-más-completo)
 - [Cómo crear un diccionario propio de pruebas (Paso a paso)](#cómo-crear-un-diccionario-propio-de-pruebas-paso-a-paso)

---

Una vez confirmado que tu archivo tiene el Handshake, el siguiente paso es conseguir o crear un diccionario de claves.

Para pruebas en entornos controlados, puedes usar diccionarios comunes como `rockyou.txt` o crear un archivo de texto plano llamado `dictionary.txt` donde cada línea sea una contraseña candidata (incluyendo la real para probar que funciona):

```text
12345678
password
tu_contraseña_real_de_prueba
87654321

```

### ¿Qué es `rockyou.txt`?

Es el diccionario de contraseñas más famoso y utilizado en auditorías de seguridad y laboratorios de pruebas en todo el mundo. Es un archivo de texto plano que contiene millones de las contraseñas más comunes que la gente suele usar (como `12345678`, `password`, `qwerty`, etc.). En la mayoría de distribuciones enfocadas a ciberseguridad (como Kali Linux) ya viene preinstalado, pero en Ubuntu estándar normalmente hay que descargarlo o crearse uno propio para pruebas controladas.

Tienes varias opciones para conseguir `rockyou.txt` en Ubuntu:

### Opción 1: Descarga directa (la más sencilla)

Descarga el archivo comprimido desde el repositorio de Praetorian y descomprímelo:

```bash
wget https://github.com/praetorian-inc/Hob0Rules/raw/master/wordlists/rockyou.txt.gz
gunzip rockyou.txt.gz
```

Esto te dejará `rockyou.txt` en el directorio actual.

### Opción 2: Usar SecLists (más completo)

Si quieres tener muchas más listas de seguridad además de `rockyou.txt`, puedes clonar el repositorio de SecLists, que es la fuente más fiable y recomendada:

```bash
# Crear el directorio de wordlists
sudo mkdir -p /ruta/path/wordlists

# Clonar SecLists
sudo git clone https://github.com/danielmiessler/SecLists.git
```

`rockyou.txt` estará dentro en `SecLists/Passwords/Leaked-Databases/`. En algunas versiones del repositorio, el archivo viene comprimido como `rockyou.txt.tar.gz`, así que tendrías que extraerlo:

```bash
cd /ruta/path/wordlists/seclists/Passwords/Leaked-Databases/
sudo tar -xzf rockyou.txt.tar.gz
```

## Cómo crear un diccionario propio de pruebas (Paso a paso)

Para entender cómo funciona y probar si `aircrack-ng` es capaz de descifrar tu clave, lo más rápido y práctico es crear un archivo de texto con un editor y meter unas cuantas palabras de prueba (asegurándote de incluir la contraseña real de tu red de laboratorio entre ellas).

1. **Crear el archivo de texto:** Ubicación en tu proyecto.
Abre la terminal y crea un archivo llamado `dictionary.txt` dentro de la carpeta `wordlists` que ya tienes creada:

```bash
nano wordlists/dictionary.txt

```

2. **Añadir contraseñas candidatas:** Una por línea.
Escribe varias palabras o combinaciones de prueba, pulsa Enter después de cada una. Incluye por ejemplo:

```text
12345678
password
tu_contraseña_real_de_laboratorio
vodafone123
87654321

```

*(Guarda el archivo en nano pulsando `Ctrl + O`, luego `Enter`, y sal con `Ctrl + X`).*


3. **Verificar el archivo creado:** Comprobación rápida.
Comprueba que el archivo se ha guardado correctamente leyendo su contenido:

```bash
cat wordlists/dictionary.txt

```

*Verificación:* Deberías ver en pantalla la lista de contraseñas una debajo de otra.


---

Una vez que tengas tu `dictionary.txt` listo con la contraseña real metida dentro, ya podemos volver a lanzar el comando de `aircrack-ng` apuntando a él y ver la magia en acción.

---