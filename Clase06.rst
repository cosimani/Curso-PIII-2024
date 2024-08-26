.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 06 - PIII 2024
====================
(Fecha: 26 de agosto)


NRZ (Non-Return-to-Zero)
------------------------

- NRZ es un tipo de codificación digital utilizado para transmitir datos binarios en telecomunicaciones y sistemas digitales. 
- Los bits de datos se representan por dos niveles de voltaje sin retornar a cero.


NRZ-L (Non-Return-to-Zero-Level)
--------------------------------

- Representa un bit '1' con un nivel de voltaje y un bit '0' con otro nivel de voltaje.


NRZ-I (Non-Return-to-Zero-Inverted)
-----------------------------------

- Un cambio en el nivel de voltaje representa un '1' y la ausencia de un cambio indica un '0'. 


Simulación de transmisión Ethernet usando NRZ
---------------------------------------------

.. code-block:: python

	# Codificación NRZ para simular transmisión de Ethernet

	def string_to_bin(message):
	    """
	    Convierte un mensaje de texto en una secuencia binaria.
	    Cada carácter se convierte en su representación binaria de 8 bits.
	    """
	    return ''.join(format(ord(char), '08b') for char in message)

	def nrz_encoding(binary_data):
	    """
	    Codifica la secuencia binaria usando NRZ.
	    NRZ: 1 se representa como un nivel alto, 0 como un nivel bajo.
	    """
	    encoded_signal = []
	    for bit in binary_data:
	        if bit == '1':
	            encoded_signal.append(1)  # Nivel alto
	        else:
	            encoded_signal.append(0)  # Nivel bajo
	    return encoded_signal

	def transmit_signal(signal):
	    """
	    Simula la transmisión del señal codificado.
	    En una transmisión real, esto se enviaría a través de un cable o una fibra óptica.
	    Aquí simplemente mostramos el "nivel" de la señal.
	    """
	    for level in signal:
	        print(level, end=' ')
	    print()

	# Mensaje para transmitir
	message = "Hola"

	# Paso 1: Convertir el mensaje en binario
	binary_data = string_to_bin(message)
	print(f"Mensaje original: {message}")
	print(f"Mensaje en binario: {binary_data}")

	# Paso 2: Codificar el mensaje binario usando NRZ
	nrz_signal = nrz_encoding(binary_data)
	print("Señal codificada (NRZ):")
	transmit_signal(nrz_signal)



Ejercicio:
==========

- Transmitir una señal codificada con un filtro sinc de caída cosenoidal controlando el roll-off.
- El objetivo es reducir la interferencia inter símbolos (ISI) y aprovechar el ancho de banda.
- Cree una interfaz gráfica para preparar el mensaje y mostrar las gráficas.


Ejercicio:
==========

- Ahora deseamos transmitir este mensaje pero con 4 niveles con PAM4.
- ¿Cómo lo realizamos?


Transmisión de Datos en 1000BASE-T (Gigabit Ethernet)
=====================================================

- Esquema de Transmisión: En 1000BASE-T, se utilizan todos los cuatro pares de hilos en el cable UTP. La señalización se realiza a través de una técnica llamada codificación de línea de 4D-PAM5 (Pulse Amplitude Modulation con 5 niveles de amplitud), que permite transmitir datos a 1 Gbps usando una señalización de amplitud de pulsos.

- El 4D (Cuatro Dimensiones) se refiere a la utilización de cuatro pares de cables en un cable Ethernet de categoría 5e o superior. Cada par de cables transmite datos en una dimensión separada.


Simulación de codificación y decodificación 4D-PAM5
---------------------------------------------------

.. code-block:: python

	import numpy as np
	import matplotlib.pyplot as plt

	# Define los niveles de amplitud para 4D-PAM5
	PAM5_LEVELS = np.array([-2, -1, 0, 1, 2])

	def encode_pam5(bitstream):
	    """
	    Codifica un bitstream en una secuencia de símbolos PAM5.
	    El bitstream debe ser una secuencia de 1s y 0s.
	    """
	    # Mapeo simple: 2 bits → 1 símbolo PAM5
	    if len(bitstream) % 2 != 0:
	        raise ValueError("El bitstream debe tener una longitud par.")
	    
	    pam5_symbols = []
	    for i in range(0, len(bitstream), 2):
	        # Toma dos bits y mapea a un nivel PAM5
	        bits = bitstream[i:i+2]
	        symbol_index = int(''.join(map(str, bits)), 2)  # Convertir bits a número
	        pam5_symbols.append(PAM5_LEVELS[symbol_index])
	    
	    return np.array(pam5_symbols)

	def decode_pam5(pam5_symbols):
	    """
	    Decodifica una secuencia de símbolos PAM5 en un bitstream.
	    """
	    # Asumimos que PAM5_LEVELS tiene los valores [-2, -1, 0, 1, 2]
	    bitstream = []
	    for symbol in pam5_symbols:
	        # Encuentra el índice del símbolo en PAM5_LEVELS
	        symbol_index = np.where(PAM5_LEVELS == symbol)[0][0]
	        # Convierte el índice a 2 bits
	        bitstream.extend(map(int, np.binary_repr(symbol_index, width=2)))
	    
	    return np.array(bitstream)

	original_bitstream = np.array([1, 0, 1, 1, 0, 0, 1, 0])  # Bitstream de ejemplo
	encoded_symbols = encode_pam5(original_bitstream)
	decoded_bitstream = decode_pam5(encoded_symbols)

	# Resultados
	print("Bitstream original:", original_bitstream)
	print("Símbolos PAM5 codificados:", encoded_symbols)
	print("Bitstream decodificado:", decoded_bitstream)

	# Grafica de los símbolos PAM5
	plt.stem(encoded_symbols, use_line_collection=True)
	plt.title("Símbolos PAM5 Codificados")
	plt.xlabel("Índice")
	plt.ylabel("Amplitud")
	plt.grid(True)
	plt.show()



Ejercicio:
==========

- Este es un ejercicio de investigación, desarrollo y discusión en clase.
- Simular la transmisión de un mensaje de una computadora a otra. Elija un protocolo para esto.
- Considerar los protocolos en la pila TCP/IP.
- Sobre Gigabit Ethernet con UTP con 4D-PAM5
- Usar el filtro sinc de caída consenoidal.
- ¿Cómo simularía cada etapa?
- Grafique e imprima datos para comprender lo que sucede en cada etapa.




