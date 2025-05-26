

## Project Overview & Objectives
<img width="499" alt="截屏2025-05-26 19 48 37" src="https://github.com/user-attachments/assets/52777800-2f24-4134-a59a-8010d755c0fe" />


# Mapping Water Bodies and Vegetation with Remote Sensing and Machine Learning

This project uses Sentinel-2 satellite imagery to classify land and water areas using remote sensing techniques and machine learning. We explore the difference between Level-1C (Top-of-Atmosphere) and Level-2A (Surface Reflectance) data, compute NDVI and NDWI indices, and apply clustering (K-Means) and supervised learning (Random Forest) to map features.

---
## Project Overview & Objectives
### 1. Problem Statement

Accurate mapping of surface water and vegetation is essential for land-use monitoring, environmental management, and climate research. This project compares atmospheric correction effects between L1C and L2A products using NDVI. It further explores water detection using NDWI, followed by clustering and classification using K-Means and Random Forest, trained on a NDWI-derived baseline.
#### 1.1 Problem Description

Accurate mapping of surface features such as vegetation and water bodies is essential for environmental monitoring, land-use planning, disaster response, and climate change studies. With the increasing availability of satellite data, especially from platforms like Sentinel-2, remote sensing has become a powerful tool for large-scale analysis.

This project addresses the challenge of distinguishing between water and land features in Sentinel-2 imagery using a combination of traditional remote sensing indices and machine learning techniques. Specifically, we:

- Assess the effect of atmospheric correction by comparing NDVI computed from Level-1C (top-of-atmosphere reflectance) and Level-2A (surface reflectance) Sentinel-2 products.
- Use NDWI (Normalized Difference Water Index) to identify water bodies and generate binary masks for supervised learning.
- Apply unsupervised K-Means clustering on both NDVI alone and a combined NDVI+NDWI feature space to segment the image into land cover classes.
- Train a supervised Random Forest classifier using raw spectral bands and derived indices, with the NDWI mask as a pseudo ground-truth.
- Visualize the separability of land and water features using PCA and UMAP dimensionality reduction techniques.

The ultimate goal is to evaluate how well machine learning can replicate or improve upon traditional index-based water detection in remote sensing workflows.

---

### 2. Data Location

All Sentinel-2 and auxiliary data (e.g., MODIS or CORINE) are stored in the following Google Drive folder:

**[[Google Drive Link]](https://drive.google.com/drive/folders/1qrzCOUFN0HxSSXjxvkTllgiAwHWXsbrK?usp=sharing)**

Folders include:
- `S2A_MSIL1C_...SAFE/`: Sentinel-2 L1C imagery (top-of-atmosphere)
- `S2C_MSIL2A_...SAFE/`: Sentinel-2 L2A imagery (surface reflectance)
- Any other optional auxiliary datasets (e.g., MODIS, CORINE)

Note: Within each `.SAFE` folder, `GRANULE` contains `.jp2` band images, which are loaded directly into Colab.

---

### 3. How to Run (on Google Colab)

1. Mount your Google Drive in Colab:
```python
from google.colab import drive
drive.mount('/content/drive')



## 2. Methodology Diagrams (Remote Sensing and AI Implementation)

To fulfill the requirement of illustrating both the remote sensing techniques and the AI pipeline used in this project, the following diagrams provide a clear visual summary.

---

### **Figure 1: NDWI vs. K-Means Classification Flow**

<img width="499" alt="截屏2025-05-26 19 48 37" src="https://github.com/user-attachments/assets/52777800-2f24-4134-a59a-8010d755c0fe" />

This flowchart represents the core comparison of two approaches to surface water detection:

- **Left branch (Remote Sensing)**: NDWI (Normalized Difference Water Index) is thresholded at 0 to generate a binary water vs. land mask, based on established hydrological interpretation.
  
- **Right branch (AI Clustering)**: NDVI and NDWI images are used as input to a K-Means clustering model (unsupervised machine learning). The resulting clusters are manually mapped to water or land classes based on color inspection or NDWI magnitude.

Both approaches lead to the same evaluation step: a **confusion matrix, accuracy score, and classification report** comparing the AI output with the NDWI-derived “truth.” The result is visualized as side-by-side classification maps.

---

### **Figure 2: Full Remote Sensing + AI Pipeline**
<img width="499" alt="截屏2025-05-26 19 48 37" src="https://github.com/user-attachments/assets/31f7645c-971a-49af-8e11-153af2a8ae07" />

This more detailed diagram presents the complete flow of the project from start to finish:

- **Data Input**: Sentinel-2 Level-2A and Level-1C bands (B02, B04, B08).
  
- **Index Calculation**:
  - NDVI from B08 and B04 (vegetation indicator).
  - NDWI from B02 and B08 (water indicator).
  - NDVI differences between L1C and L2A are also assessed to analyze atmospheric correction effects.

- **Masking and Clustering**:
  - Binary water masks are created by thresholding NDWI.
  - K-Means clustering is performed on both NDVI and NDWI, with clusters manually labeled.

- **Supervised Learning**:
  - Random Forest is trained using features: [B02, B04, B08, NDVI, NDWI].
  - NDWI mask is used as a pseudo-ground-truth for labels.

- **Evaluation and Output**:
  - Confusion matrices and accuracy scores are computed.
  - Visual maps are produced to compare predicted vs baseline classifications.

---

These figures together illustrate the integration of traditional remote sensing indices and modern machine learning methods in a practical, scalable geospatial classification pipeline.
