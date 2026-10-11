## Paso 4: El verdadero aprendizaje en Wireshark

Ahora viene lo interesante. Independientemente de si Hashcat encuentra la contraseña o no, **puedes usar Wireshark para entender cómo funciona todo esto**.

#### A. ¿Qué buscar en Wireshark (sin la contraseña)?

Incluso sin saber la clave, el `.pcap` es una mina de oro para aprender. Abre tu `eapol_0.pcap` y prueba estos filtros en la barra superior:

1.  **`eapol`**: Este es el filtro clave. Aislará solo los 4 mensajes del handshake. Si los ves, el proceso de autenticación está capturado. En los detalles del paquete (panel inferior), expande **802.1X Authentication** para ver campos como `Replay Counter` (debe seguir la secuencia 1, 1, 2, 2).
2.  **`wlan.fc.type_subtype == 0x08`**: Este filtro muestra solo las **Beacons** (balizas) del router. Ahí puedes ver el SSID, el canal y, muy importante, el **Auth Key Management (AKM) Suite**. Si ves `SAE (SHA256)`, es que tu red usa **WPA3**. **WPA3 no se puede descifrar con la contraseña** usando este método porque usa un intercambio de claves diferente. Si ves `PSK`, es WPA2 y el plan de descifrado funciona.
3.  **`ip` o `arp` o `dhcp`**: Aplica este filtro **antes** de poner la contraseña. Verás que **no aparece nada**. Esto te demuestra que el tráfico IP está cifrado y es ilegible sin la clave.

#### B. ¿Cómo usar la contraseña en Wireshark si la encuentras?

Si Hashcat (o Aircrack-ng) encuentra la contraseña, este es el proceso para ver el tráfico descifrado:

1.  Ve a **Editar → Preferencias → Protocols → IEEE 802.11**.
2.  Marca la casilla **"Enable decryption"** (Habilitar descifrado).
3.  Haz clic en el botón **"Edit..."** junto a "Decryption Keys".
4.  Pulsa el `+` para añadir una nueva clave.
5.  En **Key type**, selecciona **`wpa-pwd`**.
6.  En **Key**, escribe la contraseña y el SSID con este formato exacto: **`tu_contraseña:MiFibra-BB6F`** (sin espacios, con dos puntos en medio).
7.  Acepta todo y observa cómo, mágicamente, los paquetes que antes eran ilegibles ahora muestran direcciones IP, tráfico DNS, etc.

### 💎 Conclusión

El plan es:
1.  **Aircrack-ng** dice "Key not found" porque tu contraseña es fuerte y no está en `rockyou.txt`. Es una **buena noticia** para tu seguridad.
2.  **Usa Hashcat** para probar diccionarios más grandes o variaciones con reglas, es mucho más rápido.
3.  **Usa Wireshark** ahora mismo para **analizar el handshake** (filtro `eapol`) y entender el proceso. Si encuentras la clave, úsala para **descifrar el tráfico** y ver la IP de tus dispositivos.