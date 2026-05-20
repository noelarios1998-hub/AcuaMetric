<div align="center">
  <h1>PROYECTO: ACUAMETRIC</h1>
  <p><i>Estimación de peso de peces en ecosistemas LTRM</i></p>
</div>

---
<div align="center">
  <img src="Logo_CUGDL_1.png" alt="Logo CU Guadalajara" width="796" height="256">
  <h1>📊 PROYECTO: ACUAMETRIC</h1>
  <p><i>Estimación de peso de peces en ecosistemas LTRM</i></p>
</div>

 **Carrera**  Licenciatura en IA y Ciencia de Datos  
 
 **Equipo**  Noe Larios, Carlos Linares, Christian Herrera, Arturo Rosas  
 
 **Semestre**  2026 A 

---

## [DESCARGAR DATASET CSV AQUÍ](https://github.com/noelarios1998-hub/AcuaMetric/releases/download/base_de_datos/ltrm_fish_data.csv)

---

## Descripción del Proyecto

AcuaMetric es un proyecto académico enfocado en el desarrollo de un modelo avanzado para la estimación de la biomasa en ecosistemas acuáticos. Utilizando técnicas de aprendizaje automático (Machine Learning), el sistema predice el peso de los especímenes a partir de variables morfológicas y condiciones ambientales. Este proyecto está directamente relacionado y sirve como base complementaria para el sistema de monitoreo de fauna denominado BioTracker.

El objetivo principal es optimizar los procesos de investigación biológica, proporcionando una herramienta analítica computacional que elimine la necesidad de manipulación física excesiva de las especies, agilizando la toma de datos y reduciendo los costos operativos de los programas de conservación.

## Introducción y Problemática

El monitoreo de poblaciones de peces es fundamental para evaluar la salud de los ecosistemas acuáticos. Históricamente, el programa de Monitoreo de Recursos a Largo Plazo (LTRM, por sus siglas en inglés) en los Estados Unidos ha recopilado vastas cantidades de información. Sin embargo, el proceso tradicional de pesaje manual de cada espécimen presenta severas limitaciones:

1. Estrés y Daño Biológico: La captura, manipulación y pesaje fuera del agua genera altos niveles de estrés en los peces, alterando sus hábitos e incluso incrementando las tasas de mortalidad post-monitoreo.
2. Consumo de Recursos: Requiere una inversión significativa de tiempo, personal calificado y equipo especializado en el trabajo de campo.
3. Lentitud Operativa: El registro físico ralentiza las expediciones científicas, limitando el volumen de datos que pueden recolectarse eficientemente.

AcuaMetric aborda esta problemática mediante el modelado predictivo, estableciendo una relación matemática robusta entre el peso del pez y variables alternativas no invasivas (como longitudes y parámetros físico-químicos del agua), transformando un proceso lento y disruptivo en un flujo de estimación ágil y automatizado.

## Metodología y Gestión de Base de Datos

### Origen y Estructura de los Datos
La base de datos original se obtuvo de la plataforma Kaggle, provista por el programa LTRM. El archivo fuente en formato CSV constaba originalmente de:
* Registros totales: Más de 166,000 filas.
* Atributos: 86 columnas con datos morfológicos, taxonómicos y ambientales.

Acorde a los requerimientos de la materia de Base de Datos, se realizó una descripción detallada de la estructura lógica del conjunto de datos, analizando la entidad principal (pez), su clave primaria (código de identificación único) y las relaciones con variables secundarias y ambientales. Aunque inicialmente se contempló el despliegue de un servidor con FastAPI para interconectar los datos aplicando conceptos de la materia de Redes, el entregable final se enfocó estrictamente en el procesamiento, depuración y estructuración relacional del archivo plano por indicaciones de la cátedra.

### Depuración y Variables Seleccionadas
Para garantizar la calidad del modelado, se filtró el conjunto de datos para el periodo comprendido entre los años 2015 y 2025. Tras la eliminación exhaustiva de registros nulos, el dataset final consolidó un total de 92,222 registros limpios.

Las variables clave seleccionadas para el análisis relacional y predictivo fueron:
* Código de identificación del pez (Llave Primaria/ID).
* Longitud total del pez.
* Longitud estándar del pez.
* Temperatura del agua.
* Profundidad del cuerpo de agua en el punto de captura.
* Conductividad eléctrica del agua.
* Oxígeno disuelto.
* Transparencia y turbidez del agua.
* Peso del pez (Variable objetivo / Target).

### Preprocesamiento y Estandarización
Para homogeneizar las escalas de las variables numéricas y procesar variables categóricas de manera uniforme entre los distintos algoritmos evaluados, se aplicaron dos técnicas esenciales:
1. StandardScaler: Utilizado para la estandarización de características numéricas, centrando los datos con media cero y varianza unitaria.
2. OneHotEncoder: Aplicado para la codificación de variables categóricas, permitiendo su correcta interpretación matemática por parte de los modelos.

## Análisis Estadístico

Siguiendo el diseño experimental de la materia de Probabilidad y Estadística II, se implementaron tres pruebas estadísticas fundamentales para validar las hipótesis del proyecto:

### 1. Prueba T de Student para Muestras Independientes
* Objetivo: Evaluar si el tamaño (longitud) de la especie influye de manera estadísticamente significativa en el peso final del ejemplar.
* Resultados: Se obtuvo un valor estadístico de 17.66, empleando un nivel de significancia (alfa) de 0.05 y un intervalo de confianza del 95%. Al superar holgadamente el valor crítico, se rechazó la hipótesis nula, confirmando la fuerte dependencia del peso respecto a las dimensiones longitudinales.

