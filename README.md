
# Proyecto de Machine Learning Supervisado  
## Análisis macroeconómico de países de la Unión Europea
### Integrantes 

### Pedro Rosales Pedrojose.rosales@cunef.edu 
### francisco coraul franciscoraul.abreu@cunef.edu

# Proyecto de Machine Learning Supervisado  

## Análisis macroeconómico de países de la Unión Europea

---

## 1. Introducción

El análisis del desempeño económico y fiscal de los países constituye un elemento central en el estudio de la macroeconomía aplicada. En particular, la relación entre los indicadores fiscales y el crecimiento económico ha sido objeto de un amplio debate en la literatura económica, tanto desde enfoques teóricos como empíricos.

En este proyecto se propone un enfoque basado en aprendizaje automático supervisado para analizar si la información macroeconómica y fiscal disponible en un período determinado puede aportar capacidad predictiva sobre el desempeño económico futuro de los países de la Unión Europea. A diferencia de enfoques puramente descriptivos, el objetivo es evaluar estas relaciones desde una perspectiva predictiva, utilizando técnicas estándar de Machine Learning aplicadas a datos tabulares.

El estudio se apoya en datos macroeconómicos armonizados procedentes de Eurostat, lo que permite trabajar con múltiples países bajo una estructura común y analizar patrones generales sin centrarse en casos individuales.

---

## 2. Objetivos del estudio

### Objetivo general

El objetivo central de este estudio es trascender el análisis fiscal tradicional centrado únicamente en el déficit. Mientras que la mayoría de los modelos económicos se enfocan en la relación deuda-PIB, esta investigación introduce el Patrimonio Neto del Sector Público (PSNW, por sus siglas en inglés) como el principal predictor de la salud económica. La hipótesis sostiene que el balance general total de un gobierno (activos menos pasivos) proporciona una señal más precisa de la estabilidad futura del PIB que el análisis de la deuda por sí sola.

### Objetivos específicos

- Formular un problema de regresión supervisada a partir de datos macroeconómicos comparables entre países.
- Analizar la estructura y características del dataset mediante un análisis exploratorio de datos (EDA).
- Evaluar la distribución, escalas y calidad de las variables numéricas disponibles.
- Identificar valores faltantes, outliers y posibles inconsistencias estructurales.
- Construir un dataset maestro consistente para el modelado supervisado.
- Entrenar y evaluar modelos predictivos bajo un marco metodológico reproducible.
- Documentar de forma explícita las decisiones técnicas y metodológicas adoptadas durante el proceso.

### Hipótesis de investigación

A partir del planteamiento teórico y empírico del estudio, se formulan las siguientes hipótesis:

**Hipótesis nula (H₀):**  
El Valor Neto del Sector Público (PSNW) no aporta información predictiva adicional sobre el crecimiento del PIB en comparación con la métrica tradicional de Deuda/PIB.

**Hipótesis alternativa (H₁):**  
El Valor Neto del Sector Público (PSNW) aporta mayor capacidad predictiva sobre el crecimiento del PIB que la métrica tradicional de Deuda/PIB, especialmente cuando se modela utilizando retardos temporales.


---

## 3. Marco metodológico

### 3.1 Planteamiento del problema y enfoque metodológico

El presente proyecto adopta un enfoque de aprendizaje automático supervisado, formulado como un problema de regresión sobre datos tabulares de tipo panel. El objetivo principal es evaluar la capacidad predictiva de indicadores macroeconómicos y fiscales observados en períodos anteriores sobre el crecimiento económico futuro de los países de la Unión Europea.

El análisis se realiza a partir de observaciones correspondientes a combinaciones país–período, permitiendo aplicar técnicas estándar de Machine Learning supervisado bajo un esquema temporal controlado.

---

### 3.2 Unidad de observación y estructura del dataset

La unidad de observación del estudio es un país de la Unión Europea en un período temporal determinado.

Cada observación se define como una combinación única *(país, período)* y se construye siguiendo un esquema basado en retardos temporales:

\[
(\text{País}, \text{Período } t-1) \rightarrow \text{Crecimiento del PIB en } t
\]

Este diseño garantiza el uso exclusivo de información pasada para la predicción, evitando contaminación temporal (*data leakage*).

---

### 3.3 Definición del problema de Machine Learning

#### Tipo de problema

- Aprendizaje supervisado  
- Regresión  

#### Variable objetivo (Target)

La variable objetivo es el crecimiento del Producto Interior Bruto (PIB) en el período \( t \), medido como tasa de crecimiento porcentual.

---

### 3.4 Variables explicativas

Las variables explicativas corresponden al período \( t-1 \) e incluyen seis indicadores macroeconómicos y fiscales principales:

