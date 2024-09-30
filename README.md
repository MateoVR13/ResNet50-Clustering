# Clustering de Imágenes con ResNet50 y K-Means

Este proyecto implementa un sistema de clustering de imágenes utilizando características extraídas por una red neuronal convolucional pre-entrenada (ResNet50) y el algoritmo de clustering K-Means. El código está diseñado para procesar un conjunto de imágenes, agruparlas en clusters basados en su contenido visual, y guardar las imágenes agrupadas en carpetas separadas.

## Contenido

1. [Descripción General](#descripción-general)
2. [Requisitos](#requisitos)
3. [Estructura del Código](#estructura-del-código)
4. [Funciones Principales](#funciones-principales)
5. [Uso](#uso)
6. [Posibles Mejoras](#posibles-mejoras)

## Descripción General

El script realiza las siguientes tareas principales:

1. Extrae características de las imágenes utilizando ResNet50.
2. Aplica clustering K-Means a las características extraídas.
3. Organiza las imágenes en carpetas basadas en los clusters asignados.

## Requisitos

El código requiere las siguientes bibliotecas de Python:

- os
- shutil
- numpy
- PIL (Python Imaging Library)
- scikit-learn
- Keras
- TensorFlow (como backend para Keras)

Asegúrate de tener estas bibliotecas instaladas antes de ejecutar el script.

## Estructura del Código

El código está organizado en varias funciones principales:

1. `extract_features`: Extrae características de las imágenes.
2. `cluster_images`: Aplica K-Means clustering a las características.
3. `save_clustered_images`: Guarda las imágenes agrupadas en carpetas.
4. `find_and_cluster_images`: Función principal que orquesta todo el proceso.

## Funciones Principales

### `extract_features(folder_path, model, input_shape=(224, 224))`

Esta función recorre un directorio de imágenes y extrae características utilizando un modelo pre-entrenado (ResNet50).

- **Parámetros**:
  - `folder_path`: Ruta al directorio que contiene las imágenes.
  - `model`: Modelo de Keras pre-entrenado para la extracción de características.
  - `input_shape`: Tamaño de entrada requerido por el modelo (por defecto 224x224).

- **Retorna**:
  - Un array NumPy con las características extraídas.
  - Una lista de rutas de archivos correspondientes.

### `cluster_images(features, n_clusters=5)`

Aplica el algoritmo K-Means a las características extraídas para agrupar las imágenes.

- **Parámetros**:
  - `features`: Array NumPy de características extraídas.
  - `n_clusters`: Número de clusters a formar (por defecto 5).

- **Retorna**:
  - Etiquetas de cluster asignadas a cada imagen.

### `save_clustered_images(labels, file_paths, output_folder)`

Guarda las imágenes en carpetas separadas basadas en sus etiquetas de cluster.

- **Parámetros**:
  - `labels`: Etiquetas de cluster asignadas a cada imagen.
  - `file_paths`: Lista de rutas de archivos de las imágenes originales.
  - `output_folder`: Directorio donde se guardarán las carpetas de clusters.

### `find_and_cluster_images(input_folder, output_folder, n_clusters=5)`

Función principal que coordina todo el proceso de clustering de imágenes.

- **Parámetros**:
  - `input_folder`: Directorio que contiene las imágenes de entrada.
  - `output_folder`: Directorio donde se guardarán los resultados.
  - `n_clusters`: Número de clusters a formar (por defecto 5).

## Uso

Para utilizar este script, simplemente define las rutas de entrada y salida, y llama a la función principal:

```python
input_folder = '/ruta/a/tus/imagenes/'
output_folder = '/ruta/para/resultados/'
find_and_cluster_images(input_folder, output_folder, n_clusters=7)
```
---

Este README proporciona una visión general del proyecto de clustering de imágenes. Para más detalles sobre la implementación, consulta los comentarios en el código fuente.
