# Predicción de Clientes Potenciales para ExtraaLearn

## Descripción del Proyecto

ExtraaLearn es una startup educativa que ofrece programas de tecnologías emergentes para profesionales y estudiantes. Este proyecto desarrolla un modelo de machine learning para identificar qué leads (clientes potenciales) tienen mayor probabilidad de convertirse en clientes de pago, permitiendo a la empresa optimizar la asignación de recursos de ventas y marketing.

El análisis incluye la identificación de los factores clave que impulsan el proceso de conversión y la creación de perfiles de leads con mayor probabilidad de compra.

---

## Objetivo del Proyecto

- Analizar y construir un modelo de machine learning para identificar qué leads tienen mayor probabilidad de convertirse en clientes de pago
- Encontrar los factores que impulsan el proceso de conversión
- Crear perfiles de leads con alta probabilidad de convertirse en clientes de pago

---

## Estructura del Notebook

El notebook está organizado en las siguientes secciones:

1. **Definición del Problema**
   - Contexto del problema
   - Descripción del dataset

2. **Exploratory Data Analysis (EDA)**
   - Descripción general de los datos
   - Análisis univariado
   - Análisis bivariado
   - Correlaciones

3. **Preprocesamiento de Datos**
   - Tratamiento de valores faltantes
   - Detección y tratamiento de outliers
   - Codificación de variables categóricas
   - Eliminación de duplicados

4. **Modelado**
   - Árbol de Decisión (base, podado, optimizado)
   - Random Forest (base, optimizado)
   - Optimización de hiperparámetros con GridSearchCV

5. **Evaluación**
   - Métricas: Accuracy, ROC-AUC, Precision, Recall
   - Matriz de confusión
   - Curvas ROC y Precision-Recall

6. **Insights Accionables**
   - Factores clave de conversión
   - Recomendaciones de negocio

---

## Dataset Utilizado

### ExtraaLearn Leads Dataset

**Nombre:** ExtraaLearn.csv

**Descripción:** Conjunto de datos que contiene diferentes atributos de leads y los detalles de su interacción con ExtraaLearn, una startup EdTech.

**Fuente:** Datos proporcionados para el proyecto

**Variables:**
| Variable | Descripción |
|----------|-------------|
| ID | Identificador único del lead |
| age | Edad del lead |
| current_occupation | Ocupación actual (Professional, Unemployed, Student) |
| first_interaction | Primer canal de interacción (Website, Mobile App) |
| profile_completed | Porcentaje de perfil completado (Low, Medium, High) |
| website_visits | Número de visitas al sitio web |
| time_spent_on_website | Tiempo total en el sitio web |
| page_views_per_visit | Promedio de páginas vistas por visita |
| last_activity | Última interacción (Email, Phone, Website) |
| print_media_type1 | Indicadores que señalan si el lead vio el anuncio en el periódico |
| print_media_type2 | Indicadores que señalan si el lead vio el anuncio en una revista |
| digital_media | Indicadores que señalan si el lead vio el anuncio en plataformas digitales |
| educational_channels | Indicadores que señalan si el lead supo de ExtraaLearn a través de canales educativos |
| referral | Indicadores que señalan si el lead supo de ExtraaLearn a través de una recomendación |
| status | Variable objetivo: 1 = convertido, 0 = no convertido |

**Dimensiones:** 4,612 registros × 15 variables

---

## Tecnologías Utilizadas

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- GridSearchCV

---

## Análisis Exploratorio - Hallazgos Clave

### Distribución del Target
- **No convertidos (0):** 70% (3,232 leads)
- **Convertidos (1):** 30% (1,380 leads)

El dataset está desbalanceado, lo que justifica el uso de técnicas como class_weight='balanced'.

### Factores que Influyen en la Conversión

| Factor | Impacto |
|--------|---------|
| **first_interaction = Website** | 45.62% conversión vs 10.57% (Mobile App) |
| **current_occupation = Professional** | 35.54% conversión vs 11.73% (Student) |
| **profile_completed = High/Medium** | ~40% conversión vs 7.48% (Low) |
| **referral** | 67.74% conversión (mayor tasa) |
| **time_spent_on_website** | Media: 1,070 seg (convertidos) vs 580 seg (no convertidos) |

### Insights Principales
1. **La primera interacción es crucial:** Los leads que llegan por el sitio web tienen 4x más probabilidad de convertir que los que vienen por app móvil
2. **Perfil completado importa:** Usuarios con perfil alto/medio tienen ~5x más probabilidad de conversión
3. **Las referencias son clave:** Los leads referidos tienen la tasa de conversión más alta (67.74%)
4. **El tiempo en sitio web diferencia:** Los convertidos pasan casi el doble de tiempo en el sitio

---

## Modelos Entrenados

### 1. Árbol de Decisión Podado

**Parámetros óptimos:**
- max_depth: 5
- min_samples_leaf: 10
- criterion: gini
- class_weight: balanced

**Rendimiento:**
| Métrica | Valor |
|---------|-------|
| Accuracy | 83.8% |
| ROC-AUC | 0.92 |
| Recall (clase 1) | 0.85 |

### 2. Random Forest Optimizado

**Parámetros óptimos:**
- n_estimators: 200
- max_features: 0.7
- max_depth: None
- min_samples_split: 5
- class_weight: balanced

**Rendimiento:**
| Métrica | Valor |
|---------|-------|
| Accuracy | 84.6% |
| ROC-AUC | 0.929 |
| Recall (clase 1) | 0.84 |

---

## Importancia de Features

**Top 5 factores más importantes (modelo Random Forest):**

1. **time_spent_on_website** - Tiempo total en el sitio web
2. **first_interaction_Website** - Primera interacción vía sitio web
3. **age** - Edad del lead
4. **page_views_per_visit** - Páginas vistas por visita
5. **profile_completed_High** - Perfil altamente completado

---

## Recomendaciones de Negocio

Basado en el análisis, se recomienda:

1. **Fortalecer adquisición digital vía sitio web:** Optimizar SEO y landing pages para maximizar conversiones desde el sitio web.

2. **Mejorar engagement en sitio:** Introducir navegación guiada, contenido dinámico y recomendaciones personalizadas.

3. **Activar leads templados:** Envío de recordatorios personalizados para usuarios con perfiles incompletos.

4. **Optimizar segmentación:** Usar scoring basado en comportamiento para priorizar leads.

5. **Invertir en programa de referencias:** Las referencias tienen la mayor tasa de conversión.

6. **Mantener retención:** Construir campañas de re-engagement para prevenir abandono de prospectos.

---

## Conclusiones

1. El modelo Random Forest optimizado alcanza un AUC-ROC de 0.929, lo que demuestra alta capacidad predictiva
2. La conversión está impulsada principalmente por el **comportamiento de engagement**, no por factores demográficos estáticos
3. Los leads que interactúan primero por el sitio web y pasan más tiempo tienen significativamente mayor probabilidad de convertir
4. Las referencias son el canal más efectivo para generar leads de alta calidad

