# Image Clustering with ResNet50 and K-Means

This project implements an image clustering system using features extracted by a pre-trained convolutional neural network (ResNet50) and the K-Means clustering algorithm. The code is designed to process a set of images, cluster them based on their visual content, and save the grouped images into separate folders.

## Table of Contents

1. [Overview](#overview)
2. [Requirements](#requirements)
3. [Code Structure](#code-structure)
4. [Main Functions](#main-functions)
5. [Usage](#usage)
6. [Possible Improvements](#possible-improvements)

## Overview

The script performs the following main tasks:

1. Extracts features from images using ResNet50.
2. Applies K-Means clustering to the extracted features.
3. Organizes images into folders based on their assigned clusters.

## Requirements

The code requires the following Python libraries:

- os
- shutil
- numpy
- PIL (Python Imaging Library)
- scikit-learn
- Keras
- TensorFlow (as the backend for Keras)

Ensure you have these libraries installed before running the script.

## Code Structure

The code is organized into several main functions:

1. `extract_features`: Extracts features from images.
2. `cluster_images`: Applies K-Means clustering to the features.
3. `save_clustered_images`: Saves the grouped images into folders.
4. `find_and_cluster_images`: Main function that orchestrates the entire process.

## Main Functions

### `extract_features(folder_path, model, input_shape=(224, 224))`

This function iterates through a directory of images and extracts features using a pre-trained model (ResNet50).

- **Parameters**:
  - `folder_path`: Path to the directory containing the images.
  - `model`: Pre-trained Keras model for feature extraction.
  - `input_shape`: Input size required by the model (default 224x224).

- **Returns**:
  - A NumPy array of extracted features.
  - A list of corresponding file paths.

### `cluster_images(features, n_clusters=5)`

Applies the K-Means algorithm to the extracted features to group the images.

- **Parameters**:
  - `features`: NumPy array of extracted features.
  - `n_clusters`: Number of clusters to form (default is 5).

- **Returns**:
  - Cluster labels assigned to each image.

### `save_clustered_images(labels, file_paths, output_folder)`

Saves the images into separate folders based on their cluster labels.

- **Parameters**:
  - `labels`: Cluster labels assigned to each image.
  - `file_paths`: List of file paths of the original images.
  - `output_folder`: Directory where the cluster folders will be saved.

### `find_and_cluster_images(input_folder, output_folder, n_clusters=5)`

Main function that coordinates the entire image clustering process.

- **Parameters**:
  - `input_folder`: Directory containing the input images.
  - `output_folder`: Directory where the results will be saved.
  - `n_clusters`: Number of clusters to form (default is 5).

## Usage

To use this script, simply define the input and output paths, and call the main function:

```python
input_folder = '/path/to/your/images/'
output_folder = '/path/for/results/'
find_and_cluster_images(input_folder, output_folder, n_clusters=7)
