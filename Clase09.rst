.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 09 - PIII 2024
====================
(Fecha: 3 de septiembre)



Ejercicio: Generador de tono variable con dsPIC y DAC R2R
=========================================================

Configurar un dsPIC para leer un voltaje analógico a través de un ADC, y utilizar esa lectura para generar una señal de frecuencia variable. La señal será producida en 10 pines digitales conectados a un DAC R2R, que convertirá la señal digital en una salida analógica.

Descripción
-----------

1. **Configuración del ADC:**

   - Configura un canal del ADC para leer un voltaje aplicado a un pin analógico del dsPIC. El rango de voltaje es de 1 a 3V.

   - Configura el ADC para que funcione en modo de conversión continua y para que convierta el voltaje con una resolución de 12 bits.

2. **Configuración de los pines digitales:**

   - Configura 10 pines digitales del dsPIC como salidas. Estos pines se conectarán a un DAC R2R construido con resistencias.

   - El DAC R2R debe estar diseñado para convertir la señal digital de 10 bits en una señal analógica.

3. **Generación de la señal de frecuencia variable:**

   - Usa la lectura del ADC para ajustar la frecuencia de un tono. La señal debe ser generada en función de la lectura del ADC y salida a través de los 10 pines digitales configurados.

   - La frecuencia del tono debe variar en función del voltaje medido por el ADC, con un rango de frecuencia entre 100 Hz y 1 kHz.

4. **Salida a DAC R2R:**

   - Conecta los 10 pines digitales al DAC R2R, que estará armado con resistencias para convertir la señal digital en una señal analógica.
   
   - La salida analógica del DAC R2R debe ser observable con un osciloscopio.




