.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 09 - PIII 2024
====================
(Fecha: 3 de septiembre)


.. figure:: images/ejemplo_conexion_micro.png

.. code-block::

	void detectarIntT1() org 0x001a  {
	    LATBbits.LATB0 = !LATBbits.LATB0;
	    IFS0bits.T1IF = 0;  // Borramos la bandera de interrupción T1
	}

	void main()  {
	    TRISBbits.TRISB0 = 0;
	    LATBbits.LATB0 = 0;

	    // Modo de operación Timer1
	    T1CON = 0x0000;

	    // Modo operación Timer1: reloj interno, escala 1:1, empieza cuenta en 0
	    TMR1 = 0;

	    // Cuenta 500 ciclos
	    PR1 = 500;

	    // Interrupciones Timer1, borra Bandera de interrupción
	    IFS0bits.T1IF = 0;

	    // Habilita interrupción
	    IEC0bits.T1IE = 1;

	    // Arranca Timer1
	    T1CONbits.TON = 1;

	    while( 1 )
	       asm nop;
	}


Ejercicio:
==========

- Escribir un programa para un dsPIC (indique cuál elige) que encienda un led a 3 segundos y otro a 11 segundos.



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




