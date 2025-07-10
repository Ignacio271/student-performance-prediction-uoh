# Proyecto Final - Predicción del Rendimiento Estudiantil (IIA-UOH)

**Final project for the Introduction to AI course (UOH)**  
La elección de este tema fue motivado por vivencias personales y de mi entorno. Este proyecto tiene como objetivo predecir si un estudiante aprobará o no su curso final para diseñar estrategias de apoyo al estudiante, utilizando técnicas de **clasificación supervisada** a partir de características académicas y sociodemográficas.

---

## Descripción del problema 📌

El rendimiento académico de los estudiantes está influenciado por múltiples factores: personales, familiares y escolares. Poder anticipar el riesgo de reprobación permite diseñar estrategias de apoyo temprano, reducir la deserción y mejorar el desempeño global del curso.

---

## 📊 Dataset y fuente (link de Kaggle)

El dataset fue extraído desde [Kaggle](https://www.kaggle.com/datasets/henryshan/student-performance-prediction) y contiene información de 395 estudiantes de educación secundaria. Algunas variables incluidas son:

- Sexo, edad, tipo de familia, educación de los padres
- Tiempo de estudio, consumo de alcohol, apoyo escolar, relaciones familiares
- Notas parciales: `G1`, `G2`
- Nota final: `G3`

La variable objetivo se definió como:

- `1` si `G3` (nota final) ≥ 10 → Aprobado  
- `0` si `G3` < 10 → Reprobado

---

## 🤖 Justificación del modelo

Se utilizó `RandomForestClassifier` por su capacidad para:

- Manejar datos mixtos (numéricos y categóricos)
- Capturar relaciones no lineales
- Ser robusto frente al sobreajuste
- Ofrecer interpretabilidad mediante la importancia de características

Como sabemos y hemos visto es una opción eficiente y versátil para problemas educativos con muchas variables como este.

---

## Metodología aplicada

1. **Análisis exploratorio**
Se realizó un análisis inicial para entender mejor los datos y sus características:
   - Correlación entre variables: Se utilizó df.corr() para calcular la matriz de correlación, junto con sns.heatmap() para visualizarla y detectar relaciones fuertes entre las variables.
   - Estadísticas generales: Se aplicaron funciones como df.describe() y df.info() para obtener un resumen de los datos, tipos de variables y posibles valores atípicos o faltantes.

2. **Preprocesamiento**
Se prepararon los datos para que pudieran ser utilizados por el modelo de clasificación:
   - Codificación de variables categóricas: Se usó pd.get_dummies() para convertir variables como “school”, “sex”, “guardian”, entre otras, en variables numéricas.
   - Normalización de variables numéricas: Se aplicó StandardScaler() de sklearn.preprocessing para escalar las variables numéricas a una misma escala.
   - Generación de la variable binaria objetivo (aprobado): Se creó una nueva columna donde 1 representa que el estudiante aprobó (nota final G3 ≥ 10) y 0 si reprobó.

3. **Selección de variables**
Para identificar las características con mayor valor predictivo:
   - Se entrenó un modelo RandomForestClassifier() de sklearn.ensemble sobre los datos preprocesados.
   - Se extrajeron las importancias de cada variable con el atributo feature_importances_.
   - Se visualizaron los resultados mediante sns.barplot(x=importances, y=feat_names) para detectar fácilmente qué variables eran más relevantes.
Las variables más importantes según este análisis fueron: G1, G2, absences, studytime y failures, lo que muestra que el desempeño previo y el compromiso académico son claves en la predicción del resultado final.

4. **Entrenamiento**
Con los datos ya procesados, se procedió a entrenar el modelo predictivo:
   - Modelo seleccionado: RandomForestClassifier por su capacidad de manejar relaciones no lineales y su robustez frente a variables irrelevantes.
   - División de datos: Se aplicó train_test_split() (de sklearn.model_selection) con un 80% para entrenamiento y 20% para prueba.
   - Métrica de evaluación principal: Se utilizó accuracy_score() para medir el desempeño general del modelo.

5. **Evaluación**
   - Se generó la matriz de confusión con confusion_matrix() y se visualizó usando ConfusionMatrixDisplay().
   - Se calculó el reporte de clasificación con classification_report() que entrega métricas como precisión, recall y F1-score para cada clase (aprobado/reprobado).

---

## 🧠 Resultados obtenidos

| Métrica     | Aprobados | Reprobados |
|-------------|-----------|------------|
| Precision   | 94%       | 83%        |
| Recall      | 90%       | 89%        |
| F1-Score    | 0.92      | 0.86       |
| Accuracy    | 0.90      | -          |


Las variables más relevantes fueron `G1`, `G2`, `absences`, `studytime` y `failures`.  
Esto indica que el desempeño previo y el compromiso académico tienen gran valor predictivo.

---

## 📌 Conclusiones

El modelo desarrollado logró predecir con alta precisión si un estudiante aprobará, permitiendo identificar tempranamente casos de riesgo académico. Las notas parciales (G1 y G2) destacaron como los indicadores más determinantes, lo que confirma que el desempeño previo es clave en el resultado final. Esta herramienta puede servir de apoyo para docentes y equipos educativos, facilitando intervenciones preventivas y focalizadas. A futuro, podría complementarse con modelos más complejos o datos longitudinales para reforzar su capacidad predictiva. En definitiva, este proyecto demuestra que la inteligencia artificial, aplicada de forma ética y responsable, puede ser una aliada poderosa en la toma de decisiones pedagógicas basadas en datos reales.

---

## 📂 Estructura del repositorio

La estructura de este repo es la siguiente:
```
📦 student-performance-prediction-uoh
├── mat2.csv                  # Dataset base
├── notebook_base.ipynb       # Notebook con análisis y modelo
├── environment.yml           # Dependencias del proyecto
└── README.md                 # Este documento
```

---

## 🛠️ Requisitos

Instalar las dependencias desde el archivo `environment.yml`:

```bash
conda env create -f environment.yml
conda activate student-perf
```

---

## 👥 Integrantes

- Ignacio Esteban Concha Pavez – Universidad de O’Higgins
