# Datos

Los datasets no están incluidos en el repositorio por su tamaño. Sigue estas instrucciones
para descargarlos y colocarlos en las carpetas correctas antes de ejecutar los notebooks.

## Dataset 1: Histórico de mediciones

**URL:** <https://datos.madrid.es/dataset/208627-0-transporte-ptomedida-historico>

Descarga los ficheros CSV mensuales que necesites (un año completo es suficiente para
el análisis) y colócalos en `data/raw/historico/`.

```text
data/raw/historico/
├── 2024_01_Enero.csv
├── 2024_02_Febrero.csv
└── ...
```

## Dataset 2: Ubicación de los sensores

**URL:** <https://datos.madrid.es/dataset/202468-0-intensidad-trafico>

Descarga el fichero CSV de puntos de medida y colócalo en `data/raw/sensores/`.

```text
data/raw/sensores/
└── pmed_trafico.csv
```

## Estructura esperada

```text
data/
├── raw/
│   ├── historico/     <- CSVs mensuales de mediciones (separados por ;)
│   └── sensores/      <- CSV con metadata de cada sensor
└── processed/         <- generado automáticamente por 02_Preparacion_GGG.ipynb
```

> `data/raw/` y `data/processed/` están en `.gitignore` y no se suben al repositorio.
> Este README.md sí se incluye para que cualquiera pueda reproducir el entorno.
