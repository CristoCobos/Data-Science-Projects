# Predicción de reclamaciones de seguros de viaje

Proyecto de clasificación binaria para predecir si una póliza tendrá una reclamación (`Claim`).

## Objetivo
Construir modelos que identifiquen reclamaciones y comparar su desempeño usando principalmente **F1**, debido al desequilibrio de clases.

## Técnicas
- Regresión logística.
- `class_weight="balanced"`.
- Upsampling.
- Downsampling.
- Árbol de decisión con `OrdinalEncoder`.
- Ajuste de umbral con `predict_proba`.
- Curva ROC y AUC-ROC.
- Matriz de confusión.

## Datos
El notebook utiliza `travel_insurance_us.csv`. El dataset no se incluye en el repositorio. Colócalo en `data/travel_insurance_us.csv`.

Variables: `Agency`, `Agency Type`, `Distribution Channel`, `Product Name`, `Duration`, `Destination`, `Net Sales`, `Commission`, `Gender`, `Age`.

Objetivo: `Claim` (1 = reclamación, 0 = sin reclamación).

## Ejecución
```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```
Abrir `notebooks/travel-insurance-claims.ipynb` y ejecutar las celdas en orden.

## Estructura
```text
travel-insurance-claims/
├── data/
├── notebooks/
│   └── travel-insurance-claims.ipynb
├── .gitignore
└── README.md
```

Los resultados no se inventan: se calculan al ejecutar el notebook con el dataset real.
