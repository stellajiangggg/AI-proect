## Project Overview & Objectives

### 1.Overview
This project aims to demonstrate how **Sentinel-2** satellite data can be combined with external labeled datasets—such as **MODIS LAI** (for continuous leaf area index values) or **CORINE Land Cover** (for discrete classes)—to perform advanced **machine learning** tasks in Earth observation. By leveraging **Python** libraries (e.g., `rasterio`, `scikit-learn`), we develop an end-to-end workflow:

- **Ingest & preprocess** raw Sentinel-2 imagery.
- **Compute spectral indices** (e.g., NDVI, NDWI) to enhance feature separability.
- **Align** external label data (MODIS or CORINE) to the Sentinel-2 grid.
- **Train & evaluate** ML models (e.g., Random Forest, Gaussian Processes) for classification or regression.
- **Explain results** using XAI techniques (SHAP), and **assess environmental cost**.

### Objectives
1. **Data Preprocessing**  
   - Read and subset Sentinel-2 bands using `rasterio`, handle large tiles by cropping or window sampling.  
   - Compute key indices (NDVI, NDWI) to distinguish vegetation and water.

2. **Label Integration**  
   - Acquire and align **MODIS LAI** for continuous regression tasks, or **CORINE** data for discrete land cover classification.  
   - Ensure both label data and Sentinel-2 are reprojected to the same coordinate system.

3. **Machine Learning Implementation**  
   - **Unsupervised Approach**: K-Means clustering for an initial look at spectral groupings.  
   - **Supervised Approach**: RandomForest (and optionally GaussianProcesses) for classification or regression, using external ground truth.

4. **Result Visualization & XAI**  
   - Generate **classification maps** or **LAI predictions** over the chosen region ( part of Italy).  
   - Employ **SHAP** to interpret model feature importance and provide transparency.

5. **Environmental Impact Evaluation**  
   - Estimate computational resources (GPU/CPU hours), approximate energy usage, and propose strategies to reduce the carbon footprint.

Through this workflow, we illustrate a practical **AI4EO** pipeline that transforms raw satellite data into actionable insights , while highlighting best practices in data handling, machine learning, and environmental awareness.


## Step 2: Data Acquisition & Preprocessing

### 2.1 Data Location
All Sentinel-2 and auxiliary data (e.g., MODIS or CORINE) are stored in the following Google Drive folder:
[**Google Drive Link**](https://drive.google.com/drive/folders/1qrzCOUFN0HxSSXjxvkTllgiAwHWXsbrK?usp=sharing)

Within this folder, you'll find:
- **S2A_MSIL1C_...SAFE/**: Sentinel-2 L1C imagery (top-of-atmosphere).  
- **S2C_MSIL2A_...SAFE/**: Sentinel-2 L2A imagery (surface reflectance) and scene classification layers.  
- **Any other data**: e.g., partial downloads of MODIS LAI or CORINE land cover files.

> **Note**: Large `.SAFE` folders contain the `GRANULE` subfolder with `.jp2` band images, which we'll read directly from Colab.

### 2.2 Sentinel-2 Preprocessing
1. **Mount Google Drive** in Colab:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
### Note on Label Data
At this stage, we **do not yet have** the final ground-truth labels for:
- **\(y_{\text{all}}\)**: discrete classification labels (e.g., from CORINE or manual annotation), or
- **\(y_{\text{reg}}\)**: continuous variables (e.g., from MODIS LAI or other in situ measurements).

Therefore, our current code:
1. Uses **dummy labels** or random placeholders to demonstrate the Random Forest or Regression pipelines.
2. Leaves the integration of real label data as a future step once we finalize data downloads or sourcing.

**Next Steps** (once label data is obtained):
- **CORINE** or another land cover map can be aligned to form `y_all` for supervised classification.
- **MODIS LAI** or measured ground truths can be used to form `y_reg` for regression tasks.

