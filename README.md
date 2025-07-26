# Proyecto 3 – Predicción de dureza final en aceros templados

Este proyecto aplica Machine Learning tradicional para predecir la **dureza final (HRC)** de aceros al carbono y baja aleación, a partir de su composición química y parámetros de tratamiento térmico (templado y revenido).

## 📦 Dataset

El dataset fue extraído de Kaggle:  
📌 *Tempering Data for Carbon and Low Alloy Steels*  
Incluye más de 1000 observaciones con las siguientes variables:

- Composición química: C, Mn, P, S, Si, Ni, Cr, Mo, V, Al, Cu (% en peso)
- Parámetros del revenido: tiempo (s) y temperatura (°C)
- Tipo de acero (Steel Type), fuente y dureza final medida (HRC)

El dataset fue limpiado y procesado, eliminando la columna `Initial Hardness` por alta cantidad de valores faltantes.

## 🧪 Objetivo del proyecto

Predecir la **dureza final HRC** post-templado y revenido usando modelos de regresión supervisada.

## 📁 Estructura del proyecto

```
.
├── data/                   # Datos originales y limpios
├── processed_data/        # Conjuntos de train/val/test
├── models/                # Modelos entrenados (.pkl)
├── mlruns/                # Experimentos registrados con MLflow
├── notebooks/
│   ├── 01_eda.ipynb             # Análisis exploratorio de datos
│   ├── 02_preprocessing.ipynb   # Limpieza, escalado, codificación
│   ├── 03_training_validation.ipynb # Entrenamiento y validación de modelos
│   └── 04_evaluation_export.ipynb   # Evaluación final y exportación
└── requirements.txt       # Librerías requeridas
```

## 🧠 Modelos evaluados

Se entrenaron y compararon los siguientes modelos:

- **Regresión Lineal**
- **Ridge**
- **Lasso**
- **Random Forest**

El mejor desempeño fue obtenido con **Random Forest**, con los siguientes resultados sobre el conjunto de validación:

```
MSE: 3.95
MAE: 1.36
```

## 🧪 Evaluación final

Evaluado en el conjunto de prueba:

```
MSE: 6.95
MAE: 1.73
```

## 🧰 Herramientas utilizadas

- Python 3.10
- pandas, numpy, scikit-learn, seaborn, matplotlib
- MLflow para registro de experimentos
- Jupyter Notebooks para desarrollo iterativo

## 📌 Consideraciones

- Se descartaron columnas con más del 80% de valores faltantes
- Se utilizó codificación one-hot para variables categóricas
- Se aplicó `StandardScaler` a las variables numéricas
- Se utilizó `train_test_split` con partición 60/20/20
- Se entrenó con validación manual y `RandomizedSearchCV`