### 2. Prueba T de Student para Muestras Pareadas
* Objetivo: Evaluar la diferencia sistemática entre la longitud total y la longitud estándar de los especímenes.
* Resultados: La prueba reveló una diferencia estadísticamente significativa, lo que permitió fundamentar los criterios morfológicos de las especies de acuerdo con las condiciones específicas de las distintas zonas geográficas de muestreo.

### 3. Análisis de Varianza (ANOVA)
* Objetivo: Comparar los promedios de peso entre diferentes especies y entornos para determinar el impacto de la variabilidad ambiental.
* Resultados: Se calculó un estadístico F de 311.92. Este valor justifica sólidamente la inclusión de múltiples covariables ambientales en el modelo predictivo, demostrando que los factores externos alteran significativamente la distribución del peso biológico.

## Modelado y Aprendizaje Automático

En el marco de la asignatura de Machine Learning, se implementó y evaluó un amplio espectro de algoritmos de regresión para identificar la solución óptima:
* Regresión Lineal Múltiple
* Regresión Polinomial
* Regresión Lasso
* Máquinas de Soporte Vectorial (SVM)
* K-Vecinos Más Cercanos (KNN)
* Random Forest Regressor (Bosques Aleatorios)

### Rendimiento del Modelo Seleccionado
El algoritmo Random Forest Regressor demostró el rendimiento más competitivo y robusto, destacando por las siguientes métricas de evaluación:
* R Cuadrado (R2) en Entrenamiento: 0.9866
* R Cuadrado (R2) en Validación: 0.9715
* Error Absoluto Medio (MAE): 61.42

La estrecha cercanía entre el R2 de entrenamiento y validación confirmó experimentalmente que el modelo no presenta problemas de sobreajuste (overfitting), garantizando una excelente capacidad de generalización ante datos nuevos no observados.

## Fundamentos Matemáticos

El modelo Random Forest funciona como un predictor de ensamble (Ensemble Learning) basado en la combinación de múltiples árboles de decisión individuales. Matemáticamente, la predicción final para una tarea de regresión corresponde al promedio de las predicciones de todos los árboles del bosque:

Dado un conjunto de árboles T_1, T_2, ..., T_B, la estimación del peso (Y) a partir del vector de características (X) se define como:

Y = (1 / B) * sumatoria desde b=1 hasta B de T_b(X)

### Ventajas Teóricas en AcuaMetric:
1. Resiliencia ante Valores Atípicos (Outliers): Al basarse en submuestreo de datos y características (bagging), los valores extremos ambientales o morfológicos se aíslan en ramas o árboles específicos, evitando distorsionar la estructura global del predictor.
2. Captura de Relaciones No Lineales: El modelo construye fronteras de decisión ortogonales que se adaptan naturalmente a las interacciones complejas y multivariadas del entorno acuático, prescindiendo de la necesidad de transformaciones matemáticas previas en los datos de entrada.

En el desarrollo no se forzaron hiperparámetros fijos para la profundidad máxima o las divisiones de nodos, permitiendo que el algoritmo determinara de forma adaptativa los cortes óptimos basados en la reducción de la varianza (función de costo de error cuadrático medio).

## Complejidad Computacional y Optimización

El análisis del código bajo la perspectiva de la materia de Complejidad Computacional requirió el uso de herramientas de perfilado de bajo nivel debido a la naturaleza semi-orientada a objetos de los estimadores de Scikit-Learn. Se utilizó la librería estándar `tracemalloc` para auditar rigurosamente el uso de memoria RAM y los tiempos de CPU en un entorno de ejecución real con los 92,222 registros.

### Análisis Big O e Intervención con Inteligencia Artificial
El comportamiento empírico del algoritmo demostró una complejidad temporal y espacial de tipo lineal O(N), confirmando su alta escalabilidad para entornos de Big Data. No obstante, el modelo base preestablecido consumía recursos de manera ineficiente. Con el soporte de herramientas de IA, se diseñó una estrategia de optimización hiperparamétrica para reestructurar las limitaciones de ejecución del algoritmo.

Se limitó el bosque a un máximo de 40 árboles, se restringió la cantidad de hojas y nodos por árbol mediante el uso de la raíz cuadrada para la selección de características (`max_features='sqrt'`), y se habilitó la paralelización multinúcleo del procesador (`n_jobs=-1`).

### Comparativa de Rendimiento (Dataset Completo: 92,222 registros)

| Métrica de Rendimiento | Modelo Base | Modelo Optimizado | Impacto / Resultado |
| --- | --- | --- | --- |
| **Tiempo de Ejecución** | 0.59 segundos | 0.059 segundos | Reducción de tiempo ~10 veces más rápido |
| **Consumo de Memoria** | 13.52 MB | 17.04 MB | Incremento marginal de ~3.52 MB |
| **Complejidad Asintótica** | O(N) Lineal | O(N) Lineal | Mantiene la estabilidad de escala |

La optimización basada en la complejidad computacional demostró que sacrificar una cantidad ínfima de memoria RAM (aproximadamente 4 MB) a cambio de una aceleración de procesamiento de un orden de magnitud (10x) representa un balance sumamente rentable. Esto permite construir un software ecológico, computacionalmente responsable y apto para dispositivos con recursos limitados en estaciones biológicas de campo.

## Conclusión

El desarrollo de AcuaMetric integra exitosamente las competencias de diversas disciplinas de la Ciencia de Datos para resolver un problema ecológico real. Al mitigar el impacto biológico en la fauna mediante la sustitución del pesaje tradicional por un algoritmo de Random Forest altamente optimizado, se demuestra que la inteligencia artificial puede aplicarse bajo principios de sostenibilidad y eficiencia algorítmica. El proyecto cumple con rigor los estándares académicos exigidos, demostrando solidez estadística, precisión matemática y un diseño computacional óptimo.