- **Ratio Deuda pública / PIB (`debt_gdp`)**
- **Posición neta del sector público sobre PIB (`psnw_gdp`)**
- **Crecimiento del PIB (`gdp_growth`)**
- **Inflación (`inflation`)**
- **Holgura del mercado laboral (`labor_slack`)**
- **Indicadores financieros del sector público (`psnw`)**

Las variables se analizan inicialmente en su forma original durante el EDA, y son posteriormente utilizadas en el proceso de modelado.

---

### 3.5 Análisis Exploratorio de Datos (EDA)

El análisis exploratorio de datos se desarrolla en el notebook:

- `01_EDA.ipynb`

Esta fase permitió validar la estructura de los datasets, analizar distribuciones, escalas, valores faltantes y outliers, sin aplicar transformaciones definitivas ni entrenar modelos predictivos.

---

### 3.6 Construcción del dataset maestro

La integración y normalización estructural de los datos se realiza en el notebook:

- `02_Feature_Engineering.ipynb`

En esta etapa se construye un dataset maestro tipo panel, se unifican claves estructurales, se normalizan nombres de variables y se valida la integridad del conjunto final, sin aplicar imputaciones ni escalado.

---

### 3.7 Modelado y evaluación

El entrenamiento de modelos supervisados y la evaluación de su rendimiento se desarrollan en el notebook:

- `03_Modelado_y_Evaluacion.ipynb`

En esta fase se implementan:
- Estrategias de imputación aplicadas exclusivamente sobre el conjunto de entrenamiento.
- Escalado de variables cuando es requerido por los modelos.
- Entrenamiento de modelos baseline y modelos más avanzados.
- Evaluación del rendimiento mediante métricas estándar de regresión (RMSE, MAE y \(R^2\)).
- Comparación de modelos bajo un criterio cuantitativo homogéneo.

---

## 4. Fuente de datos

Los datos utilizados en este proyecto proceden de Eurostat, la oficina estadística de la Unión Europea.

- Indicadores macroeconómicos y fiscales oficiales.
- Datos armonizados y comparables entre países.
- Fuentes públicas y estandarizadas.

---

## 5. Resultados

## Resultados específicos y evidencia empírica

### Contexto institucional europeo y relevancia fiscal

La Unión Europea está sujeta al Pacto de Estabilidad y Crecimiento, que establece límites sobre el déficit y la deuda pública. Esto crea un entorno particularmente interesante para la investigación: dado que la mayoría de los países intentan mantener su ratio Deuda/PIB dentro de ciertos límites, la métrica tradicional de deuda pierde capacidad discriminatoria entre economías saludables y economías con dificultades.

Al introducir el **Valor Neto del Sector Público (PSNW)**, el análisis ofrece un criterio adicional que permite identificar qué países poseen activos sólidos a pesar de sus niveles de deuda, proporcionando una visión más sofisticada de la solvencia fiscal, especialmente relevante para la formulación de políticas de la Comisión Europea.

---

### Ventajas desde la perspectiva de ciencia de datos

Desde el punto de vista de la ciencia de datos, la elección de la Unión Europea proporciona un conjunto de datos equilibrado y de alta frecuencia.

El ciclo económico compartido de la UE ayuda al modelo **Random Forest** a identificar patrones temporalmente estables. Los conocimientos obtenidos a partir de un Estado miembro suelen ser aplicables a otros debido a sus características de mercado comunes, lo que incrementa la capacidad de generalización del modelo con retardo **T-1**.

---

### Preparación de los datos

El pipeline de preprocesamiento implementa una limpieza robusta de los datos, convirtiendo cadenas temporales trimestrales (por ejemplo, “2020Q1”) en objetos de fecha y agrupando los datos por entidad geográfica para preservar la integridad temporal.

---

### Construcción de escenarios con retardos temporales

Para garantizar que el modelo sea verdaderamente predictivo (y no simplemente correlacional en tiempo real), las variables explicativas se desplazaron temporalmente para crear tres escenarios distintos:

- **Modelo T-1**: Captura el impacto inmediato (trimestre anterior).
- **Modelo T-2**: Explora el efecto fiscal en el medio plazo (dos trimestres anteriores).
- **Modelo T-4**: Evalúa la resiliencia estructural a largo plazo (un año antes).

Este enfoque evita el *data leakage* y garantiza que el modelo utilice únicamente información pasada para predecir el crecimiento futuro.

---

### Modelos utilizados

Se evaluaron cuatro modelos distintos con el objetivo de identificar la especificación óptima:

- Regresión lineal múltiple *baseline*
- Modelo con retardo **T-1**
- Modelo con retardo **T-2**
- Modelo con retardo **T-4**

El uso del algoritmo **Random Forest** permite capturar relaciones no lineales. Por ejemplo, el impacto de la deuda sobre el PIB puede ser insignificante a niveles bajos, pero crítico al superar ciertos umbrales, fenómeno que los Random Forest están especialmente capacitados para detectar.

