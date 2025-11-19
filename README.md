# Proyecto de Estimación del Ingreso Disponible Ajustado (YDA) mediante Machine Learning

## Descripción general del proyecto

Este repositorio contiene el código, experimentos y documentación asociados al trabajo de investigación orientado a la estimación del Ingreso Disponible Ajustado (YDA) utilizando modelos de aprendizaje automático supervisado aplicados a la Encuesta Continua de Hogares (ECH) 2024.
El objetivo principal del estudio es evaluar la capacidad predictiva de diferentes algoritmos, incluyendo modelos basados en árboles y esquemas de combinación lineal, y analizar la importancia relativa de las variables socioeconómicas para la predicción del ingreso.

El proyecto incluye:
- Limpieza y preprocesamiento detallado del dataset.
- Exploración y análisis descriptivo (EDA).
- Entrenamiento de modelos de regresión penalizada, Random Forest, XGBoost y LightGBM.
- Validación cruzada con RandomizedSearchCV.
- Modelos de combinación lineal (Blending y Stacking).
- Curvas de aprendizaje, curvas de validación y análisis de Feature Importance.

## Estructura del repositorio

El repositorio contiene versiones progresivas de desarrollo, reflejando la evolución metodológica del trabajo:

- ECH 2024 EDA: primera versión del análisis exploratorio, inspección inicial del dataset y limpieza preliminar.
- ECH 2024 EDA 2: versión definitiva del EDA con limpieza avanzada con eliminacion de variables categoricas y verificacion de valores nulos, análisis descriptivo, imputacion logica de variables, unificacion de variables d181 y d 184, correlacion con variable objetivo, pipelines de transformacion y eliminación de variables con varianza cero y correlación alta. Separación formal del EDA respecto del modelado.

- ECH 2024 Modelado: primeros experimentos de modelado junto con el EDA. Incluye pruebas preliminares sin validación cruzada ni ajustes avanzados.
- ECH 2024 Modelado 2: EDA y modelado separados, algoritmos con Random Forest, XGBoost y LightGBM sin sobreajuste, primeras pruebas con Cross Validation (3 folds), métricas de desempeño en train y test.
- ECH 2024 Modelado 3: modelado definitivo que incluye reducción de complejidad de modelos (menos árboles para RF y GBMs), Cross Validation (3 folds) con RandomizedSearchCV, Feature Importance para Random Forest y evaluación completa (R², MAE, RMSE).

- ECH 2024 Blending y Stacking: primera versión de los modelos de combinación lineal.
- ECH 2024 Blending y Stacking 2: versión definitiva con meta-modelo lineal basado en regresión, Feature Importance del Stacking, comparación de desempeño frente a los modelos individuales.

## Tecnologías utilizadas:
- Python 3.x
- scikit-learn
- XGBoost
- LightGBM
- numpy, pandas, matplotlib, seaborn
- Visual Studio Code
- GitHub para control de versiones

## Metodología en resumen:
- Preprocesamiento extensivo del dataset (limpieza, eliminación de variables redundantes y codificación de variables cualitativas).
- División Train/Test conservando representatividad.
- Validación cruzada con 3 folds, ajustada a las limitaciones de hardware (uso intensivo de RAM debido al tamaño de la ECH 2024).
- Búsqueda de hiperparámetros mediante RandomizedSearchCV, priorizando eficiencia computacional.
- Evaluación estandarizada mediante R², MAE y RMSE.
- Modelos de combinación lineal para mejorar estabilidad y performance.

## Resultados principales:
- Los modelos basados en árboles mostraron un buen desempeño predictivo.
- El Tuning con RandomizedSearchCV tuvo mejoras moderadas en desempeño.
- El Random Forest mostró el mejor equilibrio entre bias y varianza.
- Blending (promedio de predicciones de RF y XGBoost) y Stacking (combinación de RF y XGB con meta-modelo lineal) alcanzan R² equivalente a 0.93–0.94 similar al RF simple.
- Stacking logra el mejor resultado general y mayor estabilidad.

## Próximas mejoras y líneas futuras:
- Probar stacking con meta-modelos no lineales o redes neuronales o modelos híbridos mas sofisticados.
- Evaluar la robustez externa de los hallazgos aplicando los modelos a distintas definiciones del ingreso.
- Usar técnicas avanzadas de interpretabilidad como los SHAP values (SHapley Additive exPlanations).
- Optimizar los procedimientos de validación, aumentar el numero de folds y reentrenar los modelos sobre subconjuntos de variables más relevantes.
- Explorar enfoques de clasificación que utilicen umbrales de ingreso.