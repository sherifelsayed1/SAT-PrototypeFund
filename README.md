# Satellite Data Gathering, Processing and training dataset creation for machine learning purposes 

## Overview
This repository contains two Jupyter notebooks demonstrating an end-to-end workflow for processing satellite images and training a machine learning model for crop segmentation. The workflow simplifies handling satellite data, allowing users to focus more on machine learning rather than complex data preprocessing.
The labels used for crops were downloaded from TUM Euro crops, a german dataset free to use and can be downloaded on a larger scale from https://github.com/maja601/EuroCrops

Ontop, we provide in the project a free platform that can be used by farmers to analyze their lands and check crop progress. That help farmers to rely on informed decison making in order to save resources like water and fertlizer: https://randomagri.users.earthengine.app/view/sat

Please see the attached video that shows how to use the platform in analyzing farms 
https://drive.google.com/file/d/169pWL_5dvvIMQo0FUFE_eBMibLp4aMb7/view?usp=sharing


## Notebooks

### 1. `Data_Gathering_Processing.ipynb`
This notebook is responsible for downloading and preparing Sentinel-1 and Sentinel-2 images for machine learning. It includes:

- **Downloading Data**: Retrieves satellite images from Google Earth Engine (GEE) for a specified region and time period.
- **Preprocessing**:
  - Ensures all image bands have the same resolution.
  - Combines images with crop labels for the same area.
  - Co-registers images to align them spatially.
- **Tiling**: Converts the processed images into smaller tiles suitable for deep learning.
- **Exporting**: Saves processed tiles as `.npy` files for use in training.

### 2. `Build_Model.ipynb`
This notebook trains a UNET-based deep learning model for segmenting corn fields using the preprocessed `.npy` data. It includes:

- **Loading Data**: Reads the tiled `.npy` files into memory.
- **Building UNET Model**: Defines and compiles a UNET architecture for semantic segmentation.
- **Training**: Trains the model using the prepared dataset.
- **Evaluation**: Tests the model’s performance on unseen data.
- **Visualization**: Displays prediction segmentation results for validation.

## Purpose
This project provides a streamlined pipeline for processing satellite images and creating labeled training datasets, making it easier to develop machine learning models for agricultural applications. By handling all major preprocessing steps, it reduces the struggle with data preparation, enabling users to focus on model training and optimization.

## Requirements
To run the notebooks, you will need:
- Python 3.8+
- Jupyter Notebook
- Google Earth Engine API
- TensorFlow/Keras
- NumPy, Pandas, Matplotlib
- OpenCV, Rasterio, Geopandas (for image processing)
- Google account required (for importing and exporting data via Google Drive)

## Usage
1. Run `Data_Gathering_Processing.ipynb` to download, preprocess, and save `.npy` training data to your google drive.
2. Run `Build_Model.ipynb` to import training data from google drive and train a UNET model on the prepared dataset.
3. Evaluate and refine the model as needed.


## Acknowledgments
Thanks to Google Earth Engine and Sentinel satellite programs for providing free access to satellite imagery.

