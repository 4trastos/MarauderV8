# ¿Cómo saber si tu `.pcap` sirve? (El Handshake)

[Volver al índice](../README.md)

---

**sí, necesitas que ese PCAP contenga el tráfico del *Handshake* completo** para poder descifrarlo con un diccionario, y **no necesitas ningún archivo adicional**, solo un buen diccionario (`wordlists`).

Un archivo `.pcap` capturado por un sniffer guarda todo el tráfico de radiofrecuencia que escucha. Si en el momento de la captura ningún dispositivo se conectó o reconoció a la red, el archivo solo tendrá tramas vacías y **no servirá**.

Para que un diccionario funcione, el archivo `.pcap` **debe contener obligatoriamente el intercambio de 4 mensajes (*4-Way Handshake*)** entre un cliente y el router.

Puedes comprobarlo rápidamente en tu Ubuntu con `aircrack-ng` (viene en el paquete `aircrack-ng`):

```bash
sudo apt install aircrack-ng -y
aircrack-ng xxxxxx.pcap

```

* **Si el resultado muestra una lista de redes y dice *"1 handshake"* (o similar):** ¡Perfecto! Tienes el paquete necesario.
* **Si dice *"0 handshake"*:** Significa que la captura no cogió la conexión y tendrás que volver a capturar (puedes acelerarlo forzando una desconexión o desautenticación si estás probando con tus propios equipos).

---