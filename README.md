# Actividad6
**Descripción del Proyecto**

Este reporte compara un modelo base (Regresión Logística) frente a uno más complejo (Random Forest) utilizando el conjunto de datos de cáncer de mama (sklearn.datasets.load_breast_cancer). 

**Objetivo SMART**

Desarrollar un modelo de machine learning (clasificación) que logre reducir los falsos negativos a menos del 5% en la detección de tumores malignos para final de trimestre, manteniendo el recall (sensibilidad) por encima del 95% y mejorando la tasa de exactitud del modelo base actual utilizando el dataset de cáncer de mama de Wisconsin (load_breast_cancer).

**Entrenamiento y Métricas Principales (Baseline)**
--- Métricas de Regresión Logística (Baseline) ---
Exactitud (Accuracy) : 0.9883
Precisión (Precision): 0.9907
Recall (Sensibilidad): 0.9907
F1-score             : 0.9907

**Matriz de Confusión e Interpretación (Baseline)**
<img width="623" height="571" alt="image" src="https://github.com/user-attachments/assets/f6f88953-e833-4636-a18c-8078e42d1ce7" />

 **Validación Cruzada**
 Cross-Validation Accuracy - Baseline: 0.9824 (+/- 0.0379)
Cross-Validation Accuracy - Avanzado: 0.9623 (+/- 0.0421)

<img width="536" height="547" alt="image" src="https://github.com/user-attachments/assets/09784be6-f370-4d11-aa64-025124229707" />

**Ajuste de Umbral y Matriz Optimizada**

Dado nuestro objetivo SMART (priorizar la sensibilidad, minimizar a toda costa los falsos negativos), ajustamos el umbral estándar de (0.5) a uno más bajo (0.2) para la Regresión Logística.


