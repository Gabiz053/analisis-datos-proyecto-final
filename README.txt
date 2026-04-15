PREDICCIÓN DE CONGESTIÓN DE TRÁFICO EN MADRID
=============================================
Proyecto final de la asignatura Análisis Inteligente de la Información
— Máster en Ingeniería Informática, UC3M.
Alumno: Gabriel Gómez García (GGG).


DESCRIPCIÓN DEL PROBLEMA
-------------------------
Madrid tiene más de 4.000 puntos de medida de tráfico repartidos por toda
la ciudad. Cada sensor registra cada 15 minutos la intensidad de vehículos,
la ocupación de la calzada y la carga (0-100%), que mide el nivel de
saturación de la vía.

El objetivo del proyecto es predecir si una vía va a estar congestionada en
función de la hora, el día de la semana y la ubicación del sensor. Es un
problema de clasificación binaria. Un sistema así puede servir para anticipar
atascos, optimizar rutas o predecir picos de contaminación.


FUENTE DE DATOS
---------------
Portal de datos abiertos del Ayuntamiento de Madrid:
https://datos.madrid.es

- Histórico de mediciones (CSV mensuales por sensor):
  https://datos.madrid.es/dataset/208627-0-transporte-ptomedida-historico

- Catálogo de sensores con coordenadas y nombre de calle:
  https://datos.madrid.es/dataset/202468-0-intensidad-trafico

Los ficheros CSV no están incluidos en el repositorio por su tamaño.
El notebook 01 los descarga automáticamente al ejecutarse.
Consulta data/README.md si prefieres descargarlos a mano.


REQUISITOS E INSTALACIÓN
-------------------------
- Python 3.12
- Dependencias: pandas, numpy, matplotlib, seaborn, scikit-learn,
  requests, jupyter (todas en requirements.txt)

  python -m venv .venv
  source .venv/Scripts/activate          (Windows)
  source .venv/bin/activate              (Linux / macOS)
  pip install -r requirements.txt
  jupyter notebook

Los notebooks descargan los datos solos al ejecutarse.
No hace falta nada más.


ESTRUCTURA DEL PROYECTO
-----------------------
analisis-datos-proyecto-final/
├── data/
│   ├── raw/               (datos descargados; no se suben al repo)
│   ├── processed/         (dataset preparado por el notebook 02; no se sube)
│   └── README.md          (instrucciones de descarga manual)
├── notebooks/
│   ├── 01_EDA_GGG.ipynb
│   ├── 02_Preparacion_GGG.ipynb
│   ├── 03_Modelos_GGG.ipynb
│   └── 04_Evaluacion_GGG.ipynb
├── README.md
├── README.txt             (este fichero)
└── requirements.txt


EJECUCIÓN DE LOS NOTEBOOKS
---------------------------
Los notebooks deben ejecutarse en orden. Cada uno parte del trabajo
del anterior.

1. 01_EDA_GGG.ipynb — Análisis exploratorio de datos
   Descarga los datos del portal del Ayuntamiento y los explora a fondo.
   Se analiza cómo se distribuye la variable carga, se justifica el umbral
   del 70% para definir cuándo hay congestión, se estudian los errores de
   sensor y los patrones de tráfico por hora, día de la semana y distrito.
   Termina con los insights que guían el resto del proyecto.

2. 02_Preparacion_GGG.ipynb — Limpieza y construcción del dataset
   Aplica lo aprendido en el EDA: quita las lecturas erróneas, une las
   mediciones con la ubicación de cada sensor y construye las variables
   que usará el modelo (hora, día, si es hora punta, distrito...). Define
   la etiqueta binaria "congestionado" y divide los datos en entrenamiento
   y test. Guarda el resultado en data/processed/.

3. 03_Modelos_GGG.ipynb — Comparativa de modelos
   Explica por qué la accuracy no es una buena métrica aquí y elige F1 y
   AUC. Entrena tres modelos de complejidad creciente (regresión logística,
   Random Forest y Gradient Boosting) con validación cruzada, los compara
   en una tabla y elige el mejor justificando la decisión.

4. 04_Evaluacion_GGG.ipynb — Evaluación final y demo
   Abre el test por primera vez y evalúa el modelo con datos que no ha
   visto nunca. Incluye matriz de confusión, curva ROC, qué variables pesan
   más y en qué horas y zonas falla el modelo. Termina con una función que,
   dado un sensor y una hora, devuelve si habrá congestión y con qué
   probabilidad.
