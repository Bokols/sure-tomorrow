### Descripción del Proyecto: **Regresión Lineal con Ofuscación de Datos**

#### **1. Introducción**
Este proyecto investiga el impacto de la ofuscación de datos en los modelos de regresión lineal. Específicamente, explora cómo la ofuscación de los datos utilizando una matriz aleatoria invertible afecta los coeficientes de regresión, los valores predichos y el rendimiento del modelo medido por métricas como RMSE (Error Cuadrático Medio) y R². La ofuscación de datos se utiliza a menudo para preservar la privacidad mientras se mantiene la utilidad del modelo, y este proyecto tiene como objetivo comprender si la ofuscación puede aplicarse sin comprometer significativamente la calidad de las predicciones de regresión.

El núcleo del análisis se basa en un conjunto de características, como la edad, el género, los ingresos y el tamaño de la familia, que predicen los beneficios del seguro. Las características se procesan y se entrena un modelo de regresión tanto en el conjunto de datos original como en el conjunto de datos ofuscado. Al comparar los valores predichos y las métricas de rendimiento, podemos evaluar la efectividad de la ofuscación para mantener la calidad de los modelos de regresión.

#### **2. Metodología**

##### **2.1 Datos y Generación de la Matriz**
Para comenzar, generamos una matriz cuadrada \( P \) a partir de una distribución uniforme de números aleatorios. Se verifica que esta matriz \( P \) sea invertible, ya que una matriz invertible es necesaria para una ofuscación efectiva. Luego, aplicamos esta matriz \( P \) para transformar el conjunto de características, creando una versión ofuscada del conjunto de datos. Los pasos involucrados son:

1. **Generación de la Matriz**: Se genera una matriz cuadrada de tamaño \( n \times n \) utilizando valores aleatorios.
2. **Comprobación de Invertibilidad de la Matriz**: Se verifica que la matriz \( P \) sea invertible. Si no lo es, se genera una nueva matriz hasta encontrar una que sea invertible.
3. **Ofuscación de los Datos**: La matriz de características original \( X \) se transforma multiplicándola por \( P \), produciendo un conjunto de características ofuscado \( X_{\text{ofuscado}} \).

##### **2.2 Modelo de Regresión Lineal**
Se implementa un modelo de regresión lineal utilizando tanto los datos originales como los datos ofuscados para predecir la variable objetivo (beneficios del seguro). La regresión se lleva a cabo utilizando una implementación personalizada de regresión lineal o una biblioteca conocida como `scikit-learn`. El modelo se entrena y prueba tanto con los datos originales como con los ofuscados, y se calculan las métricas de rendimiento, incluidos RMSE y R².

##### **2.3 Evaluación del Rendimiento**
El rendimiento de los modelos de regresión se evalúa comparando los valores predichos de la variable objetivo con los valores reales. Las dos métricas clave para la evaluación son:

- **RMSE (Error Cuadrático Medio)**: Mide la magnitud promedio de los errores entre los valores predichos y los valores reales.
- **R² (Coeficiente de Determinación)**: Indica la proporción de varianza de la variable objetivo que es predecible a partir de las características.

El propósito de esta evaluación es determinar si la ofuscación de los datos afecta la capacidad del modelo para predecir la variable objetivo.

#### **3. Resultados**

##### **3.1 Coeficientes del Modelo**
Al entrenar el modelo de regresión utilizando tanto los datos originales como los ofuscados, encontramos que los coeficientes de regresión obtenidos de los datos ofuscados están relacionados con los coeficientes originales a través de la inversa de la matriz de ofuscación \( P \). Esta relación se mantiene porque tanto los modelos originales como los ofuscados minimizan la misma función de error, lo que lleva a predicciones similares.

##### **3.2 Valores Predichos**
Los valores predichos tanto para los datos originales como para los ofuscados resultaron idénticos. Esto es esperado, ya que la matriz de ofuscación \( P \) preserva la estructura de los datos de manera que las predicciones no cambian. Esto demuestra que la transformación utilizando \( P \) no altera significativamente las predicciones del modelo de regresión.

##### **3.3 Métricas RMSE y R²**
El modelo fue evaluado tanto en los datos originales como en los datos ofuscados, y se obtuvieron los siguientes resultados para ambos:

- **RMSE**: 0.34
- **R²**: 0.66

Estos valores fueron idénticos para los datos originales y los ofuscados, lo que indica que la ofuscación no degradó la calidad del modelo de regresión en términos de precisión de las predicciones y poder explicativo.

#### **4. Discusión de los Resultados**

##### **4.1 Impacto de la Ofuscación de Datos**
Los resultados demuestran que la ofuscación del conjunto de datos utilizando una matriz invertible no afecta significativamente el rendimiento del modelo de regresión. Tanto los valores de RMSE como de R² se mantuvieron constantes para los datos originales y los ofuscados, lo que sugiere que el proceso de ofuscación preserva las relaciones dentro de los datos que son cruciales para hacer predicciones precisas.

##### **4.2 Implicaciones Teóricas**
El fundamento teórico detrás de este resultado es que la transformación de las características por la matriz \( P \) es un proceso reversible, y los coeficientes en el modelo de regresión permanecen sin cambios en el conjunto de datos ofuscado. Esto preserva la integridad del poder predictivo del modelo.

##### **4.3 Consideraciones Prácticas**
En aplicaciones del mundo real, la ofuscación de datos puede ser utilizada como una técnica de preservación de la privacidad sin comprometer la utilidad del modelo. Por ejemplo, si se involucran datos sensibles, ofuscar las características antes de entrenar un modelo podría permitir que las empresas sigan extrayendo información útil mientras minimizan los riesgos de privacidad.

#### **5. Conclusión**

Este proyecto demostró con éxito que la regresión lineal puede operar eficazmente con ofuscación de datos. Al utilizar una matriz invertible aleatoria para ofuscar los datos, no se observó una diferencia significativa en el rendimiento del modelo de regresión, como lo evidencian los valores idénticos de RMSE y R². Esto sugiere que la ofuscación, cuando se realiza correctamente, no obstaculiza el poder predictivo de los modelos de regresión. Por lo tanto, este enfoque podría ser útil en aplicaciones sensibles a la privacidad donde se requiere preservar la privacidad de los datos sin sacrificar la precisión del modelo.

Trabajos futuros podrían explorar otros tipos de transformaciones y métodos de ofuscación, así como la aplicación de modelos más complejos para evaluar su comportamiento bajo condiciones similares de preservación de la privacidad.
