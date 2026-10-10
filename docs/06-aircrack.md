# Lanzar el ataque de comprobación con Aircrack-ng

[Volver al índice](../README.md)

---

Cuando tengas tu archivo `.pcap` con el handshake verificado y tu diccionario listo, el comando en la terminal de Ubuntu para probar si la clave está en la lista es:

```bash
aircrack-ng -w dictionary.txt -b XX:XX:XX:XX:XX:XX eapol_0.pcap

```

*(Sustituye `XX:XX:XX:XX:XX:XX` por la dirección MAC del router/Access Point que capturaste).*

---