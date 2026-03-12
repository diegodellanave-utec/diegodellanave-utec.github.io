# Detección de Cascos de Seguridad con Redes Neuronales Convolucionales

## Descripción del Proyecto

Este proyecto desarrolla un sistema de computer vision (visión artificial) basado en deep learning para la detección automática del uso de cascos de seguridad en entornos laborales de construcción. El sistema utiliza una Red Neuronal Convolucional (CNN) para clasificación binaria: trabajadores **con casco** vs **sin casco**.

Según la Organización Internacional del Trabajo (OIT), al menos 60,000 trabajadores mueren cada año en accidentes en obras de construcción en todo el mundo. Este tipo de sistema podría integrarse con cámaras de vigilancia existentes para proporcionar monitoreo y alertas en tiempo real, contribuyendo a reducir accidentes laborales.

---

## Objetivo del Proyecto

Desarrollar un modelo de machine learning capaz de:
- Clasificar automáticamente imágenes de trabajadores en obras de construcción
- Identificar si la persona utiliza casco de seguridad
- Proporcionar una herramienta útil para sistemas de monitoreo de seguridad laboral

---

## Estructura del Notebook

El notebook está organizado en las siguientes secciones:

1. **Introducción**
   - Contexto del problema
   - Motivación e importancia

2. **Solución Propuesta**
   - Pipeline completo del sistema
   - Descripción de la arquitectura CNN

3. **Descripción de los Datos**
   - Dataset SHEL5K
   - Distribución de clases
   - Preprocesamiento necesario

4. **Preparación de Datos**
   - Extracción de cuadros delimitadores (bounding boxes)
   - Mapeo de clases (6 clases → 2 clases binarias)
   - Redimensionamiento y normalización
   - Aumento de datos (Data augmentation)
   - Entrenamiento, validación y prueba

5. **Arquitectura del Modelo**
   - 4 bloques convolucionales con filtros crecientes (32, 64, 128, 256)
   - BatchNormalization y Dropout
   - Global Average Pooling

6. **Entrenamiento**
   - Optimizador Adam
   - Callbacks (ReduceLROnPlateau, EarlyStopping, ModelCheckpoint)

7. **Evaluación**
   - Métricas: Accuracy, Precision, Recall, F1-Score, AUC-ROC
   - Matriz de confusión
   - Curva ROC

---

## Dataset Utilizado

### SHEL5K (Safety HELmet dataset)

**Nombre:** Hard Hat Detection Dataset

**Descripción:** Dataset benchmark público para detección de cascos de seguridad, disponible en Kaggle. Contiene 5,000 imágenes con 75,570 instancias anotadas en 6 clases.

**Fuente:** [Kaggle - Hard Hat Detection](https://www.kaggle.com/datasets/andrewmvd/hard-hat-detection)

**Clases originales:**
- helmet (casco solo)
- head (cabeza sin casco)
- head with helmet (cabeza con casco)
- person with helmet (persona con casco)
- person without helmet (persona sin casco)
- face (rostro visible sin casco)

**Clasificación binaria:**
- **Con casco (1):** helmet, head with helmet, person with helmet
- **Sin casco (0):** head, person without helmet, face

---

## Tecnologías Utilizadas

- Python
- Jupyter Notebook
- TensorFlow / Keras
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- KaggleHub

---

## Arquitectura del Modelo

```
Modelo CNN:
- Bloque 1: Conv2D(32) + BatchNorm + ReLU + MaxPool
- Bloque 2: Conv2D(64) + BatchNorm + ReLU + MaxPool
- Bloque 3: Conv2D(128) + BatchNorm + ReLU + MaxPool + Dropout(0.3)
- Bloque 4: Conv2D(256) + BatchNorm + ReLU + MaxPool + Dropout(0.4)
- GlobalAveragePooling2D
- Dense(128) + Dropout(0.5)
- Dense(1, sigmoid)
```

**Total de parámetros:** ~500,000 parámetros entrenables

---

## Resultados Obtenidos

| Métrica | Valor |
|---------|-------|
| Accuracy | 97.95% |
| Precision | 99.02% |
| Recall | 98.36% |
| AUC-ROC | 0.9943 |

### Análisis de la Matriz de Confusión

- **Verdaderos negativos (sin casco correctamente clasificados):** 592
- **Verdaderos positivos (con casco correctamente clasificados):** 2,225
- **Falsos positivos:** 22
- **Falsos negativos:** 57

### Discusión

El modelo alcanza un rendimiento excepcional (>97%) en la tarea de clasificación binaria. La diferencia visual marcada entre cabezas con casco y sin casco (forma, color, textura) explica estos resultados.

**Limitaciones identificadas:**
- Las bounding boxes varían en tamaño; recortes muy pequeños pierden información
- El modelo clasifica recortes individuales, no detecta objetos en imágenes completas
- Para un sistema de producción, sería necesario integrar con un detector de objetos (YOLO, Faster R-CNN)

---

## Conclusiones

1. Una CNN relativamente simple es altamente efectiva para clasificar personas con y sin casco de seguridad
2. El modelo alcanza un AUC-ROC de 0.9943, demostrando excelente capacidad de discriminación
3. El recall del 96% para la clase "sin casco" es crucial en contextos de seguridad laboral
4. Como trabajo futuro, se recomienda integrar este clasificador con un detector de objetos para un sistema end-to-end

