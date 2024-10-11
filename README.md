**Introducción:**

Este proyecto se basa en un conjunto de datos del archivo 2023_accidents_causa_conductor_gu_bcn_.csv que contiene registros de accidentes de tráfico de Barcelona. Las principales variables que se ha seleccionado son el nombre del distrito, barrio, fecha, código postal, las causas y las coordenadas de los accidentes.
El objetivo es analizar las tendencias de los accidentes y predecir el número de accidentes mensuales: 


*   Predecir el distrito donde podría ocurrir el accidente, utilizando variables geográficas y temporales.
*   Predecir el número de accidentes por mes con un modelo de regresión lineal.


**Depuración de datos:**

Para la normalización de los datos se aplicaron las siguientes técnicas:

*   Se ha hecho correción de formato, por ejemplo las columnas como año, mes y día se ha unificado para obtener la columna "data" y así facilitar el análisis temporal y la predicción.

*   Se ha categorizado las columnas día de la semana, causa del accidente y nombre del mes para optimizar el rendimiento de los análisis.

*   Se ha utilizado expresión regular en la columna "Num_postal", para que el registro quede sólo números y no haya caracteres en medio. Además se ha creado una función para esta columna ya que el código postal tiene 8 dígitos, y si hay registros con menos dígitos o NaN, estos registros se convierten en -1.

**Resultados:**

A través del análisis de datos geográficos y gráfico de barra, se pudo identificar que los distritos, como el Eixample y Sant Martí, presentan un mayor número de accidentes. Además, los días laborables, principalmente los lunes y viernes, registran más accidentes, a causa de la falta de atención al volante.

En cuanto a los resultados de los tres modelos:


*   Predicción del número de accidentes por mes:
<br>Utiliza el modelo de regresión lineal, y se predijo el número de accidentes por mes basado en la tendencia temporal. Los resultados fueron:
<br>**Mean Squared Error (MSE):** 7289.43
<br>**R² Score:** -1.36
<br>El modelo muestra un enorme error, esto significa que el número de accidentes no sigue una tendencia simple lineal. Se ha imprimido un gráfico en donde nos muestra los datos reales,los puntos azules, que son los datos observados del número de accidentes por mes, y los puntos rojos son los valores predichos por el modelo.


*   Predicción del distrito dependiendo de las causas del accidente:
<br>Se implementa dos modelos: Random Forest y SVM(Support Vector Machine) para predecir el distrito donde podría ocurrir un accidente basándose en datos geográficos y temporales. Los resultados fueron lo siguiente:
En el modelo Random Forest se obtuvo una presición del 100% en todos los distritos, aunque a primera vista muestra un rendimiento alto con buenos resultados, esto podría significar una posibilidad de sobreajuste (overfitting) al obtener resultados perfectos, en el futuro podría dar problemas si se añade nuevos datos al modelo ya que podría predecir mal.
En el caso del modelo SVM, la exactitud fue de 89.5%, muestra un rendimiento fuerte aunque no perfecto como el anterior modelo. Pero muestra un mejor equilibrio entre precisión y recall que el modelo Random Forest, sin llegar a ser un sobreajuste. Entonces el modelo SVM podría mejorar su rendimiento con un ajuste de hiperparámetros.

**Conclusiones:**

Tras revisar los análisis se ha concluido que:

El análisis de los datos de accidentes en Barcelona muestra que los accidentes no están distribuidos aleatoriamente, sino que ciertos distritos y días presentan un mayor riesgo. Las áreas con mayor tráfico, como Eixample, y los días con mayor actividad laboral, como los lunes, presentan más incidentes a causa de la falta de atención al volante.

El modelo de predicción de número de accidentes por mes, utilizando regresión lineal, no fue el adecuado debido a la complejidad de los datos. Significa que se podría utilizar un modelo más complejo para capturar mejor las variaciones en el tiempo.

Y el modelo Random Forest fue claramente "superior" para predecir el distrito de ocurrencia de un accidente, con una precisión perfecta pero se puede mejorar aún más la precisión y robustez de las predicciones con un ajuste de los hiperparámetros del modelo.
