# Calibracion y configuracion de los controladores ODESC

ODESC V4.2 (Firmware 0.5.6) 

### Referencias
https://docs.odriverobotics.com/v/0.5.6/getting-started.html
https://docs.odriverobotics.com/v/0.6.9/guides/getting-started.html

## Calibración de la ODESC
Ejecute las siguientes instrucciones en orden para una correcta calibración 

### Configuración de la batería 

Información de la Bateria [Lipo 4S, 14.8V 5000 mA, 25C] 

#### Límites de voltaje

```
odrv0.config.dc_bus_undervoltage_trip_level = 3.3 * 4
```
```
odrv0.config.dc_bus_overvoltage_trip_level = 4.25 * 4
```
Límites de corriente

```

```




```

```



