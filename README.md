## Project Overview & Objectives

### Overview
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


