# EDA-MMTV-Erbb2
## Perfil Transcriptómico Diferencial Asociado a Metástasis en el Modelo MMTV-Erbb2
Este repositorio contiene el pipeline completo de análisis exploratorio de datos (EDA) y análisis estadístico para identificar genes diferencialmente expresados (DEGs) en un modelo murino de cáncer de mama con fenotipo metastásico frente a muestras control, utilizando datos de secuenciación de ARN (RNA-Seq).

### 📊 Descripción del Proyecto
El objetivo principal de este proyecto es caracterizar los patrones moleculares tempranos que impulsan la capacidad metastásica en el modelo tumoral MMTV-Erbb2. A partir del dataset público GSE223351 (NCBI GEO), se desarrolló un flujo de trabajo reproducible en Python que abarca desde la adquisición y normalización de los datos de conteo crudo hasta la visualización avanzada de biomarcadores potenciales.  La hipótesis central es que el fenotipo metastásico exhibe una firma de expresión génica significativamente alterada y consistente, identificable mediante métodos estadísticos robustos, lo que sienta las bases para futuros análisis funcionales de vías biológicas.

### 🛠️ Tecnologías y Herramientas
El pipeline fue desarrollado íntegramente en Python, empleando las siguientes librerías especializadas en ciencia de datos y bioinformática:
- Adquisición y Estructuración: Requests, Pandas
- Procesamiento Numérico: NumPy
- Análisis Estadístico: SciPy (stats), Statsmodels
- Visualización de Datos: Matplotlib, Seaborn

### 🧬 Flujo Metodológico
[Datos Crudos GEO] -> [Normalización TPM] -> [Filtrado por Varianza] -> [T-Test + Ajuste FDR] -> [Visualización (Volcano/Heatmap)]

1. Obtención y Carga: Descarga automatizada de la matriz de conteos crudos correspondientes a 6 muestras (3 Controles vs. 3 Metástasis).
2. Normalización: Implementación de la métrica Transcripts Per Million (TPM) seguida de una transformación logarítmica $\log_2(\text{TPM} + 1)$ para estabilizar la varianza. 
3. Filtrado: Eliminación de genes de baja variabilidad que no aportan poder discriminativo.  
4. Prueba de Hipótesis: Aplicación de un T-test independiente gen por gen. 
5. Corrección por Múltiples Pruebas: Ajuste de valores $p$ mediante la tasa de falso descubrimiento (FDR) de Benjamini-Hochberg. 
6. Clasificación: Selección rigurosa de genes utilizando los umbrales $|\log_2\text{FC}| [cite_start]\ge 1$ y $\text{FDR} \le 0.05$.

### 📈 Resultados Clave
- Identificación de Firmas Moleculares: Se logró segregar de manera robusta los perfiles expresivos asociados al fenotipo metastásico.
- Volcano Plot: Reveló una proporción notoria de genes significativamente sobreexpresados en las muestras con metástasis, respaldando la activación de rutas oncogénicas.
- Heatmap con Clustering Jerárquico: El análisis de los 20 genes más significativos (ej. Mira, Hoxa7, Hgfac, Tspan17) demostró una separación perfecta y consistente entre los grupos experimentales (Parental vs. 2a_9827).