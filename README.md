# Grupo 5 - DP

- [Julen Aguirreurreta](https://www.linkedin.com/in/julen-aguirreurreta/)
- [Marta Castillo](https://www.linkedin.com/in/marta-castillo-garc%C3%ADa-041bb169/)
- [Olimpia Fuster](https://www.linkedin.com/in/olimpia-fuster/)
- [Alejandro Pérez](https://www.linkedin.com/in/alejandro-perez-casas/)
- [Miguel Ruiz](https://www.linkedin.com/in/miguel-ruiz-mic%C3%B3-222115213/)

## Evaluación del Riesgo Crediticio en una Entidad Bancaria

## Proyecto 

Bbank es un banco ético de reciente creación. Se trata de uno de los bancos más sostenibles del mundo. Hacen que el dinero trabaje para lograr un cambio social, ambiental y cultural positivo.

## ¿Qué nos solicita bbank? 

- Realizar un clustering para ver qué tipos de cliente tiene el banco.
- Crear un clasificador que indique si el préstamo es bueno o no.

## Introducción

Para poder reproducir la solución debes tener instalado Docker y Git.

Primero de todo, clonamos este repositorio:
```
git clone https://github.com/AlexPC23/DP3-Grupo-5
``` 
Una vez hayamos clonado el repositorio, accedemos a este y creamos un contenedor que será el que tenga el entorno Jupyter:
```
docker-compose up -d --build 
```
Con el contenedor ya en marcha, para acceder al entorno deberemos buscar la siguiente direccion:
```
http://localhost:10000/
``` 
A continuación nos pedira una contraseña o token para poder acceder. En este caso hemos especificado el token para el acceso en el archivo dokcer-compose que hemos creado y hemos puesto **dataproject**. Una vez escribamos el token ya nos deja acceder al los archivos subidos en el entorno

## Arquitectura de la solución

Primero de todo realizaremos una limpieza de los datos donde obtendremos dos sets:

- **total_merged_train.csv**: Conjunto de datos con el cual entrenaremos y testearemos los modelos.
- **total_merged_test.csv**:  Conjunto de datos sobre el que se realizará la clasificación.

Transformamos los datos de ambos sets con los notebooks de transformatiosn. En ellos, se realizará un análisis y se generarán datasets nuevos tanto para train como para test.

- **PCA3**
- **PCA6**
- **Cluster**
- **top_10_variables**
- **topfeats_coeff**

Posteriormente, comparamos todos los modelos y obtenemos aquel que cuente con la puntuación más alta. Con este modelo final realizaremos las predicciones sobre el conjunto de test correspondiente.

![arq](https://github.com/AlexPC23/DP3-Grupo-5/blob/main/arquitectura_dp3.svg)


## 1. Ingesta y procesado 

En primer lugar, para poder realizar cualquier tipo de análisis o clasificación debemos de preprocesar nuestros datos input. Contamos con tres datasets principales, los cuales a su vez se subdividen en entrenamiento y test:

* ***_datos_demograficos.csv** : Información sobre el cliente (edad, empleo, estudios, etc.).
* ***_performance.csv** : Conjunto de datos con préstamos a clasificar.
* ***_previous_loan.csv** : Préstamos históricos. 

A partir de estos datasets hemos realizado una limpieza en la cual hemos terminado tanto con el **total_merged_train** y el **total_merged_test**, los cuales utilizaremos más adelante.

## 2. Transformación del input

### Clustering

El objetivo es agrupar un conjunto de objetos en clustersr, es decir, grupos que sean similares entre ellos. Para ello se utilizará el metodo de partición k-means. 
En primer lugar se importan las librerias que aparecen en el notebook, en caso de no tenerlas es inprescindible descargarlas. 
El siguiente paso es cargar el dataset **"total_merged_train.csv"** para comenzar a trabajar.
Para averiguar el numero de clústeres para realizar k-means se realiza el método 'elbow' el cual mediante una gráfica nos indica cual es el numero de k mas óptimo (El punto donde mas varia la inclinación).
También utilizamos la Shiloutte Score para observar las puntuaciones de las "k's".
Una vez definido el número de k´s se aplica el método k-means el cual clasificara cada fila del dataset en uno de los dos clústeres definidos. 
Definidos ya, se añaden los clústeres al dataset.

### PCA

El ojetivo del PCA es el de simplificar la complejidad de espacios muestrales con muchas dimensiones a la vez que conserva su información.
Por esta misma razón utilizamos los PCA, con los cuales crearemos un dataset con las variables que mejor lo representen y el cual utilizaremos para hacer el modelo final.

### Feature Importance

El objetivo del feature importance es de encontrar las variables más importantes y posteriormente crear un dataset con esas variables, dataset el cual utilizaremos para hacer el modelo final.

## 3. Entrenamiento y modelo final 

Una vez que contamos con todos los inputs necesarios, pasaremos a entrenar los modelos y medir sus errores con el conjunto de validación.
Realizamos la búsqueda de hiperparámetros y entrenamos los modelos.

## 4. Predicción de test

Finalmente, tan sólo nos queda realizar la predicción final sobre el conjunto de test.
