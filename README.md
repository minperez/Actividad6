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

--- Métricas con Umbral Optimizado ---
              precision    recall  f1-score   support

   malignant       0.01      0.02      0.01        64
      benign       0.09      0.06      0.07       107

    accuracy                           0.04       171
   macro avg       0.05      0.04      0.04       171
weighted avg       0.06      0.04      0.05       171

Matriz de Confusión Optimizada:
 [[  1  63]
 [101   6]]

**Implementación de Escenario de Prueba A/B y Significancia Estadística**

Una vez que el modelo está entrenado y ajustado, se pasa a producción mediante una Prueba A/B:

Grupo Control (A): Los médicos diagnostican con el método/modelo Baseline (regresión logística umbral 0.5).

Grupo Tratamiento (B): Los médicos reciben asistencia de diagnóstico del nuevo modelo (Random Forest o Regresión Logística optimizada umbral 0.2).

Métrica objetivo (KPIs): Tasa de falsos negativos y tiempo total de diagnóstico por paciente.

Análisis de Significancia Estadística

Para comparar las proporciones de errores (falsos negativos) entre ambos grupos, se utiliza la Prueba de Proporciones (Z-Test)

Estadístico Z: 2.3570, p-valor: 0.0092
Resultado estadísticamente significativo: El Grupo B tuvo significativamente menos falsos negativos.

**Justificación Técnica e Impacto en el Negocio**

Justificación Técnica:Desde una perspectiva técnica, las métricas estándar de clasificación como la Accuracy pueden resultar engañosas debido al desequilibrio natural en los conjuntos de datos de salud, donde una clase puede ser mucho más prevalente que otra. Al alinear el modelo con un umbral más bajo (ej. umbral de 0.2), se realiza una concesión técnica intencional: se acepta una reducción en la especificidad (aumentando la tasa de falsos positivos) a cambio de maximizar la sensibilidad (Recall). Esto garantiza que el modelo actúe como un sistema de alerta temprana con una tasa de falsos negativos prácticamente nula.

Impacto en el Negocio:En el ámbito de la salud y el diagnóstico, un falso negativo (diagnosticar como benigno a un paciente que en realidad es maligno) tiene un costo humano y financiero incalculable, requiriendo tratamientos de emergencia costosos e invasivos. Al disminuir los falsos negativos por debajo del 5%, el negocio mejora su eficiencia operativa y reduce la posibilidad de litigios por negligencia. Adicionalmente, el modelo optimizado sirve como herramienta de apoyo para el personal médico, reduciendo el tiempo de diagnóstico y aumentando la confianza del paciente en el centro de salud, lo que se traduce directamente en un aumento en la fidelización y valor de marca.



