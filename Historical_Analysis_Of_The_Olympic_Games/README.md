# Análisis Histórico de los Juegos Olímpicos (1896-2016)

## Descripción del Proyecto

Este proyecto presenta un análisis exhaustivo de 120 años de historia de los Juegos Olímpicos modernos, desde Atenas 1896 hasta Río 2016. El estudio examina múltiples dimensiones: participación de países, rendimiento atlético, tendencias de género, evolución de disciplinas deportivas y factores que influyen en la obtención de medallas.

El análisis fue desarrollado como parte del curso de Fundamentos de Programación para la Ciencia de Datos e Inteligencia Artificial de la Especialización en Ciencia de Datos e Inteligencia Artificial de UTEC.

---

## Objetivo del Proyecto

El objetivo principal de este análisis es estudiar la evolución de los Juegos Olímpicos, tanto de verano como de invierno, desde su inicio hasta el año 2016. Se buscan responder preguntas clave sobre:

- Participación histórica de países
- Presencia y representación femenina a lo largo del tiempo
- Disciplinas deportivas y su evolución
- Medallas y rendimiento por país
- Características físicas de los atletas medallistas

---

## Estructura del Notebook

El notebook está organizado en las siguientes etapas:

1. **Contextualización y Carga de Datos**
   - Importación del dataset
   - Descripción de variables

2. **Evaluación de Calidad de Datos**
   - Análisis de integridad
   - Detección de duplicados
   - Verificación de validez y consistencia

3. **Limpieza y Preprocesamiento**
   - Imputación de valores faltantes
   - Estandarización de variables
   - Creación de variables derivadas (continente, país anfitrión, categoría de deporte)

4. **Análisis Exploratorio de Datos**
   - Estadísticos descriptivos
   - Distribuciones de variables numéricas
   - Análisis de correlaciones
   - Visualizaciones multivariadas

5. **Resultados y Conclusiones**
   - Hallazgos principales
   - Respuestas a preguntas clave

---

## Dataset Utilizado

### 120 Years of Olympic History

**Nombre:** Olympic Games Dataset

**Descripción:** Conjunto de datos históricos que contiene información sobre atletas que han participado en los Juegos Olímpicos desde 1896 hasta 2016. Incluye datos demográficos, desempeño deportivo y medallero por país.

**Fuente:** [Kaggle - 120 years of Olympic history](https://www.kaggle.com/datasets/heesoo37/120-years-of-olympic-history-athletes-and-results)

**Variables principales:**
- ID, Nombre, Género, Edad, Altura, Peso
- Equipo/País, Código NOC
- Año, Temporada, Ciudad sede
- Deporte, Evento
- Medal (Oro, Plata, Bronce, Sin medalla)

**Dimensiones:** 271,116 filas × 15 columnas

---

## Tecnologías Utilizadas

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Plotly
- SciPy (pruebas estadísticas)
- Prince (Análisis de Correspondencias Múltiples)

---

## Resultados Clave

### Participación Histórica
- Se han celebrado 28 ediciones oficiales de Verano y 22 de Invierno
- La participación creció de 14 países (1896) a 208 países (2016)
- Algunos países como Francia, Gran Bretaña, Grecia, Italia y Suiza han participado en TODAS las ediciones de Verano

### Evolución de la Participación Femenina
- 1896: Exclusión total de mujeres
- 2016: 45% de participación femenina
- En 2012, todos los países incluyeron al menos una mujer

### Factores que Influyen en las Medallas
- **Efecto sede:** Los países anfitriones tienden a ganar más medallas
- **Correlación positiva** entre cantidad de participantes y medallas obtenidas
- Los países especializados en ciertos deportes (como China en Gimnasia) muestran patrones de especialización

### Perfil de los Atletas
- Edad promedio: 22-28 años
- Altura promedio: 175 cm
- Peso promedio: 70 kg
- La relación altura-peso varía significativamente según el deporte

### Disciplinas Principales
- Atletismo, Natación y Gimnasia artística lideran en número de participantes
- Las disciplinas de marca son las más numerosas

---

## Visualizaciones Destacadas

- Heatmaps de participación por país y año
- Evolución de la participación femenina
- Distribución de edades, alturas y pesos por deporte
- Mapa de coropletas de medallas por país
- Análisis del "efecto sede" en el medallero

