# DISENO Y DESARROLLO DE SOFTWARE
Juan Carlos Almanza Guevara LISSE 5TO
#Simulador de ECU 

##INTRODUCCION,DESCRIPICION Y CARACTERISTICAS:

*   **Validación de Rangos Físicos:** El sistema comprueba que los valores de los sensores no sean absurdos (ej. voltajes negativos o porcentajes mayores a 100%).
*   **Comprobación de Coherencia:** Cuenta con lógica para detectar situaciones contradictorias. Por ejemplo, detecta si el acelerador está a más del 80% pero el motor registra menos de 500 RPM.
*   **Diagnóstico y Respuesta Automática:** Dependiendo de los datos de entrada, el sistema levanta "banderas" de advertencia (*warning*) o críticas (*critical*).
*   **Máquina de Estados Dinámica:** Transiciona automáticamente para proteger el motor.

## Estados del Sistema

1.  `INIT`: Inicialización básica del sistema.
2.  `SELF_TEST`: Autoprueba antes de arrancar.
3.  `OPERATIONAL`: Todos los parámetros están dentro de la normalidad.
4.  `DEGRADED`: Modo de advertencia. Se activa por temperatura ligeramente alta, RPM elevadas, voltaje bajo o inconsistencias entre sensores.
5.  `SAFE_STATE`: Modo de emergencia/crítico. Se activa inmediatamente ante temperatura crítica (>110°C), RPM excesivas (>7000) o voltaje peligrosamente bajo (<11.0V).
6.  `SHUTDOWN`: Apagado seguro del sistema.


##Sensores Monitorizados
*   **Velocidad:** 0 - 250 km/h
*   **RPM:** 0 - 8000 rpm
*   **Temperatura:** -40°C a 150°C
*   **Acelerador:** 0% a 100%
*   **Voltaje:** 9.0V a 16.0V
