# Modelo de Clasificación para Recomendar Planes Móviles - Megaline

¡Bienvenido al proyecto de clasificación de clientes de **Megaline**! 
Este repositorio contiene un modelo de aprendizaje automático que **predice si un cliente debe estar en el plan _Smart_ o _Ultra_**, basado en su comportamiento mensual.

## Descripción del Proyecto

Megaline busca migrar a sus clientes desde planes heredados hacia dos nuevos planes: `Smart` y `Ultra`.  
Este modelo se entrenó utilizando datos reales de usuarios, incluyendo:

- Número de llamadas realizadas
- Minutos consumidos
- Mensajes enviados
- Datos móviles utilizados (`mb_used`)

**Objetivo**: Desarrollar un modelo que recomiende automáticamente el mejor plan para cada cliente, con una precisión mínima del **75%**.

# Modelos Evaluados

Se probaron distintos modelos de clasificación con sus respectivos hiperparámetros.  
Los mejores resultados en validación fueron:

| Modelo                   | Parámetros        | Exactitud |
|--------------------------|-------------------|-----------|
| Random Forest            | n_estimators = 50 | 0.8025    |
| Decision Tree            | depth = 3         | 0.8040    |
| Logistic Regression      | -                 | 0.7045    |

El modelo seleccionado final fue **Random Forest (n=50)** por su estabilidad y buen desempeño en prueba (0.7885).

## Resultados Finales

| Conjunto   | Métrica              | Valor                                             | Descripción                                                                 |
| ---------- | -------------------- | ------------------------------------------------- | --------------------------------------------------------------------------- |
| Validación | Exactitud (Accuracy) | `0.7962`                                          | Proporción de predicciones correctas durante la validación del modelo.      |
| Prueba     | Exactitud (Accuracy) | `0.7885`                                          | Desempeño del modelo en datos no vistos (generalización).                   |
| Prueba     | Matriz de Confusión  | **                                                | Representación visual de aciertos y errores del modelo en la clasificación. |


-El modelo predice correctamente la mayoría de los casos, especialmente para el plan **Smart**, aunque comete algunos falsos positivos con el plan **Ultra**.

## Pruebas de Cordura

El modelo fue validado con pruebas de robustez:

- ✔️ Pequeñas variaciones en los datos no afectan significativamente la predicción.
- ✔️ Casos con usuarios similares devuelven predicciones coherentes.
- ✔️ Se supera el umbral mínimo de exactitud exigido por Megaline (0.75).

## Estructura del Proyecto

.
├── modelo-clasificacion-megaline.ipynb
├── README.md
├── data/
│   └── megaline_clients.csv
├── models/
│   └── best_model.pkl
├── visuals/
│   ├── confusion_matrix.png
│   └── feature_importance.png
├── requirements.txt
└── utils/
    └── preprocessing.py
