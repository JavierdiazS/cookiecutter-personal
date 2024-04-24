# ECO DATA

## E-Commerce Olist: ETL | EDA | Segmentación de Clientes | Predicción de Valor de transacción

[![logo-ecodataa.png](https://i.postimg.cc/851LGQSX/logo-ecodataa.png)](https://postimg.cc/McFn0LX1)

El objetivo de este proyecto es potenciar el éxito de [Olist (E-commerce brasileña)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data) transformando los datos con acciones estratégicas como un análisis exhaustivo y el uso de herramientas avanzadas.

### Tabla de contenidos
- [Resumen ejecutivo](#resumen)
- [Introducción](#introducción)
- [Resultados logrados](#resultados)
- [Guía de Instalación](#guía)
- [Referencias](#referencias)
- [Licencia](#licencia)

## Resumen ejecutivo

Project Organization

    ├── LICENSE
    ├── tasks.py           <- Invoke with commands like `notebook`.
    ├── README.md          <- The top-level README for developers using this project.
    ├── install.md         <- Detailed instructions to set up this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries.
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures         <- Generated graphics and figures to be used in reporting.
    │
    ├── environment.yml    <- The requirements file for reproducing the analysis environment.
    │
    ├── .here              <- File that will stop the search if none of the other criteria
    │                         apply when searching head of project.
    │
    ├── setup.py           <- Makes project pip installable (pip install -e .)
    │                         so e_commerce_project can be imported.
    │
    └── e_commerce_project               <- Source code for use in this project.
        ├── __init__.py    <- Makes e_commerce_project a Python module.
        │
        ├── data           <- Scripts to download or generate data.
        │   └── make_dataset.py
        │
        ├── features       <- Scripts to turn raw data into features for modeling.
        │   └── build_features.py
        │
        ├── models         <- Scripts to train models and then use trained models to make
        │   │                 predictions.
        │   ├── predict_model.py
        │   └── train_model.py
        │
        ├── utils          <- Scripts to help with common tasks.
            └── paths.py   <- Helper functions to relative file referencing across project.
        │
        └── visualization  <- Scripts to create exploratory and results oriented visualizations.
            └── visualize.py


## Introducción
Para lograr el objetivo planeado, seguimos el siguiente roadmap:


[![estructura.png](https://i.postimg.cc/26CPh6Qk/estructura.png)](https://postimg.cc/t1mSH9vw)

- **Problema del negocio**: El dataset esta fragmentado, presentan defectos como valores NaN, requeriere un análisis exploratorio para comprender los datos y trazar algunos gráficos para aclarar los conceptos y obtener información útil. Requiere un analisis predictivo usando ML y una segmentación de clientes para desarrollar mejores estrategias de Marketing.

- **ETL**: Se hace la "Extracción de los datos" del dataset en Kaggle. Se "Transforman los datos" para que sean más adecuados para el análisis (Preprocesamiento y un merge para obetener solo un dataset). Se "cargan los datos" en la base de datos de MySQL para posteriormente usarlos en PowerBI.

- **EDA**: Se hace un análisis exploratorio de datos usando graficas y visualizaciones tanto en el Notebook como en PowerBI, para explorar el dataset final (con el merging).  

- **Preparación de los datos**: Se crea una copia y se filtran los valores numéricos del dataset, se crea una matriz de covarianza para evidenciar las columnas con mayor relación entre sí, se separan los datos por grupos de entrenamiento (80%) y grupos de validación (20%), se estandarizan las caracteristicas numéricas de ambos grupos de datos.

- **Entrenamiento de modelos**: Se crea un modelo de aprendizaje "No Supervisado" usando agrupamiento(Clustering) con la tecnica RFM y el algoritmo K-means, haciendo una división por grupos de clientes con caracteristicas similares. Se crean 4 modelos de aprendizaje "Supervisado" usando el problema de clasificación con los algoritmos de Red Neuronal, XGBoost, Regresión Lineal, Regresor de bosque aleatorio (Random Forest). Esto con el fin de predecir el precio de los productos.

- **Evaluación de modelos**: Se hace la evaluación de los modelos utilizando el conjunto de datos validación o prueba. La evaluación del modelo proporciona una estimación del rendimiento del modelo en datos no vistos, lo que ayuda a determinar cómo se generaliza el modelo a nuevos datos.

- **Validación de modelos**: Durante la validación de los modelos, se ajustan los hiperparámetros y se evalúa su rendimiento. El propósito es ajustar los hiperparámetros del modelo para obtener el mejor rendimiento posible en los datos de entrenamiento y validación.


### Contexto del dataset:

[![arquitectura.png](https://i.postimg.cc/RZhMjgy1/arquitectura.png)](https://postimg.cc/3kM5GFKW)

El conjunto de datos tiene información de 100.000 pedidos de 2016 a 2018 realizados en múltiples mercados de Brasil. 

Sus características permiten ver un pedido desde múltiples dimensiones: desde el estado del pedido, el precio, el pago y el rendimiento del flete hasta la ubicación del cliente, los atributos del producto y finalmente las reseñas escritas por los clientes. También tiene un conjunto de datos de geolocalización que relaciona los códigos postales con las coordenadas de latitud/longitud.

Se trata de datos comerciales reales, se han puesto en anonimos y las referencias a las empresas y socios en el texto de la reseña se han sustituido por los nombres de las grandes casas de "Juego de Tronos"(Serie de TV).

## Resultados logrados

- [x]  Se obtuvo el dataset final **olist_df** en la etapa "Procesamiento de datos(Feature Engineer)" con el que se realizará todo:
[![dataset-final.png](https://i.postimg.cc/JhvTxhCV/dataset-final.png)](https://postimg.cc/qtcXM47j)
- [x]  Se hizo el analisis del dataset con varias graficas que describen información importante:
[![graficas.png](https://i.postimg.cc/yddyMgcr/graficas.png)](https://postimg.cc/bG7nbv6Q)
- [x]  Se obtuvo la división por grupos de clientes con caracteristicas similares con el modelo de aprendizaje "No Supervisado" usando agrupamiento(Clustering) con la tecnica RFM y el algoritmo K-means:
[![kmeans.png](https://i.postimg.cc/rs6XzkVc/kmeans.png)](https://postimg.cc/JDQddSHd)
- [x]  Para predecir el precio del producto se hizo 4 modelos de aprendizaje "Supervisado" usando el problema de clasificación con los algoritmos de Red Neuronal, XGBoost, Regresión Lineal, Regresor de bosque aleatorio (Random Forest). Se selecciona el mejor según sus resultados, en este caso puede ser la red neuronal o el Regresor de bosque aleatorio:
[![modelpredict.png](https://i.postimg.cc/0jfs44vs/modelpredict.png)](https://postimg.cc/7JfdGmbs)

## Guía de Instalación

Lea [install.md](install.md) para obtener detalles sobre cómo configurar este proyecto.

## Referencias

Olist, and André Sionek. (2018). Brazilian E-Commerce Public Dataset by Olist [Data set]. Kaggle. https://doi.org/10.34740/KAGGLE/DSV/195341

## Licencia

Se publica bajo la licencia MIT. Consulte el archivo [LICENSE](/LICENSE) para obtener más detalles.
