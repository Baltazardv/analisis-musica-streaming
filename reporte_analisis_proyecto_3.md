# Reporte de Análisis - Proyecto 3: Análisis de Música Streaming

## 📊 Resumen del Dataset

**Datos Iniciales:**
- Total de registros en el dataset original: 65,079
- Total de columnas: 7
- Tipos de datos encontrados: ['object']

**Información de Columnas:**
- **userid**: 65,079 no nulos, object
- **track**: 63,736 no nulos, object
- **artist**: 57,512 no nulos, object
- **genre**: 63,881 no nulos, object
- **city**: 65,079 no nulos, object
- **time**: 65,079 no nulos, object
- **day**: 65,079 no nulos, object

## 🧹 Preprocesamiento de Datos

### Valores Ausentes (Antes de Limpieza)
- **track**: 1,343 valores nulos (2.06%)
- **artist**: 7,567 valores nulos (11.63%)
- **genre**: 1,198 valores nulos (1.84%)

### Duplicados
- **Duplicados exactos encontrados**: 3,826
- **Porcentaje de duplicados**: 5.88%
- **Registros después de eliminar duplicados**: 61,253

### Duplicados Implícitos en Géneros
- **Géneros únicos antes de corrección**: 269
- **Géneros corregidos**: hip, hop → hiphop
- **Total de registros de 'hiphop' después de corrección**: 3,055
- **Géneros únicos después de corrección**: 267

### Dataset Final Limpio
- **Total de registros finales**: 61,253
- **Columnas normalizadas**: userid, track, artist, genre, city, time, day
- **Valores ausentes restantes**: 0

## 🎵 Análisis por Ciudad y Día

### Lunes (Monday)
- **Springfield**: 15,740 reproducciones
- **Shelbyville**: 5,614 reproducciones
- **Diferencia**: 10,126 reproducciones
- **Ciudad con mayor actividad**: Springfield

### Viernes (Friday)
- **Springfield**: 15,945 reproducciones
- **Shelbyville**: 5,895 reproducciones
- **Diferencia**: 10,050 reproducciones
- **Ciudad con mayor actividad**: Springfield

### Miércoles (Wednesday)
- **Springfield**: 11,056 reproducciones
- **Shelbyville**: 7,003 reproducciones
- **Diferencia**: 4,053 reproducciones
- **Ciudad con mayor actividad**: Springfield

### Resumen de Actividad por Día
| Día | Springfield | Shelbyville | Diferencia | % Diferencia* |
|-----|-------------|-------------|------------|--------------|
| Monday | 15,740 | 5,614 | 10,126 | 64.33% |
| Wednesday | 11,056 | 7,003 | 4,053 | 36.66% |
| Friday | 15,945 | 5,895 | 10,050 | 63.03% |



## 🎸 Top 10 Géneros por Ciudad

### Springfield - Top 10 Géneros
1. **pop**: 5,892 reproducciones (13.79%)
2. **dance**: 4,435 reproducciones (10.38%)
3. **rock**: 3,965 reproducciones (9.28%)
4. **electronic**: 3,786 reproducciones (8.86%)
5. **hiphop**: 2,095 reproducciones (4.90%)
6. **classical**: 1,616 reproducciones (3.78%)
7. **world**: 1,432 reproducciones (3.35%)
8. **alternative**: 1,379 reproducciones (3.23%)
9. **ruspop**: 1,372 reproducciones (3.21%)
10. **rusrap**: 1,161 reproducciones (2.72%)

### Shelbyville - Top 10 Géneros
1. **pop**: 2,431 reproducciones (13.13%)
2. **dance**: 1,932 reproducciones (10.44%)
3. **rock**: 1,879 reproducciones (10.15%)
4. **electronic**: 1,736 reproducciones (9.38%)
5. **hiphop**: 960 reproducciones (5.19%)
6. **alternative**: 649 reproducciones (3.51%)
7. **classical**: 646 reproducciones (3.49%)
8. **rusrap**: 564 reproducciones (3.05%)
9. **ruspop**: 538 reproducciones (2.91%)
10. **world**: 515 reproducciones (2.78%)

### Géneros Comunes en Top 10
- pop
- dance
- rock
- electronic
- hiphop
- classical
- world
- alternative
- ruspop
- rusrap

(Nota: El orden varía pero los 10 géneros son idénticos en ambas ciudades)

## 📈 Métricas Adicionales

### Distribución de Actividad
- **Total de reproducciones procesadas**: 61,253
- **Promedio de reproducciones por día**: 20,417.67
- **Ciudad más activa en general**: Springfield
- **Día con mayor actividad global**: Viernes (Friday)
- **Día con menor actividad global**: Miércoles (Wednesday)

### Estadísticas de Género
- **Género más popular (global)**: pop con 8,323 reproducciones
- **Género menos popular del top 20**: rusrock con 612 reproducciones
- **Número total de géneros únicos**: 267

### Comparativa de Ciudades
- **Porcentaje de actividad de Springfield**: 69.78%
- **Porcentaje de actividad de Shelbyville**: 30.22%
- **Ratio Springfield/Shelbyville**: 2.31

## 💡 Insights Clave

1. **Dominio de Springfield**: Springfield domina la actividad con más del doble de reproducciones que Shelbyville (Ratio 2.31), lo que sugiere una base de usuarios significativamente mayor o más activa.
2. **Patrón de "Viernes Festivo"**: Ambas ciudades muestran su pico de actividad los viernes, indicando un comportamiento de consumo similar alineado con el fin de semana. Sin embargo, Springfield cae drásticamente el miércoles (-29% vs Lunes), mientras que Shelbyville es más estable e incluso sube el miércoles respecto al lunes (+24%), sugiriendo patrones de uso semanales opuestos.
3. **Homogeneidad de Gustos**: A pesar de la diferencia en volumen, las preferencias musicales son sorprendentemente similares. Los Top 10 géneros son idénticos en composición (Pop, Dance, Rock lideran), variando solo ligeramente en clasificación relativa.
4. **Impacto de la Calidad de Datos**: El alto porcentaje de artistas desconocidos (11.6%) sugiere la necesidad de mejorar la metadata en la ingestión de datos, aunque la limpieza de géneros (hiphop) fue efectiva para consolidar categorías fragmentadas.
