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

bat_n_cells = 4
```
odrv0.config.dc_bus_undervoltage_trip_level = 3.3 * 4
```
```
odrv0.config.dc_bus_overvoltage_trip_level = 4.25 * 4
```
#### Límites de corriente

Corriente de descarga máxima de la bateria [5A*25C = 125]
```
odrv0.config.dc_max_positive_current = 125
```

Corriente de carga máxima de la bateria [-5*1 = -5]
```
odrv0.config.dc_max_negative_current = -5 
```

### Configuración del motor

Tipo de motor [MotorType.HIGH_CURRENT = 0]
```
odrv0.axis0.motor.config.motor_type = 0
```
Número de electroimanes
```
odrv0.axis0.motor.config.pole_pairs = 15
```

Constante de torque [8.27/Kv]
```
odrv0.axis0.motor.config.torque_constant = 8.27/39 
```
```

```



