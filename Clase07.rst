.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 07 - PIII 2024
====================
(Fecha: 27 de agosto)


Tonos de Shepard
================

- Acústica, psicoacústica, y procesamiento de señales. 
- Los Tonos de Shepard son una serie de tonos puros que, cuando se reproducen en secuencia, crean la ilusión auditiva de un tono que sube o baja infinitamente en altura, a pesar de que en realidad no ocurre un cambio real en la frecuencia.
- Los Tonos de Shepard consisten en varios tonos sinusoidales espaciados por octavas. Al variar la amplitud de estos tonos de forma que los extremos (frecuencias más bajas y más altas) se atenúan, se crea una ilusión de un tono que parece subir o bajar infinitamente.
- Psicoacústica: La percepción de los Tonos de Shepard explota una característica de nuestro sistema auditivo: la capacidad de identificar tonos en diferentes rangos de frecuencia, pero sin una clara distinción cuando los tonos están compuestos de múltiples frecuencias.


.. code-block:: python

	import numpy as np
	import matplotlib.pyplot as plt
	from IPython.display import Audio

	def generate_shepard_tone(base_freq, num_tones, duration, sample_rate):
	    t = np.linspace(0, duration, int(sample_rate * duration), endpoint=False)
	    tone = np.zeros_like(t)

	    for i in range(num_tones):
	        freq = base_freq * (2 ** i)
	        amplitude = np.sin(np.pi * i / num_tones) ** 2
	        tone += amplitude * np.sin(2 * np.pi * freq * t)

	    return tone

	# Parámetros
	base_freq = 440  # Frecuencia base en Hz (Nota La)
	num_tones = 6    # Número de tonos superpuestos
	duration = 0.5   # Duración de cada tono en segundos
	sample_rate = 44100  # Tasa de muestreo

	# Generar el tono de Shepard
	shepard_tone = generate_shepard_tone(base_freq, num_tones, duration, sample_rate)

	# Reproducir el tono generado
	Audio(shepard_tone, rate=sample_rate)

	def generate_shepard_scale(base_freq, num_tones, duration, sample_rate, steps):
	    scale = []
	    for step in range(steps):
	        tone = generate_shepard_tone(base_freq * (2 ** (step / steps)), num_tones, duration, sample_rate)
	        scale.append(tone)
	    return np.concatenate(scale)

	# Parámetros adicionales
	steps = 100  # Número de pasos en la escala (equivalente a una octava)

	# Generar la escala de Shepard
	shepard_scale = generate_shepard_scale(base_freq, num_tones, duration, sample_rate, steps)

	# Reproducir la escala
	Audio(shepard_scale, rate=sample_rate)



Ejercicio
=========

- Modificar parámetros como num_tones, base_freq, y steps para observar cómo cambia la percepción.
- ¿Qué ocurre si cambia la tasa de muestreo o la duración de cada tono?
- Implementar una versión que genera una escala descendente.



Pulsación
=========

- La pulsación, o "beats", es un fenómeno acústico que ocurre cuando dos tonos de frecuencias diferentes se reproducen simultáneamente. 
- Se manifiesta como una oscilación en la amplitud de la onda resultante, que se percibe como un sonido que fluctúa en volumen.


.. code-block:: python

	import numpy as np
	import matplotlib.pyplot as plt
	from IPython.display import Audio

	def generate_beats(freq1, freq2, duration, sample_rate):
	    t = np.linspace(0, duration, int(sample_rate * duration), endpoint=False)
	    signal1 = np.cos(2 * np.pi * freq1 * t)
	    signal2 = np.cos(2 * np.pi * freq2 * t)
	    beats = signal1 + signal2
	    return t, beats

	# Parámetros
	freq1 = 440  # Frecuencia del primer tono en Hz (Nota La)
	freq2 = 442  # Frecuencia del segundo tono en Hz
	duration = 5.0  # Duración de la señal en segundos
	sample_rate = 44100  # Tasa de muestreo

	# Generar la señal de beats
	t, beats_signal = generate_beats(freq1, freq2, duration, sample_rate)

	# Visualizar la señal de beats
	plt.plot(t[:1000], beats_signal[:1000])  # Visualización de un pequeño fragmento de la señal
	plt.title('Señal de Beats')
	plt.xlabel('Tiempo [s]')
	plt.ylabel('Amplitud')
	plt.show()

	# Reproducir la señal de beats
	Audio(beats_signal, rate=sample_rate)




Ejercicio
=========

- ¿Cuál es la fórmula para calcular la frecuencia de oscilación?
- ¿Cómo se perciben las pulsaciones cuando las frecuencias están muy cerca en comparación a cuando están más alejadas?


Entrega Nº 1
=============

Objetivo
--------
Esta es la primera de las tres entregas evaluativas de la materia. En esta entrega, se evaluarán los temas relacionados con Gigabit Ethernet y la pila de protocolos, así como la implementación práctica y la documentación de los resultados.

Temas a cubrir
--------------
1. **Gigabit Ethernet**
2. **Pila de Protocolos**: Estructura y funcionamiento.
3. **Mensajería**: Implementación de un protocolo, como STOMP
4. **Convolución con Filtro Transmisor**: Aplicación y análisis.
5. **Diagrama Ojo**: Interpretación y análisis.
6. **Simulaciones**: Implementación y análisis de simulaciones.
7. **Organización de código fuente**
8. **Interfaz Gráfica de Usuario**: Diseño y usabilidad.

Requisitos
-----------
- Todos los temas deben integrarse en una única entrega.
- El trabajo debe ser presentado de manera colaborativa. Los cuatro estudiantes deben acordar cómo presentar los temas de forma coherente y organizada.
- La presentación debe incluir:
  - Simulación relevante al tema.
  - Repositorio GitHub de cada estudiante, que debe contener el código fuente y documentación correspondiente.
  - Diapositivas de presentación que resuman y expliquen los temas.
  - Un informe colaborativo único que integre el trabajo de los cuatro estudiantes.

Evaluación
----------
- La entrega será evaluada con un **8** si cubre todos los temas correctamente con los conceptos vistos en clase.
- Ampliar la exploración de los temas y realizar aportes adicionales puede elevar la calificación a un **9** o **10**.

Fecha de Presentación
----------------------
La entrega debe ser presentada el **10 de septiembre**.

Instrucciones adicionales
--------------------------
- Asegúrense de coordinarse bien entre los miembros del equipo para evitar solapamientos y asegurar que cada tema esté cubierto de manera adecuada.
- La calidad del informe y la organización del repositorio GitHub serán factores importantes en la evaluación.







