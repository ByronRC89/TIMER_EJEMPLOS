# TIMER_EJEMPLOS

Este código se configura y utiliza varios temporizadores en un microcontrolador STM32L053 para realizar operaciones de encendido y apagado de varios pines GPIO conectados a un led. A continuación, se explica cada parte del código en detalle:
![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/5476f6e7-4ed2-4a57-aaea-4f024c8a3b06)

Se declaran las funciones que configurarán los temporizadores 2, 6 y 21.
![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/9d6438cc-6297-4905-adef-c6df0a3e6539)

Configuración del Sistema de Reloj
HSI (High-Speed Internal Clock): Se habilita y selecciona el HSI de 16 MHz como fuente de reloj del sistema.
GPIO Clock: Se habilitan los relojes para los puertos GPIOA, GPIOB y GPIOC.
SYSCFG Clock: Se habilita el reloj para el sistema de configuración.
Configuración de los GPIO
PC8: Configurado como salida, inicialmente apagado.
PC6 y PC5: Configurados como salidas.
PC13: Configurado como entrada.

evaluacion donde se encuentran los timer 2, 6, 21.

![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/ca286e15-6205-43f6-9df2-1df2098fc376)

buscamos sus configuraciones en el manual de referencia en los temas siguintes 
![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/07e6784d-545c-499f-9f21-13acd046f743)

esto se utiliza para poder encontrar los registros que deben ser habilitados para poder encender y poner en funcionamiento cada timer a cada tasa de propagacion segun sea la necesidad.
por ejemplo: la configuracion del TIM2, con un valor de ARR estimado para 1 segundo a 16 bits con una frecuencia de 16Mhz
![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/68a51485-0d98-46f5-bbbd-d1875d36f4d7)

Timer 2: Si el flag de actualización está activado, se limpia el flag, se realiza un toggle en el pin PC8 y se resetea.
Timer 6: Si el flag de actualización está activado, se limpia el flag, se realiza un toggle en el pin PC6 y se resetea.
Timer 21: Si el flag de actualización está activado, se limpia el flag, se realiza un toggle en el pin PC5 y se resetea.

a continuacion se muestra la logica de los cilos ```if()``` , los cuales tienen las condicones de encendido y apagado 
![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/80290b37-e094-4bbc-8080-cd67a384f180)

a continuacion un video con una descripcion breve del funcionamiento, codigo y los registros.

https://youtu.be/WNBuC7DbV2o ![image](https://github.com/ByronRC89/TIMER_EJEMPLOS/assets/159856194/f4b71041-2b19-4eba-8926-4ef222294a10)

