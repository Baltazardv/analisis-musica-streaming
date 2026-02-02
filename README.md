# 🎵 Análisis de Comportamiento Musical: Springfield vs Shelbyville

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-green.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

## 🎯 Problema de Negocio

Una plataforma de streaming de música requiere entender los patrones de consumo en dos ciudades clave (Springfield y Shelbyville) para optimizar estrategias de contenido, marketing y recomendaciones personalizadas. El análisis busca validar si existen diferencias significativas en el comportamiento de usuarios según la ciudad y el día de la semana.

## 📊 Dataset

- **Registros iniciales**: 65,079 reproducciones
- **Registros finales (después de limpieza)**: 61,253
- **Período**: Datos históricos de streaming
- **Fuente**: `music_project_en.csv`

**Variables del dataset:**
- `userid`: Identificador único del usuario
- `track`: Nombre de la canción
- `artist`: Nombre del artista
- `genre`: Género musical
- `city`: Ciudad del usuario (Springfield o Shelbyville)
- `time`: Hora de reproducción
- `day`: Día de la semana (Monday, Wednesday, Friday)

**Problemas de calidad identificados:**
- ❌ 1,343 tracks sin nombre (2.06%)
- ❌ 7,567 artistas desconocidos (11.63%)
- ❌ 1,198 géneros sin clasificar (1.84%)
- ❌ 3,826 duplicados exactos (5.88%)
- ❌ Duplicados implícitos en géneros (`hip`, `hop` → `hiphop`)

## 🛠️ Stack Tecnológico

- **Python 3.9+**: Lenguaje de programación
- **Pandas 2.0+**: Manipulación y análisis de datos
- **Métodos de limpieza**: 
  - `.strip()`, `.lower()` para normalización de texto
  - `.fillna()` para valores ausentes
  - `.drop_duplicates()` para duplicados
  - `.replace()` para corrección de géneros
- **Jupyter Notebook**: Documentación interactiva

## 📈 Pasos Clave del Proyecto

1. **Exploración Inicial**: Análisis con `head()` e `info()` para identificar estructura y problemas
2. **Normalización de Encabezados**: Conversión a snake_case con list comprehension
3. **Manejo de Valores Ausentes**: Reemplazo con marcador `'unknown'` (1,343 tracks, 7,567 artists, 1,198 genres)
4. **Eliminación de Duplicados**: Remoción de 3,826 registros duplicados (5.88%)
5. **Corrección de Géneros**: Consolidación de `hip` + `hop` → `hiphop` (3,055 registros)
6. **Prueba de Hipótesis**: Comparación de actividad por ciudad y día

## ✅ Características del Análisis

✅ **Limpieza Exhaustiva**: Dataset reducido de 65,079 a 61,253 registros preservando integridad  
✅ **Normalización Completa**: Columnas estandarizadas en snake_case  
✅ **Manejo de Ausentes**: 0 valores nulos en dataset final  
✅ **Corrección de Inconsistencias**: 269 géneros únicos → 267 (consolidación efectiva)  
✅ **Análisis Comparativo**: Evaluación por ciudad, día y género  
✅ **Función Reutilizable**: `number_tracks()` para conteo dinámico

## 📊 Resultados del Análisis

### 📈 Preprocesamiento Aplicado

**Valores Ausentes Corregidos:**
- Tracks: 1,343 → 0 (reemplazados con 'unknown')
- Artists: 7,567 → 0 (11.63% del dataset)
- Genres: 1,198 → 0

**Duplicados Eliminados:**
- Duplicados exactos: 3,826 (5.88%)
- Registros finales: 61,253

**Géneros Consolidados:**
- Géneros únicos: 269 → 267
- Registros de 'hiphop' consolidados: 3,055

### 🎵 Análisis por Ciudad y Día

| Día | Springfield | Shelbyville | Diferencia | % Diferencia |
|-----|-------------|-------------|------------|--------------|
| **Monday** | 15,740 | 5,614 | 10,126 | 64.33% |
| **Wednesday** | 11,056 | 7,003 | 4,053 | 36.66% |
| **Friday** | 15,945 | 5,895 | 10,050 | 63.03% |

