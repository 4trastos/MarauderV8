# 🗺️ Wardrive

[⬅️ Volver al índice WiFi](../../README.md) · [Volver al índice Marauder](../../../README.md)

---

## 📝 Descripción

**Wardrive** es la función del Marauder que combina **escaneo pasivo de redes WiFi** con **geolocalización GPS**. Registra cada red detectada junto a las coordenadas donde fue vista, generando un log en formato **WigleWifi CSV** que se puede subir a la base de datos mundial **WiGLE** o analizar con herramientas como **Wardrive Tracker**.

Es la herramienta de referencia para hacer **wardriving responsable**: mapear el espectro WiFi de una zona sin interactuar con las redes.

> ⚠️ **Requiere módulo GPS externo** conectado por UART. El Marauder no trae GPS integrado.

---

## ⚙️ Cómo se usa

### Preparación previa

1. **Conecta el módulo GPS** al Marauder:
   | Marauder | GPS (NEO-6M) |
   |---|---|
   | GPIO 16 (RX2) | TX del GPS |
   | GPIO 17 (TX2) | RX del GPS |
   | 3.3V | VCC |
   | GND | GND |

2. **Verifica el fix GPS** antes de empezar:
   - Ve a **GPS → GPS Info**.
   - Espera a tener al menos **4 satélites** y un **fix 3D**.
   - Sin fix, las coordenadas serán incorrectas o nulas.

3. **Inserta la tarjeta SD** (formateada en FAT32) con las carpetas `/pcap` y `/logs` creadas.

### Desde el menú del Marauder

1. Navega hasta **WiFi → Sniffers → Wardrive**.
2. Configura el **intervalo de escaneo** (por defecto: 1 segundo por canal).
3. Pulsa **Start**.
4. El Marauder empezará a:
   - Escanear los canales 1-13 (2.4 GHz) y 36-165 (5 GHz).
   - Registrar cada red nueva con su SSID, BSSID, cifrado, canal y RSSI.
   - Asociar cada registro a las coordenadas GPS del momento.
5. Muévete por la zona (coche, bici, caminando) para cubrir más terreno.
6. Pulsa **Stop** cuando termines.
7. El log se guarda automáticamente en `/logs/wardrive_XXXX.csv` en la SD.

### Formato del log (WigleWifi CSV)

Cada línea del CSV contiene:

```
MAC,SSID,AuthMode,FirstSeen,Channel,RSSI,CurrentLatitude,CurrentLongitude,AltitudeMeters,AccuracyMeters,Type
```

Ejemplo real:

```
FA:8F:CA:61:05:78,MiFibra-BB6F,[WPA2-PSK-CCMP][ESS],2026-10-11 12:34:56,6,-67,40.4168,-3.7038,650,10,WIFI
00:1A:2B:3C:4D:5E,Movistar_5G,[WPA2-PSK-CCMP][WPS][ESS],2026-10-11 12:35:01,44,-72,40.4170,-3.7040,650,12,WIFI
```

Campos principales:

| Campo | Descripción |
|---|---|
| `MAC` | BSSID del AP |
| `SSID` | Nombre de la red |
| `AuthMode` | Tipo de cifrado (WPA2, WPA3, WEP, Open) |
| `FirstSeen` | Timestamp del primer avistamiento |
| `Channel` | Canal WiFi |
| `RSSI` | Intensidad de señal (dBm) |
| `CurrentLatitude` | Latitud GPS |
| `CurrentLongitude` | Longitud GPS |
| `AltitudeMeters` | Altitud |
| `AccuracyMeters` | Precisión del fix |
| `Type` | `WIFI` o `BLE` |

---

## 📊 Qué genera

Un archivo **`.csv`** en la carpeta `/logs` de la SD:

```text
/logs/
├── wardrive_20261011_123456.csv
├── wardrive_20261011_134512.csv
└── wardrive_20261012_091234.csv
```

### Cómo usar ese log

**1. Subirlo a WiGLE**

- Ve a [wigle.net](https://wigle.net/).
- Crea una cuenta (gratis).
- **Upload → CSV** → sube el archivo.
- Contribuyes a la base de datos mundial de redes WiFi.

**2. Analizarlo con Wardrive Tracker**

- Abre tu instancia local de Wardrive Tracker.
- **Subir captura** → selecciona el CSV.
- Verás las redes en un mapa interactivo con filtros, panel de detalles y traza de avistamientos.

**3. Convertirlo a otros formatos**

```bash
# CSV a GPX (para Google Maps, Strava, etc.)
gpsbabel -i wigle -f wardrive.csv -o gpx -F wardrive.gpx

# CSV a KML (para Google Earth)
gpsbabel -i wigle -f wardrive.csv -o kml -F wardrive.kml
```

---

## 🎯 Diferencia con EAPOL/PMKID Scan

| Aspecto | Wardrive | EAPOL/PMKID Scan |
|---|---|---|
| **Objetivo** | Mapear redes (inventario) | Capturar handshakes (ataque) |
| **Interacción** | 100% pasiva | Pasiva (o forzada con deauth) |
| **GPS** | Requerido | Opcional |
| **Salida** | CSV (WigleWifi) | PCAP |
| **Uso** | WiGLE, mapas | Hashcat, aircrack-ng |
| **Legalidad** | Zona gris (mapear) | Delito si es red ajena |

**En la práctica:** puedes combinar ambos. El Marauder puede hacer Wardrive y EAPOL Scan simultáneamente si el firmware lo permite.

---

## ⚠️ Advertencias

- **Legalidad del wardriving:** registrar redes con GPS es legal en muchos países, pero en algunas jurisdicciones puede ser considerado invasión de privacidad. Infórmate de la legislación local.
- **No te conectes** a las redes que registres. El wardrive es 100% pasivo.
- **No ataques** las redes que registres. Eso ya no es wardriving, es delito.
- **GPS obligatorio:** sin módulo GPS y sin fix, el CSV tendrá coordenadas nulas o incorrectas.
- **Precisión:** la precisión del GPS depende de la visibilidad de satélites. En zonas urbanas densas puede ser de 10-20 metros.
- **Almacenamiento:** los CSV pueden crecer rápido. Cada red ocupa ~100 bytes. Un wardrive de 1 hora puede generar 1-5 MB.
- **Batería:** el GPS y el WiFi consumen mucho. Un wardrive largo agota la batería del Marauder en 2-3 horas.

---

## 🔗 Relacionado

- [EAPOL/PMKID Scan](eapol-pmkid.md) — para capturar handshakes mientras haces wardrive
- [Beacon Sniff](beacon.md) — para descubrir redes sin GPS
- [Scan AP/STA](scan-ap-sta.md) — para inventariar redes y clientes
- [GPS Info](../../gps/info/gps-info.md) — para verificar el fix antes de empezar
- [GPS Data Log](../../gps/captura/gps-data-log.md) — para registrar solo el recorrido
- [Wardrive Tracker](../../../07-wardrive.md) — para analizar el CSV en un mapa
- [WiGLE](https://wigle.net/) — base de datos mundial de redes WiFi
