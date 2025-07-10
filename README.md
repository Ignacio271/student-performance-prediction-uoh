# Proyecto Final - Predicción del Rendimiento Estudiantil

**Final project for the Introduction to AI course (UOH)**  
Este proyecto tiene como objetivo predecir si un estudiante aprobará o no su curso final, utilizando técnicas de **clasificación supervisada** a partir de características académicas y sociodemográficas.

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

## 🧪 Metodología aplicada

1. **Análisis exploratorio**  
   - Correlación entre variables
   - Estadísticas generales

2. **Preprocesamiento**
   - Codificación de variables categóricas
   - Normalización de variables numéricas
   - Generación de variable binaria (`aprobado`)

3. **Selección de variables**
   - Se analizaron las características más relevantes con `feature_importances_` del modelo

4. **Entrenamiento**
   - Modelo: `RandomForestClassifier`
   - División `train/test`: 80% / 20%
   - Métrica principal: Accuracy

5. **Evaluación**
   - Matriz de confusión
   - Precisión, recall y F1-score

---

## 🧠 Resultados obtenidos

- **F1-score**:
  - Aprobados: 0.92
  - Reprobados: 0.86
- **Accuracy**: 0.90  
- **Precision**:
  - Aprobados: 94%
  - Reprobados: 83%
- **Recall**:
  - Aprobados: 90%
  - Reprobados: 89%

Las variables más relevantes fueron `G1`, `G2`, `absences`, `studytime` y `failures`.  
Esto indica que el desempeño previo y el compromiso académico tienen gran valor predictivo.

---

## 📌 Conclusiones

Con esto ya tenemos nuestras conclusiones que son:
1. El modelo predice con alta precisión si un estudiante aprobará, lo cual puede ayudar a detectar casos de riesgo.
2. Las notas parciales (G1 y G2) son los indicadores más importantes para anticipar el resultado final.
3. Este tipo de modelos podría ser útil como herramienta de apoyo para docentes, orientadores o equipos directivos, facilitando intervenciones preventivas.
4. A futuro, podrían complementarse con modelos más complejos o con datos longitudinales para reforzar la capacidad predictiva.


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