**Hallazgos clave:**
- 🏆 **Springfield domina** en todos los días con ~70% de la actividad total
- 📊 **Ratio Springfield/Shelbyville**: 2.31 (más del doble de reproducciones)
- 🎉 **Viernes = Pico de actividad** en ambas ciudades
- 📉 **Miércoles = Menor actividad** en Springfield (-29% vs lunes)
- 📈 **Miércoles = Actividad estable** en Shelbyville (+24% vs lunes)

### 🎸 Top 10 Géneros por Ciudad

#### Springfield
| # | Género | Reproducciones | % del Total |
|---|--------|----------------|-------------|
| 1 | **pop** | 5,892 | 13.79% |
| 2 | **dance** | 4,435 | 10.38% |
| 3 | **rock** | 3,965 | 9.28% |
| 4 | **electronic** | 3,786 | 8.86% |
| 5 | **hiphop** | 2,095 | 4.90% |
| 6 | **classical** | 1,616 | 3.78% |
| 7 | **world** | 1,432 | 3.35% |
| 8 | **alternative** | 1,379 | 3.23% |
| 9 | **ruspop** | 1,372 | 3.21% |
| 10 | **rusrap** | 1,161 | 2.72% |

#### Shelbyville
| # | Género | Reproducciones | % del Total |
|---|--------|----------------|-------------|
| 1 | **pop** | 2,431 | 13.13% |
| 2 | **dance** | 1,932 | 10.44% |
| 3 | **rock** | 1,879 | 10.15% |
| 4 | **electronic** | 1,736 | 9.38% |
| 5 | **hiphop** | 960 | 5.19% |
| 6 | **alternative** | 649 | 3.51% |
| 7 | **classical** | 646 | 3.49% |
| 8 | **rusrap** | 564 | 3.05% |
| 9 | **ruspop** | 538 | 2.91% |
| 10 | **world** | 515 | 2.78% |

**🎯 Géneros Comunes en Top 10:** Los 10 géneros son **idénticos** en ambas ciudades, solo varía el orden de preferencia.

### 📊 Métricas Globales

**Distribución de Actividad:**
- Total de reproducciones procesadas: **61,253**
- Promedio de reproducciones por día: **20,418**
- Ciudad más activa: **Springfield (69.78%)**
- Día con mayor actividad: **Viernes (21,840 reproducciones)**
- Día con menor actividad: **Miércoles (18,059 reproducciones)**

**Estadísticas de Género:**
- Género más popular global: **pop** (8,323 reproducciones)
- Número total de géneros únicos: **267**
- Top 3 géneros representan: **~33%** del total de reproducciones

**Comparativa de Ciudades:**
- Springfield: **69.78%** de actividad total
- Shelbyville: **30.22%** de actividad total
- Ratio de dominancia: **2.31:1**

## 💡 Insights de Negocio y Recomendaciones

### 1. 🎯 Dominio de Springfield
**Hallazgo:** Springfield genera más del doble de reproducciones (Ratio 2.31:1), indicando una base de usuarios significativamente mayor o más activa.

**Recomendación:**
- Invertir en adquisición de usuarios en Shelbyville para equilibrar la plataforma
- Crear campañas de retención específicas para Springfield (mercado clave)
- Analizar causas del dominio: ¿población, demografía, penetración de internet?

### 2. 📅 Patrón de "Viernes Festivo"
**Hallazgo:** Ambas ciudades muestran pico de actividad los viernes, alineado con el fin de semana. Springfield cae drásticamente el miércoles (-29%), mientras Shelbyville aumenta (+24%).

**Recomendación:**
- Lanzar playlists y promociones especiales los **viernes** (máximo engagement)
- En Springfield: contenido nuevo/exclusivo los **lunes** para mantener actividad
- En Shelbyville: aprovechar el miércoles para contenido mid-week (momento de bajo competencia)

### 3. 🎵 Homogeneidad de Gustos Musicales
**Hallazgo:** Top 10 géneros son idénticos en composición (Pop, Dance, Rock lideran), con solo ligeras variaciones en ranking.

**Recomendación:**
- Estrategia de contenido unificada por género: no requiere curación diferenciada
- Oportunidad de cross-promotion: usuarios de una ciudad pueden descubrir artistas populares de la otra
- Personalización por ciudad innecesaria a nivel de género; enfocarse en artistas/canciones específicas

### 4. 📊 Impacto de la Calidad de Datos
**Hallazgo:** 11.63% de artistas desconocidos representa una brecha significativa en metadata.

