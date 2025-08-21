# Calibración y configuración de los controladores ODESC

ODESC V4.2 (Firmware 0.5.6) 

### Referencias
https://docs.odriverobotics.com/v/0.5.6/getting-started.html

https://docs.odriverobotics.com/v/0.6.9/guides/getting-started.html

## Calibración de la ODESC
Ejecute las siguientes instrucciones en orden para una correcta calibración 

### 1. Configuración de la batería 

> Información de la Bateria [Lipo 4S, 14.8V 5000 mA, 25C] 

#### 1.1. Límites de voltaje (bat_n_cells = 4)
```
odrv0.config.dc_bus_undervoltage_trip_level = 3.3 * 4
```
```
odrv0.config.dc_bus_overvoltage_trip_level = 4.25 * 4
```
#### 1.2. Límites de corriente

1.2.1. Corriente de descarga máxima de la bateria [5A*25C = 125]
```
odrv0.config.dc_max_positive_current = 125
```

1.2.1. Corriente de carga máxima de la bateria [-5*1 = -5]
```
odrv0.config.dc_max_negative_current = -5 
```

### 2. Configuración del motor

2.1. Tipo de motor [MotorType.HIGH_CURRENT = 0]
```
odrv0.axis0.motor.config.motor_type = 0
```
2.2. Número de electroimanes
```
odrv0.axis0.motor.config.pole_pairs = 15
```

2.3. Constante de torque [8.27/Kv]
```
odrv0.axis0.motor.config.torque_constant = 8.27/39 
```

2.4. Corriente de calibración para el motor 
```
odrv0.axis0.motor.config.calibration_current = 3
```

2.5. Voltaje máximo permitido durante la calibración
```
odrv0.axis0.motor.config.resistance_calib_max_voltage = 4 
```

2.6. Corriente de bloqueo para la calibración del encoder
```
odrv0.axis0.config.calibration_lockin.current = 0.12
```

2.7. Calibración del motor [axisState.MOTOR_CALIBRATION = 4]
> [!IMPORTANT]
> Al ejecutar el siguiente comando, el motor debe emitir un silbido
```
odrv0.axis0.requested_state = 4 
```

2.8. Guardar la configuración establecida
```
odrv0.save_configuration() 
```

### 3. Configuración de los límites del motor 

3.1. Limite de corriente (A)
```
odrv0.axis0.motor.config.current_lim = 5
```

3.2. Limite de velocidad (vueltas/s)
```
odrv0.axis0.controller.config.vel_limit = 7
```

### 4. Configuración del encoder del motor

4.1. Tipo de encoder
```
odrv0.axis0.encoder.config.mode = ENCODER_MODE_HALL
```

4.2. Pulsos por revolución
```
odrv0.axis0.encoder.config.cpr = 90
```
4.3. Ancho de banda (reducido para motores hoverboard)
```
odrv0.axis0.encoder.config.bandwidth = 100 
```
4.4. Offset de calibración (aumentada debido a la baja resolución)
```
odrv0.axis0.encoder.config.calib_scan_distance = 150
```

4.5. Ejecutar el siguiente comando hasta que el CPR = 1
```
odrv0.axis0.encoder.count_in_cpr 
```

4.6. Primera secuencia de calibración del encoder
> [!IMPORTANT]
> Al ejecutar el comando, el motor deberá girar en levógiro 
```
odrv0.axis0.requested_state = AXIS_STATE_FULL_CALIBRATION_SEQUENCE
```

4.7. Guardar la configuración establecida
```
odrv0.save_configuration() 
```

4.8. Resetear el ODESC
```
odrv0.reboot()
```

4.9. Ejecutar el siguiente comando hasta que el CPR = 0
```
odrv0.axis0.encoder.count_in_cpr 
```

4.10. Segunda secuencia de calibración del encoder
> [!IMPORTANT]
> Al ejecutar el comando, el motor deberá girar en levógiro y dextrógiro 
```
odrv0.axis0.requested_state = AXIS_STATE_FULL_CALIBRATION_SEQUENCE
```

4.11. Activar el control en lazo cerrado
```
odrv0.axis0.config.startup_closed_loop_control = True
```

4.12. Activar la calibración del motor
> [!IMPORTANT]
> Al ejecutar el siguiente comando, el motor debe emitir un silbido
```
odrv0.axis0.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```

4.13. Guardar la configuración de precalibración del motor
```
odrv0.axis0.motor.config.pre_calibrated = True
```

4.14. Offset de calibración del encoder
> [!IMPORTANT]
> Al ejecutar el comando, el motor deberá girar en levógiro y dextrógiro 
```
odrv0.axis0.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```

4.15. Guardar la configuración de precalibración del encoder
```
odrv0.axis0.encoder.config.pre_calibrated = True
```

4.16. Habilitar el control en lazo cerrado
```
odrv0.axis0.requested_state = AXIS_STATE_CLOSED_LOOP_CONTROL
```

4.17. Guardar la configuración establecida
```
odrv0.save_configuration() 
```

4.18. Resetear el ODESC
```
odrv0.reboot()
```




