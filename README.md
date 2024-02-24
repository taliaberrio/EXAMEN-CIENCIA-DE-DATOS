# EXAMEN-CIENCIA-DE-DATOS
EXAMEN CIENCIA DE DATOS
OBJETIVO: Desarrollar el análisis y modelado sobre un dataset de empleados de una empresa. Este dataset incluye información sobre la educación, año de incorporación, ciudad de trabajo, categoría salarial, edad, género, si han sido asignados temporalmente a la banca (EverBenched), experiencia en el dominio actual y si el empleado tomó tiempo libre (LeaveOrNot). El dataset ha sido modificado para incluir datos faltantes, añadiendo realismo al desafío analítico.
Este código lleva a cabo un análisis completo de datos y modelado utilizando un conjunto de datos de empleados. Aquí está el desglose de cada parte:
1.	Importación de bibliotecas: Importa las bibliotecas necesarias para el análisis de datos y modelado, incluyendo Pandas para la manipulación de datos, NumPy para operaciones numéricas, Matplotlib para visualización y RandomForestClassifier para la construcción de modelos de clasificación.
2.	Carga de datos: Carga el conjunto de datos desde un archivo CSV en un DataFrame de Pandas llamado datos.
3.	Verificación de valores faltantes: Utiliza el método isnull().sum() para verificar si existen valores faltantes en el DataFrame y muestra la suma de valores faltantes por cada columna.
4.	Preprocesamiento de datos:
•	Convierte la columna 'LeaveOrNot' en etiquetas categóricas ('Not Leave' y 'Leave').
•	Elimina las filas que tienen valores faltantes en las columnas 'ExperienceInCurrentDomain' y 'JoiningYear'.
•	Imputa los valores faltantes en las columnas 'Age' y 'PaymentTier' utilizando la media y la moda respectivamente.
•	Calcula los cuantiles y filtra los registros atípicos utilizando el rango intercuartílico (IQR).
5.	Análisis Exploratorio de Datos (EDA):
•	Grafica la distribución de los sexos con un gráfico de torta.
•	Grafica la distribución de niveles de estudio con un gráfico de barras y un gráfico de torta.
•	Crea un histograma para analizar la propensión de los jóvenes a tomar licencias.
•	Grafica la distribución de clases ('Leave' y 'Not Leave') con un gráfico de torta.
6.	Preparación de datos para el modelado:
•	Define las características (X) y la variable objetivo (y) del modelo.
•	Convierte las variables categóricas en variables dummy utilizando pd.get_dummies().
7.	División de datos:
•	Divide el conjunto de datos en conjuntos de entrenamiento y prueba utilizando train_test_split().
8.	Entrenamiento de modelos:
•	Entrena dos modelos RandomForestClassifier: uno sin balanceo de clases y otro con balanceo de clases.
9.	Cálculo de métricas de desempeño:
•	Define una función calculate_metrics() para calcular métricas de desempeño como la precisión (accuracy) y el puntaje F1 para ambos modelos.
•	Calcula la matriz de confusión para ambos modelos.
10.	Visualización de resultados:
•	Grafica la matriz de confusión para ambos modelos utilizando ConfusionMatrixDisplay.
En resumen, este código realiza una exploración completa de los datos, prepara los datos para el modelado, entrena modelos de clasificación y evalúa su desempeño utilizando métricas y visualizaciones.
SALIDA


Este fragmento de código muestra la salida de la función isnull().sum() aplicada al DataFrame datos. Esta función cuenta la cantidad de valores faltantes (NaN) en cada columna del DataFrame. La salida indica el número de valores faltantes para cada columna:
•	Education: Tiene 0 valores faltantes.
•	JoiningYear: Tiene 36 valores faltantes.
•	City: Tiene 0 valores faltantes.
•	PaymentTier: Tiene 42 valores faltantes.
•	Age: Tiene 27 valores faltantes.
•	Gender: Tiene 0 valores faltantes.
•	EverBenched: Tiene 0 valores faltantes.
•	ExperienceInCurrentDomain: Tiene 30 valores faltantes.
•	LeaveOrNot: Tiene 0 valores faltantes.
Estos resultados son útiles para identificar qué columnas tienen valores faltantes en el conjunto de datos. En este caso, las columnas JoiningYear, PaymentTier, Age y ExperienceInCurrentDomain tienen valores faltantes, y se aplican diferentes estrategias para manejar estos valores faltantes durante la limpieza y preparación de datos, como la eliminación de filas con valores faltantes o la imputación de valores utilizando la media o la moda.


Estas métricas y la matriz de confusión proporcionan una evaluación del desempeño de los modelos de Random Forest tanto sin balanceo como con balanceo de clases.
Random Forest sin balanceo:
•	Accuracy (precisión): En el conjunto de entrenamiento es del 92.51% y en el conjunto de prueba es del 84.53%. Esto indica la proporción de predicciones correctas realizadas por el modelo.
•	F1 Score: En el conjunto de entrenamiento es de 0.9224 y en el conjunto de prueba es de 0.8359. El F1 Score es una métrica que combina precisión y exhaustividad, útil cuando hay un desbalance de clases en los datos.
•	Confusion Matrix (Matriz de Confusión): Esta matriz muestra la cantidad de verdaderos positivos, verdaderos negativos, falsos positivos y falsos negativos del modelo en el conjunto de prueba. En este caso, tenemos 108 verdaderos positivos (predicciones de "Leave" que son correctas), 471 verdaderos negativos (predicciones de "Not Leave" que son correctas), 81 falsos positivos (predicciones de "Leave" que son incorrectas) y 25 falsos negativos (predicciones de "Not Leave" que son incorrectas).
Random Forest con balanceo:
•	Accuracy (precisión): En el conjunto de entrenamiento es del 91.71% y en el conjunto de prueba es del 83.36%.
•	F1 Score: En el conjunto de entrenamiento es de 0.9169 y en el conjunto de prueba es de 0.8299.
•	Confusion Matrix (Matriz de Confusión): Muestra 120 verdaderos positivos, 451 verdaderos negativos, 69 falsos positivos y 45 falsos negativos.
Comparación:
•	El modelo sin balanceo muestra una precisión ligeramente más alta en ambos conjuntos (entrenamiento y prueba) en comparación con el modelo con balanceo.
•	Sin embargo, el modelo con balanceo tiende a tener una puntuación F1 más alta, lo que sugiere un mejor equilibrio entre precisión y exhaustividad, especialmente en el conjunto de prueba.
•	En la matriz de confusión, observamos que ambos modelos tienen un número similar de verdaderos positivos y verdaderos negativos, pero el modelo con balanceo tiende a tener menos falsos negativos a costa de más falsos positivos en comparación con el modelo sin balanceo.
En resumen, ambos modelos tienen un buen desempeño en términos de precisión y F1 Score, pero el modelo con balanceo podría ser preferible si se desea minimizar la cantidad de falsos negativos, es decir, si es crucial detectar correctamente los casos de "Leave".
