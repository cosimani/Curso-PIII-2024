.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 15 - PIII 2024
====================
(Fecha: 28 de octubre)


Trabajo práctico 3: Monitoreo de condiciones en una finca de café usando IoT y predicción con IA
------------------------------------------------------------------------------------------------

Aplicar tecnologías IoT y técnicas de inteligencia artificial para monitorear y predecir condiciones ambientales en un cultivo de café, usando una arquitectura completa de recopilación, almacenamiento y análisis de datos.

**Objetivos:**

- Comprender la aplicación de IoT en la agricultura y su impacto en la toma de decisiones.
- Implementar una conexión de datos en MySQL para almacenar y consultar datos recolectados de los sensores.
- Utilizar herramientas de visualización y análisis de datos para generar reportes y realizar predicciones.

**Actividades:**

- Presentación del flujo de datos: Sensores → TTN → Servidor → MySQL.
- Conexión a la base de datos MySQL y consulta de los datos históricos.
- Visualización de los datos (temperatura y humedad ambiente y del suelo).
- Investigar sobre Grafana y preparar un dashboard.
- Investigar sobre las opciones de TTN.
- Definir y entrenar una arquitectura de red neuronal MLP para realizar predicciones sobre lo que sucede en la finca.
- Realizar una predicción con una serie temporal para analizar el comportamiento cíclico de los sensores.

**Por estudiante:**

API en PHP para la base de datos:

- Crear una API en PHP que permita realizar consultas específicas a la base de datos MySQL.
- Asegurarse de que la API pueda retornar datos históricos y actuales, listos para ser visualizados en el dashboard.

Dashboard en Grafana:

- Configurar un dashboard en Grafana utilizando los datos de la API.
- Incluir visualizaciones que permitan analizar tendencias y detectar patrones inusuales en las condiciones de la finca.

Red Neuronal MLP en Weka:

- Usar Weka para entrenar un modelo de red neuronal MLP que prediga valores futuros de humedad o temperatura en base a los datos históricos.
- Documentar los resultados de predicción y analizar la precisión del modelo en la predicción de eventos.

Predicción de serie temporal en Python:

- Crear una serie temporal en Python usando librerías como statsmodels o Prophet para predecir el comportamiento de los sensores en el corto y mediano plazo.
- Visualizar las predicciones en comparación con los datos reales en el tiempo y discutir las tendencias observadas.


**Para todos:**

- Exploración y discusión grupal: Usos del IoT en telecomunicaciones





