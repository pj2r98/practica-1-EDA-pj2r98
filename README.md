# Proyecto de Machine Learning Supervisado  
## Análisis macroeconómico de países de la Unión Europea

---

## 1. Introducción

El análisis del desempeño económico y fiscal de los países constituye un elemento central en el estudio de la macroeconomía aplicada. En particular, la relación entre los indicadores fiscales y el crecimiento económico ha sido objeto de un amplio debate en la literatura económica, tanto desde enfoques teóricos como empíricos.

En este proyecto se propone un enfoque basado en **aprendizaje automático supervisado** para analizar si la información macroeconómica y fiscal disponible en un período determinado puede aportar capacidad predictiva sobre el desempeño económico futuro de los países de la Unión Europea. A diferencia de enfoques puramente descriptivos, el objetivo es evaluar estas relaciones desde una perspectiva predictiva, utilizando técnicas estándar de Machine Learning aplicadas a datos tabulares.

El estudio se apoya en datos macroeconómicos anuales armonizados, lo que permite trabajar con múltiples países bajo una estructura común y analizar patrones generales sin centrarse en casos individuales.

---

## 2. Objetivos del estudio

### Objetivo general

Evaluar la capacidad predictiva de indicadores macroeconómicos y fiscales para anticipar el crecimiento económico futuro de los países de la Unión Europea mediante modelos de aprendizaje automático supervisado.

### Objetivos específicos

- Formular un problema de regresión supervisada a partir de datos macroeconómicos comparables entre países.
- Analizar la estructura y características del dataset mediante un análisis exploratorio de datos (EDA).
- Aplicar técnicas de ingeniería y selección de variables orientadas al modelado predictivo.
- Entrenar y comparar distintos modelos de Machine Learning supervisado.
- Evaluar el rendimiento de los modelos utilizando métricas estándar de regresión.
- Analizar la relevancia de las variables explicativas mediante técnicas de interpretabilidad.
- Extraer conclusiones sobre el alcance y las limitaciones del enfoque aplicado.

---

## 3. Marco metodológico

### 3.1 Planteamiento del problema y enfoque metodológico

El presente proyecto adopta un enfoque de **aprendizaje automático supervisado**, formulado como un problema de **regresión** sobre datos tabulares de tipo panel. El objetivo principal es evaluar la capacidad predictiva de indicadores macroeconómicos y fiscales pasados sobre el desempeño económico futuro de los países de la Unión Europea.

El análisis se realiza a partir de observaciones independientes correspondientes a combinaciones país–año, lo que permite disponer de un número suficiente de datapoints y aplicar técnicas estándar de Machine Learning supervisado.

---

### 3.2 Unidad de observación y estructura del dataset

La unidad de observación es un país de la Unión Europea en un año determinado.

Cada observación se construye utilizando información del período anterior como variables explicativas y una variable objetivo correspondiente al período actual, siguiendo el esquema:

(País, Año t−1) → Variable objetivo en Año t

Este diseño garantiza que el modelo únicamente utiliza información disponible con anterioridad al valor que se desea predecir.

---

### 3.3 Definición del problema de Machine Learning

#### Tipo de problema

- Aprendizaje supervisado  
- Regresión  

#### Variable objetivo (Target)

La variable objetivo del modelo es el **crecimiento del PIB en el año t**, medido como porcentaje respecto a un año base. Esta variable se utiliza como proxy del desempeño económico, permitiendo evaluar si la información macroeconómica y fiscal previa contiene poder predictivo relevante.

---

### 3.4 Variables explicativas y selección de variables (Feature Engineering)

Las variables explicativas corresponden al período t−1 e incluyen indicadores macroeconómicos y fiscales ampliamente utilizados en el análisis económico:

- Producto Interior Bruto (PIB)  
- Valor Neto del Sector Público (NETW)  
- Ratio NETW / PIB  
- Deuda pública  
- Ratio Deuda / PIB  
- Inflación  
- Holgura del mercado laboral (Slack)  

Durante la fase de ingeniería de variables se aplican transformaciones orientadas al modelado supervisado, incluyendo normalización, tratamiento de valores faltantes, selección de variables relevantes y análisis de multicolinealidad.

---

### 3.5 Análisis Exploratorio de Datos (EDA)

Previamente al entrenamiento de los modelos, se realiza un análisis exploratorio de datos con los siguientes o

---

## 4. Fuente de datos

Los datos utilizados en este proyecto proceden de **Eurostat**, la oficina estadística de la Unión Europea. Se emplean indicadores macroeconómicos y fiscales anuales armonizados a nivel país, lo que garantiza la comparabilidad entre las distintas economías analizadas.

El conjunto de datos incluye información correspondiente a varios países de la Unión Europea y abarca un período temporal reciente, suficiente para aplicar técnicas de aprendizaje automático supervisado bajo un enfoque de datos tabulares comparables.

Los datos han sido obtenidos a partir de fuentes oficiales públicas y presentan un alto grado de estandarización, lo que los hace adecuados para su uso en análisis exploratorio y modelado predictivo.

---

## 5. Resultados

Esta sección se completará tras la ejecución de los notebooks correspondientes al análisis exploratorio, la construcción de variables y el entrenamiento de los modelos de Machine Learning.  
En ella se presentarán los resultados obtenidos a partir de las métricas de evaluación y la comparación entre modelos.

---

## 6. Discusión

La discusión de los resultados se desarrollará una vez finalizado el proceso de modelado.  
Esta sección permitirá analizar e interpretar los resultados obtenidos, así como contrastarlos con los objetivos planteados en el estudio.

---

## 7. Conclusiones

Las conclusiones finales del proyecto se elaborarán tras la obtención de los resultados empíricos.  
En esta sección se sintetizarán los principales hallazgos del estudio y se evaluará el cumplimiento de los objetivos establecidos.

---

## 8. Limitaciones y líneas futuras

Las limitaciones del estudio y las posibles líneas futuras de investigación se actualizarán al finalizar el análisis, teniendo en cuenta los resultados obtenidos y las restricciones observadas durante el desarrollo del proyecto.



