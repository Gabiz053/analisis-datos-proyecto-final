# Predicción de Congestión de Tráfico en Madrid

Proyecto final de la asignatura **Análisis Inteligente de la Información**
— Máster en Ingeniería Informática, UC3M.

## Descripción del problema

Madrid cuenta con más de 4.000 puntos de medida de tráfico distribuidos por la ciudad.
Cada sensor registra cada 15 minutos la intensidad de vehículos, la ocupación de la
calzada y la **carga** (0–100%), que mide el nivel de saturación de la vía.

El objetivo de este proyecto es predecir si una vía va a estar congestionada en función
de la hora, el día de la semana y la ubicación del sensor. Un modelo de este tipo puede
servir para anticipar atascos, optimizar rutas o predecir picos de contaminación.

## Datos

Los datasets provienen del [portal de datos abiertos del Ayuntamiento de Madrid][mad].

| Dataset | Descripción |
| --- | --- |
| [Histórico de mediciones][hist] | Intensidad, ocupación y carga por sensor (CSV mensuales) |
| [Ubicación de sensores][sens] | Coordenadas y nombre de calle de cada punto de medida |

[mad]: https://datos.madrid.es
[hist]: https://datos.madrid.es/dataset/208627-0-transporte-ptomedida-historico
[sens]: https://datos.madrid.es/dataset/202468-0-intensidad-trafico

> Los ficheros CSV no están incluidos en el repositorio por su tamaño.
> Consulta `data/README.md` para las instrucciones de descarga.

## Requisitos

- Python 3.12
- Las dependencias están en `requirements.txt`

## Instalación

```bash
# Crear entorno virtual
python -m venv .venv
source .venv/Scripts/activate   # Windows
# source .venv/bin/activate     # Linux / macOS

# Instalar dependencias
pip install -r requirements.txt

# Descargar los datos (ver data/README.md)

# Lanzar Jupyter
jupyter notebook
```

## Estructura del proyecto

```text
analisis-datos-proyecto-final/
├── data/
│   └── README.md                      # Instrucciones de descarga
├── notebooks/
│   ├── 01_EDA_GGG.ipynb               # Análisis exploratorio de datos
│   ├── 02_Preparacion_GGG.ipynb       # Limpieza y preparación del dataset
│   ├── 03_Modelos_GGG.ipynb           # Comparativa de modelos de ML
│   └── 04_Evaluacion_GGG.ipynb        # Evaluación final y demo de predicción
└── requirements.txt
```

## Ejecución de los notebooks

Los notebooks deben ejecutarse en orden:

1. **`01_EDA_GGG.ipynb`** — Exploración de los datos. Patrones temporales y espaciales,
   análisis de errores de sensor y justificación del umbral de congestión.

2. **`02_Preparacion_GGG.ipynb`** — Limpieza de errores, merge de los dos datasets,
   ingeniería de características y definición de la variable objetivo. Genera el dataset
   procesado que usan los notebooks siguientes.

3. **`03_Modelos_GGG.ipynb`** — Comparativa de Regresión Logística, Random Forest y
   Gradient Boosting con justificación de métricas.

4. **`04_Evaluacion_GGG.ipynb`** — Evaluación del modelo seleccionado: matriz de confusión,
   curva ROC, feature importance y demo de predicción práctica por sensor y hora del día.
