# Series temporales. Predicción de ventas

## Contexto

Este proyecto analiza una serie temporal de ventas diarias.

El objetivo es estudiar el comportamiento de las ventas, comprobar si la serie es estacionaria y entrenar un modelo `ARIMA` para predecir valores futuros.

El caso práctico está orientado a estimar la demanda futura y ayudar en la decisión sobre el espacio necesario para un nuevo almacén.

El proyecto parte del ejercicio original de [4Geeks Academy](https://github.com/4GeeksAcademy), disponible en el repositorio [alternative-time-series-project](https://github.com/4GeeksAcademy/alternative-time-series-project/tree/main).

## Dataset

El dataset usado es `sales.csv` y debe estar ubicado en la carpeta `data/raw/`.

La fuente del dataset es este enlace de [BreatheCode/4Geeks](https://breathecode.herokuapp.com/asset/internal-link?id=2546&path=sales.csv). Puede depender de la disponibilidad de la plataforma.

| Variable | Descripción | Tipo |
|----------|-------------|------|
| `date` | Fecha del registro de ventas | Fecha |
| `sales` | Ventas registradas para cada día | Numérico |

## Qué incluye el proyecto

- Carga y revisión inicial del dataset.
- Conversión de la columna `date` a índice temporal.
- Fijado de frecuencia diaria con `asfreq("D")`.
- Análisis visual de la serie temporal.
- Descomposición de la serie para revisar tendencia, estacionalidad y residuos.
- Prueba de `Dickey-Fuller` para comprobar estacionariedad.
- Diferenciación de la serie.
- Análisis de `ACF` y `PACF`.
- Entrenamiento de un modelo manual `ARIMA(1, 1, 1)`.
- Entrenamiento automático con `auto_arima`.
- Evaluación con `MAE`, `RMSE` y `MAPE`.
- Forecast futuro de 30 días.
- Guardado del modelo final en la carpeta `models/`.

## Resultados principales

Las ventas muestran una tendencia ascendente clara durante todo el periodo analizado.

La serie original no era estacionaria. Después de aplicar una primera diferenciación, la serie pasó a ser estacionaria.

El modelo manual `ARIMA(1, 1, 1)` sirvió como primera aproximación, pero su predicción quedaba algo por encima de los valores reales.

El modelo automático con `auto_arima` obtuvo mejores métricas sobre el conjunto de `test`. El `MAPE` fue cercano a `0.26%`, por lo que el error porcentual medio fue bajo.

Al entrenar el modelo final con toda la serie, `auto_arima` seleccionó un `ARIMA(1, 1, 1)` con `intercept`. Con este modelo se generó un forecast futuro de 30 días.

## Modelo guardado

El modelo final se guarda en:

```text
models/final_auto_arima_sales_model.pkl
```

Este modelo fue entrenado con toda la serie disponible y se usa para generar predicciones futuras de ventas.

## Cómo usar este proyecto

1. Clonar el repositorio.
2. Crear o activar un entorno de Python.
3. Instalar las dependencias.

```bash
pip install -r requirements.txt
```

4. El archivo `sales.csv` ya está incluido en `data/raw/`.
5. Abrir y ejecutar el notebook principal.

```text
src/explore.ipynb
```

## Archivos principales

- `src/explore.ipynb`: notebook principal con el análisis, modelado y conclusiones.
- `src/apple.mplstyle`: estilo visual usado en los gráficos.
- `data/raw/sales.csv`: dataset original usado para ejecutar el notebook.
- `models/final_auto_arima_sales_model.pkl`: modelo final entrenado.
- `requirements.txt`: dependencias necesarias para ejecutar el proyecto.

## Créditos

Este proyecto fue realizado como parte del [Bootcamp de Data Science y Machine Learning de 4Geeks](https://4geeksacademy.com/en/career-programs/data-science-ml).

El enunciado original pertenece a [4Geeks Academy](https://github.com/4GeeksAcademy).
