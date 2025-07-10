# student-performance-prediction-uoh
Final project for the Introduction to AI course (UOH). A supervised learning model predicts student pass/fail outcomes based on academic and socio-demographic features.


# Proyecto Final - Predicción del Rendimiento Estudiantil 📚

Este proyecto de Introducción a la Inteligencia Artificial tiene como objetivo predecir si un estudiante aprobará o no su curso final, utilizando técnicas de clasificación supervisada.

## 📌 Descripción del problema

El rendimiento académico de los estudiantes es influenciado por múltiples factores personales, familiares y escolares. Poder predecir de forma temprana si un estudiante aprobará permite tomar decisiones para prevenir la deserción y mejorar el apoyo educativo.

## 📊 Dataset

El dataset utilizado proviene de [Kaggle](https://www.kaggle.com/datasets/henryshan/student-performance-prediction) y contiene información de estudiantes como:

- Sexo, edad, educación de los padres
- Tiempo de estudio, actividades extracurriculares, consumo de alcohol
- Notas parciales y finales (G1, G2, G3)

La variable objetivo es binaria:
- `1` si G3 (nota final) ≥ 10 → Aprobado
- `0` si G3 < 10 → Reprobado

## 🔍 Metodología

1. **Análisis exploratorio**: Se visualizan correlaciones y estadísticas generales.
2. **Preprocesamiento**:
   - Codificación de variables categóricas
   - Normalización de variables numéricas
3. **Feature selection**: Se visualiza la importancia de las variables.
4. **Modelo**: Se utiliza `RandomForestClassifier`.
5. **Evaluación**:
   - Accuracy
   - Matriz de confusión
   - Precisión, recall y F1-score

## 🧠 Resultados

El modelo logró una precisión adecuada para el problema educativo, destacando factores como el tiempo de estudio, faltas a clases y desempeño previo como claves para la predicción.

## 📂 Estructura del repositorio

```
📦 Proyecto_Rendimiento_Estudiantil
├── mat2.csv
├── notebook_base.ipynb
├── README.md
└── environment.yml
```

## 🛠️ Requisitos

Para correr el notebook se requiere instalar las dependencias desde `environment.yml`.

## 👥 Integrantes

- Ignacio Esteban Concha Pavez (UOH)

