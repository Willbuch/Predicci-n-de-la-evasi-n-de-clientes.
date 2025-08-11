# Proyecto: Análisis y Modelado Predictivo de Evasión de Clientes (Churn)

## Objetivo
El objetivo de este proyecto es desarrollar y evaluar modelos predictivos capaces de identificar a los clientes de la compañía de telecomunicaciones **TelecomX** que tienen una alta probabilidad de cancelar sus servicios. Al anticipar la evasión, la empresa puede implementar estrategias proactivas para retener a sus clientes, mejorando la lealtad y la rentabilidad.

## Metodología y Pasos del Análisis

### 1. Preprocesamiento de Datos
- **Limpieza:** Se cargó el archivo `EDA_Churn_TelecomX_Parte2.ipynb` y se eliminaron columnas que no aportan valor predictivo, como el identificador único de cliente (`ClienteID`).
- **Tratamiento de Nulos:** Se convirtieron los valores de la columna `TotalGasto` a un formato numérico y se eliminaron las filas con valores faltantes resultantes.
- **Codificación de Variables:** Las variables categóricas, como el tipo de contrato, el servicio de internet y el método de pago, se transformaron a un formato numérico utilizando `OneHotEncoder` para que fueran compatibles con los algoritmos de *machine learning*.

### 2. Análisis Exploratorio de Datos (EDA)
Se realizó un análisis para entender la estructura de los datos y las relaciones entre las variables:

- Se evaluó la proporción de clientes que cancelaron versus los que permanecieron, identificando un desbalance de clases que debe ser considerado en la evaluación de los modelos.
- Se visualizó la matriz de correlación para las variables numéricas, identificando relaciones potenciales entre ellas.
- Se utilizaron gráficos de *boxplot* para examinar la relación entre variables clave como `TiempoContrato` y `TotalGasto` con la evasión.

### 3. Modelado Predictivo
Se construyó un *pipeline* robusto para entrenar dos modelos predictivos, uno con normalización de datos y otro sin ella, para comparar su desempeño:

**Modelo 1: Regresión Logística**
- Este modelo es sensible a la escala de los datos, por lo que se aplicó una normalización (`StandardScaler`) a las variables numéricas.

**Modelo 2: Árbol de Decisión**
- Este modelo no se ve afectado por la escala de los datos, por lo que se entrenó sin normalización en las variables numéricas.

Se dividió el conjunto de datos en **80% para entrenamiento** y **20% para prueba** para una evaluación imparcial del rendimiento.

### 4. Evaluación de Modelos
Se evaluó el rendimiento de ambos modelos en el conjunto de prueba utilizando un conjunto de métricas clave:

- **Exactitud (Accuracy)**
- **Precisión (Precision)**
- **Recall**
- **Puntuación F1 (F1-score)**
- **Matriz de Confusión**

El modelo de Regresión Logística fue seleccionado como el de mejor desempeño general debido a su equilibrio entre *Precision* y *Recall*, lo que permite una clasificación más confiable de los clientes en riesgo.

### 5. Análisis de Importancia de Variables
Se analizaron las variables más influyentes en la predicción de la evasión para obtener *insights* de negocio:

- **Regresión Logística:** Los coeficientes mostraron que el tipo de contrato mensual y el servicio de internet de fibra óptica son los predictores más fuertes de evasión.
- **Árbol de Decisión:** La importancia de las variables confirmó que el tipo de contrato y el gasto total son los factores más relevantes para las decisiones del modelo.

## Conclusiones y Estrategias de Retención
El análisis identificó que el tipo de contrato mensual y el servicio de fibra óptica son los principales factores de riesgo para la evasión. Con base en estos hallazgos, se recomiendan las siguientes estrategias:

1. **Incentivar Contratos a Largo Plazo:** Crear ofertas especiales y beneficios para los clientes con contratos mensuales que opten por planes de 1 o 2 años.
2. **Mejorar el Servicio de Fibra Óptica:** Investigar las causas detrás de la alta evasión en este segmento (p.ej., calidad de servicio, soporte técnico) y tomar medidas correctivas.
3. **Monitoreo Proactivo:** Utilizar el modelo predictivo para identificar a los clientes con alta probabilidad de evasión y contactarlos de manera proactiva con ofertas personalizadas para su retención.

## Requisitos
El código de este proyecto se ejecutó utilizando las siguientes bibliotecas de Python:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
