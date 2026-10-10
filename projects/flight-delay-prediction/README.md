# Predicción de retrasos de vuelos

Proyecto de aprendizaje automático supervisado para estimar el retraso de llegada de vuelos en minutos.

## Objetivo

Construir y comparar modelos de regresión para predecir `Arrival Delay`. La métrica principal es el error absoluto medio (EAM/MAE), con el objetivo de alcanzar un EAM de validación de **26.2 minutos o menos**.

## Modelos

- Modelo de referencia: predicción constante con la mediana del conjunto de entrenamiento.
- Regresión lineal.
- Random Forest Regressor, con comparación de profundidades y evaluación de la configuración de 50 árboles y profundidad 8.

## Datos

El notebook espera el archivo `flights_preprocessed.csv`, que no se distribuye en este repositorio. Colócalo en `data/flights_preprocessed.csv`. También admite la ruta `/datasets/flights_preprocessed.csv`, usada en el entorno de los ejercicios.

La variable objetivo es `Arrival Delay`. El archivo debe contener las variables predictoras numéricas ya preprocesadas, tal como se describe en el material del curso.

## Cómo ejecutar

1. Instala las dependencias:
   ```bash
   pip install pandas numpy matplotlib scikit-learn jupyter
   ```
2. Copia el archivo de datos en `data/flights_preprocessed.csv`.
3. Abre Jupyter desde la carpeta raíz:
   ```bash
   jupyter notebook
   ```
4. Ejecuta `notebooks/prediccion_retrasos_vuelos.ipynb` de arriba hacia abajo.

## Métricas

El notebook calcula EAM, raíz del error cuadrático medio (RECM/RMSE) y R² sobre el conjunto de validación. Los resultados se generan a partir del archivo de datos al ejecutar el notebook; no se incluyen resultados estimados ni inventados.

## Estructura

```text
proyecto_prediccion_retrasos_vuelos/
├── data/                          # Colocar aquí el CSV (no incluido)
├── notebooks/
│   └── prediccion_retrasos_vuelos.ipynb
└── README.md
```

## Limitaciones

La predicción depende de las variables disponibles y de la calidad de los datos. La importancia de variables no implica causalidad y el rendimiento de validación no garantiza el mismo desempeño en producción.
