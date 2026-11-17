# Pre-entrega-14
# Análisis de Distribución y Detección de Outliers

Trabajo práctico desarrollado para el curso de Data Science / Análisis de Datos de Coderhouse.

## Origen de los Datos
Se utilizó el dataset **`tips` (Propinas)** provisto de forma nativa por la librería **Seaborn** de Python. Este conjunto de datos contiene 244 registros (243 tras eliminar duplicados) sobre las cuentas y propinas recibidas en un restaurante, incluyendo variables numéricas (`total_bill`, `tip`, `size`) y categóricas (`sex`, `smoker`, `day`, `time`).

## Hallazgos Principales
* **Asimetría:** Las variables `total_bill` y `tip` presentan asimetría positiva (cola hacia la derecha), concentrando la mayoría de los consumos en montos bajos/medios.
* **Outliers:** Mediante el método del Rango Intercuartílico (IQR) y la visualización con Boxplots y Violin Plots, se detectaron valores atípicos superiores en ambas variables (cuentas mayores a ~$40.30 y propinas mayores a ~$5.90).

## Decisiones sobre los Outliers
Basándome en el análisis visual y en el contexto del negocio, **no eliminaría estos outliers**. 
* **Justificación:** Los valores extremos corresponden a mesas grandes (de 4 a 6 comensales) en turnos de cena durante los fines de semana. No son errores de carga ni anomalías técnicas, sino clientes reales de alto consumo.
* **Acción recomendada:** En caso de entrenar un modelo predictivo sensible a valores extremos (como una regresión lineal), optaría por aplicar una **transformación logarítmica** (`np.log1p`) sobre las variables para reducir la asimetría sin perder información valiosa de los clientes más rentables.
