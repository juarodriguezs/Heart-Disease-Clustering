# 🩺 Heart Disease Clustering (K-means)

Este proyecto aplica técnicas de **aprendizaje no supervisado** para identificar grupos de pacientes con características similares dentro de una base de datos de personas diagnosticadas con enfermedades cardíacas. El objetivo es explorar cómo el **clustering con K-means** puede ayudar a los profesionales de la salud a descubrir patrones relevantes que podrían apoyar la toma de decisiones clínicas.

---

## 📘 Descripción general

El análisis se basa en el dataset **`heart_disease_patients.csv`**, que contiene información anonimizada de pacientes del **V.A. Medical Center (Long Beach, CA)**.  
La hipótesis subyacente es que pacientes con perfiles fisiológicos semejantes pueden responder de forma similar a ciertos tratamientos o presentar riesgos comparables de enfermedad coronaria.

El proceso se desarrolla en **Python**, con un enfoque exploratorio y visual, abarcando limpieza de datos, escalado, selección de variables y aplicación del algoritmo **K-means**.

---

## 📂 Estructura del proyecto

```plaintext
Heart-Disease-Clustering/
│
├── heart_disease_clustering.ipynb
├── data/
│ ├── heart_disease_patients.csv
│ └── heart_disease_patients_summary.txt
│
└── README.md
```

---

## 📊 Descripción de los datos

Cada registro corresponde a un paciente diagnosticado con alguna forma de enfermedad cardíaca.  
A continuación, se listan las principales variables consideradas (ver detalles completos en `heart_disease_patients_summary.txt`):

| Variable | Descripción |
|-----------|--------------|
| `age` | Edad del paciente |
| `sex` | Género (1 = hombre, 0 = mujer) |
| `cp` | Tipo de dolor en el pecho |
| `trestbps` | Presión arterial en reposo (mm Hg) |
| `chol` | Colesterol sérico (mg/dl) |
| `fbs` | Azúcar en sangre en ayunas > 120 mg/dl (1 = sí, 0 = no) |
| `restecg` | Resultados del electrocardiograma en reposo |
| `thalach` | Frecuencia cardíaca máxima alcanzada |
| `exang` | Angina inducida por ejercicio (1 = sí, 0 = no) |
| `oldpeak` | Depresión del segmento ST inducida por ejercicio |
| `slope` | Pendiente del segmento ST máximo de ejercicio |

---

## 🧠 Metodología

1. **Preprocesamiento de datos**
   - Carga del dataset y exploración inicial.
   - Tratamiento de valores faltantes.
   - Estandarización de variables numéricas mediante `StandardScaler`.

2. **Selección del número de clusters**
   - Uso del método del **codo (Elbow method)** para determinar el valor óptimo de *K*.

3. **Aplicación del algoritmo K-means**
   - Entrenamiento del modelo con los datos escalados.
   - Asignación de etiquetas de cluster a cada paciente.

4. **Análisis e interpretación**
   - Visualización 2D con PCA para representar la distribución de los clusters.
   - Comparación de medias de las variables más relevantes por grupo.
   - Discusión de patrones clínicos observados.

---

## 📈 Resultados destacados

El modelo de **K-means** permitió identificar **agrupaciones naturales de pacientes** con perfiles cardiovasculares distintos dentro del conjunto de datos.  
Tras aplicar el método del **codo (Elbow Method)** y analizar el **índice de silueta**, se determinó que el número óptimo de clusters era **K = 3**, reflejando tres grupos clínicamente diferenciables:

1. **Cluster 0 — Perfil de bajo riesgo:**  
   Pacientes con valores promedio de colesterol y presión arterial dentro de rangos normales, sin presencia de angina inducida por ejercicio.  
   Estos individuos tienden a presentar una **frecuencia cardíaca máxima alta** y una **depresión ST mínima**, lo que sugiere una buena respuesta al esfuerzo físico.

2. **Cluster 1 — Perfil intermedio o moderado:**  
   Grupo con valores de colesterol y presión arterial ligeramente superiores al promedio, junto con una frecuencia cardíaca máxima media.  
   Presentan una **mayor incidencia de dolor torácico atípico (cp = 2)** y niveles moderados de `oldpeak`.  
   Podrían corresponder a pacientes en observación o en fases iniciales de enfermedad coronaria.

3. **Cluster 2 — Perfil de alto riesgo:**  
   Pacientes con **colesterol elevado**, **presión arterial en reposo alta** y **frecuencia cardíaca máxima reducida**.  
   La mayoría muestra **angina inducida por ejercicio (exang = 1)** y valores altos de **depresión ST (`oldpeak`)**, indicadores asociados a mayor severidad.  
   Este grupo podría representar a los pacientes que requieren **seguimiento médico intensivo** o tratamientos especializados.

---

Además, se empleó una **reducción de dimensionalidad mediante PCA (Análisis de Componentes Principales)** para representar los grupos en un espacio bidimensional, observándose **separaciones claras entre los clusters**.  
Los resultados visuales confirmaron que las variables más influyentes en la formación de los grupos fueron:
- `chol` (colesterol sérico)
- `trestbps` (presión arterial en reposo)
- `thalach` (frecuencia cardíaca máxima alcanzada)
- `oldpeak` (depresión ST inducida por ejercicio)

---

En conjunto, los hallazgos muestran que el algoritmo **K-means** es capaz de segmentar a los pacientes en función de sus características clínicas clave, proporcionando una base útil para:
- **Apoyar la toma de decisiones médicas**, priorizando la atención según niveles de riesgo.  
- **Explorar patrones de evolución y respuesta al tratamiento.**  
- **Construir modelos predictivos más precisos** en futuros trabajos supervisados.

---

## 🛠️ Tecnologías y librerías utilizadas

- **Python 3.9 o superior**
- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `scikit-learn` (KMeans)

---

## 👥 Autores

Proyecto desarrollado colaborativamente como Microproyecto 2 del curso de **Introducción a la Inteligencia Artificial** de la Universidad Nacional de Colombia - Sede Medellín.

**Equipo 9:**

- Jacobo Ochoa Ramírez
- Juan Manuel Rodríguez Sánchez
- Luis Alejandro Varela Ojeda