---

### Optimización del modelo

Se utilizó **GridSearchCV** para ajustar hiperparámetros como:

- Número de árboles (*n_estimators*)
- Profundidad máxima (*max_depth*)
- Tamaño mínimo de muestra por división (*min_samples_split*)

**Métrica optimizada:** Error Cuadrático Medio Negativo (*Negative MSE*).

**Hallazgo principal:** Se requirió un bosque más profundo para capturar la volatilidad de la ratio PSNW/PIB, lo que sugiere una alta complejidad en la relación entre el valor neto del sector público y la producción económica.

---

### Resultados del modelo

| Variante del modelo | R² | RMSE |
|---|---|---|
| T-1 (ajustado) | 0.6337 | 9.0852 |
| T-4 | 0.5308 | 9.4231 |
| T-2 | 0.5044 | 10.4057 |
| Baseline (media) | 0.2500 | 13.1469 |

El modelo **T-1** explica aproximadamente el **63% de la variabilidad del PIB**, lo cual representa un nivel elevado de precisión para datos macroeconómicos.

---

### Importancia de variables e interpretabilidad

#### Importancia por permutación

El análisis confirmó que el **PSNW** es el predictor más relevante, superando incluso a la deuda pública.

#### Valores SHAP

El análisis SHAP reveló una correlación positiva consistente: un mayor valor neto del sector público incrementa las predicciones de crecimiento del PIB.

Además, se identificó un **efecto de interacción**: el PSNW es más efectivo cuando la holgura del mercado laboral es baja, lo que sugiere que la fortaleza fiscal multiplica el impacto económico en contextos de pleno empleo.

### Evaluación de hipótesis

Los resultados empíricos obtenidos permiten **rechazar la hipótesis nula (H₀)**.

Los modelos que incorporan el Valor Neto del Sector Público (PSNW) como variable explicativa presentan un desempeño predictivo significativamente superior al modelo baseline y a las especificaciones basadas únicamente en la Deuda/PIB.

En particular, el modelo con retardo T-1 alcanza un valor de R² de aproximadamente 0.63, frente al desempeño notablemente inferior del modelo baseline, lo que indica que el PSNW contiene información relevante adicional para anticipar el crecimiento económico futuro.

Los resultados completos, así como las métricas cuantitativas asociadas, se documentan en el notebook `03_Modelado_y_Evaluacion.ipynb`.

---

## 6. Discusión

El análisis confirma la complejidad del fenómeno estudiado y la dificultad inherente a predecir el crecimiento económico a partir de indicadores macroeconómicos agregados. La heterogeneidad entre países y períodos, así como la presencia de valores faltantes estructurales, condiciona el rendimiento de los modelos.

No obstante, el enfoque supervisado permite identificar patrones relevantes y proporciona una base cuantitativa para el análisis económico comparado.

---

## 7. Conclusiones

### Conclusiones adicionales del análisis

- El Valor Neto del Sector Público (PSNW) se consolida como el predictor individual más relevante del crecimiento del PIB, superando a la deuda pública tradicional en términos de importancia explicativa.

- La superioridad del modelo con retardo T-1 sugiere que los efectos fiscales sobre la actividad económica se manifiestan principalmente en el corto plazo, siendo capturados de forma más eficiente por modelos con información temporal reciente.

- La utilización de algoritmos no lineales, como Random Forest, permite identificar relaciones complejas y umbrales en el impacto de las variables fiscales sobre el crecimiento económico, que no son capturadas por modelos lineales tradicionales.

- El análisis de interpretabilidad mediante importancia por permutación y valores SHAP confirma una relación positiva consistente entre el PSNW y el crecimiento del PIB.

- Se identifica un efecto de interacción relevante: el impacto positivo del PSNW sobre el crecimiento económico es más pronunciado en contextos de baja holgura del mercado laboral, lo que sugiere que la fortaleza fiscal amplifica su efecto en economías cercanas al pleno empleo.

---

## 8. Limitaciones

El estudio presenta varias limitaciones relevantes:

- La cobertura temporal y geográfica de algunas variables es desigual, lo que reduce el número efectivo de observaciones disponibles.
- La imputación de valores faltantes puede introducir sesgos, especialmente en contextos macroeconómicos heterogéneos.
- El uso de datos agregados a nivel país limita la capacidad de capturar dinámicas internas más finas.
- El rendimiento predictivo está condicionado por shocks económicos no observables y eventos excepcionales.

Estas limitaciones deben tenerse en cuenta al interpretar los resultados obtenidos.

---

### Estado final del documento

- README 
- Alineado con los notebooks:
  - `01_EDA.ipynb`
  - `02_Feature_Engineering.ipynb`
  - `03_Modelado_y_Evaluacion.ipynb`
- Publicación en GitHub
