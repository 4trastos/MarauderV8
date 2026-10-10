# 📶 Wifi Captura de paquetes PCAP

[Volver al índice](../README.md)

---

Un **archivo PCAP** (abreviatura de *Packet Capture*) es un formato estándar que contiene la grabación de todo el tráfico de datos transmitido a través de una red inalámbrica o de cable durante un periodo de tiempo. Funciona esencialmente como un "registro" o "vídeo" de lo que ha viajado por el aire: direcciones MAC, tramas de gestión y paquetes de datos.

En el contexto de la seguridad Wi-Fi, los archivos PCAP son fundamentales para analizar protocolos de red y entender el funcionamiento de intercambios de autenticación como el **WPA Handshake**.

---

### ¿Qué es un WPA Handshake (4-Way Handshake)?

Cuando un dispositivo (como un teléfono o portátil) se conecta a un router Wi-Fi protegido con WPA2 o WPA3, ambos intercambian **4 mensajes clave** antes de permitir la navegación. Este proceso de 4 pasos se conoce como *4-Way Handshake*.

* **Su función:** Permite que el router y el cliente demuestren que conocen la contraseña correcta y deriven las claves de cifrado temporales para la sesión, **sin enviar la contraseña real por el aire**.
* **Contenido de la captura:** El archivo PCAP registrado por un sniffer (como la Marauder) guarda esos 4 mensajes. Dentro de ellos viajan números aleatorios (*nonces*) y un código de autenticación (*MIC*).

---

### Análisis defensivo y auditoría con Wireshark en Ubuntu

Para inspeccionar y analizar capturas PCAP en un entorno de laboratorio o auditoría de red propia, se utiliza **Wireshark**.

#### 1. Instalación de Wireshark en Ubuntu

Abre la terminal e instala la herramienta:

```bash
sudo apt update
sudo apt install wireshark -y

```

*(Opcional: Durante la instalación, si pregunta si los usuarios no superusuarios deben poder capturar paquetes, selecciona "Sí" y añade tu usuario al grupo `wireshark` con `sudo usermod -aG wireshark $USER`).*

---

#### 2. Inspeccionar la captura PCAP

1. Copia el archivo `.pcap` generado por la tarjeta SD a tu equipo Ubuntu.
2. Abre el archivo en Wireshark:
```bash
wireshark /ruta/a/tu/archivo.pcap

```

3. **Filtros útiles en Wireshark:**
* Para ver únicamente los paquetes del intercambio de autenticación (*Handshake*), escribe en la barra de filtro superior:
```text
eapol

```

* Si deseas ver únicamente las tramas de gestión de una red o cliente específico por su dirección MAC:
```text
wlan.addr == XX:XX:XX:XX:XX:XX

```

Si el filtro `eapol` muestra los 4 mensajes (o al menos los pares necesarios 1-2 o 2-3), significa que la captura del Handshake se ha realizado correctamente y está completa para su análisis.

---