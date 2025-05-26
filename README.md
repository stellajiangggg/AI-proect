# AI-proect
Context & Motivation
Monitoring vegetation health and land cover is crucial for environmental management, agriculture, and climate studies. Satellite data, like Sentinel-2 (10 m resolution), provide high‐resolution reflectances, while MODIS LAI or CORINE Land Cover offer complementary labeled information. By integrating these datasets, we can train AI/ML models to perform tasks such as:

Land Cover Classification (urban, vegetation, water, etc.), or

Continuous Parameter Regression (predicting LAI or other vegetation indices).

Goals
Fetch & Preprocess Sentinel-2 L1C & L2A images for our study region in central Italy.

Compute Indices like NDVI, NDWI to enhance spectral separability.

Ingest an external labeled dataset:

CORINE for discrete land cover classes (y_all ), or

MODIS LAI for continuous “Leaf Area Index” (y_reg).

Train & Evaluate ML/AI methods:

Unsupervised K-Means,

RandomForest classification/regression,

Gaussian Process for advanced interpolation (optional),

Explainable AI (SHAP) to interpret model features.

Ultimately, we demonstrate how to create an end‐to‐end pipeline—from raw satellite data to final classification/regression maps.

2. Figure Illustrating the Technique (10%)
(Replace the text below with a real diagram if possible.)

<p align="center"> <img src="PATH_TO_YOUR_FLOWCHART.png" width="400" alt="Workflow Diagram"> </p>
Figure 1: Project Workflow

Data Ingestion: Sentinel‐2 imagery and external labeled data (CORINE or MODIS LAI).

Preprocessing: Cropping, resampling, index computations (NDVI, NDWI).

ML Model:

Classification (RandomForest, K-Means) for land cover.

Regression (RandomForest, GaussianProcess) for LAI.

Results: Final maps of land cover classes or LAI predictions.

XAI: Using SHAP to interpret feature importance.