**Recomendación:**
- Implementar validación de metadata en el proceso de ingesta
- Enriquecer datos existentes con APIs de música (Spotify, MusicBrainz)
- Priorizar corrección de artistas populares (mayor impacto en recomendaciones)

### 5. 🚀 Oportunidades de Crecimiento
**Basado en los patrones identificados:**
- **Shelbyville**: Mercado con alto potencial de crecimiento (+130% para igualar Springfield)
- **Miércoles en Springfield**: Día con oportunidad de impulso (+44% vs miércoles actual)
- **Géneros nicho**: 267 géneros únicos sugieren audiencia diversa más allá del top 10

## 📈 Validación de Hipótesis

### Hipótesis Planteada
*"La actividad de los usuarios difiere según el día de la semana y la ciudad"*

### ✅ HIPÓTESIS CONFIRMADA

**Evidencia:**

1. **Diferencia por Ciudad:**
   - Springfield: 69.78% de actividad
   - Shelbyville: 30.22% de actividad
   - Diferencia estadísticamente significativa (Ratio 2.31:1)

2. **Diferencia por Día:**
   - Viernes: 21,840 reproducciones (pico)
   - Miércoles: 18,059 reproducciones (valle)
   - Variación del 21% entre días extremos

3. **Interacción Ciudad-Día:**
   - Springfield: Patrón lunes-alto, miércoles-bajo, viernes-pico
   - Shelbyville: Patrón más estable con incremento en miércoles
   - Patrones de comportamiento **distintos** por ciudad

**Conclusión:** Se confirma que tanto la ciudad como el día de la semana influyen significativamente en la actividad de usuarios, con patrones diferenciados que justifican estrategias personalizadas.

## 🚀 Cómo Replicar el Proyecto

### Requisitos
```bash
Python 3.9+
pandas>=2.0.0
jupyter notebook
```

### Instalación
```bash
# Clonar repositorio
git clone https://github.com/Baltazardv/analisis-musica-streaming.git
cd analisis-musica-streaming

# Instalar dependencias
pip install pandas jupyter

# Abrir notebook
jupyter notebook proyecto_3_musica_limpio.ipynb
```

### Estructura de Archivos
```
analisis-musica-streaming/
├── README.md
├── proyecto_3_musica_limpio.ipynb
└── music_project_en.csv
```

### Ejecución
1. Asegúrate de que `music_project_en.csv` esté en la misma carpeta que el notebook
2. Ejecuta todas las celdas secuencialmente
3. Los resultados se generan automáticamente

## 🎯 Próximos Pasos

Este análisis establece fundamentos para:

1. **Análisis Temporal Profundo**: Explorar patrones horarios y tendencias mensuales
2. **Segmentación de Usuarios**: Clustering por comportamiento de escucha
3. **Sistema de Recomendación**: Modelos colaborativos basados en preferencias de ciudad
4. **Dashboard Interactivo**: Visualización en tiempo real con Streamlit o Plotly
5. **Predicción de Churn**: Identificar usuarios en riesgo de abandono
6. **A/B Testing Framework**: Validar estrategias de contenido diferenciadas por ciudad

## 💻 Habilidades Demostradas

- **Data Wrangling**: Limpieza exhaustiva de 65K+ registros con múltiples inconsistencias
- **Pandas avanzado**: Manipulación de DataFrames, filtrado condicional, agregaciones
- **Calidad de datos**: Identificación y corrección de valores ausentes, duplicados y duplicados implícitos
- **Análisis comparativo**: Evaluación de hipótesis con datos reales
- **Pensamiento de negocio**: Traducción de hallazgos técnicos en recomendaciones accionables
- **Documentación técnica**: Jupyter Notebook con estructura profesional

---

**📚 Proyecto desarrollado como parte del Bootcamp de Data Analytics en TripleTen**

**👨‍💻 Autor**: Baltazar Dimayuga  
**📧 Contacto**: [baltazardv13@gmail.com](mailto:baltazardv13@gmail.com)  
**💼 LinkedIn**: [linkedin.com/in/baltazar-dimayuga](https://linkedin.com/in/baltazar-dimayuga)  
**🐙 GitHub**: [github.com/Baltazardv](https://github.com/Baltazardv)
