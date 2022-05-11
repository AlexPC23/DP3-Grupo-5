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

## 1. Ingesta y procesado 

## 2. Transformación del input

### Clustering

### PCA

### Feature Importance

## 3. Entrenamiento y modelo final 

## 4. Predicción de test
