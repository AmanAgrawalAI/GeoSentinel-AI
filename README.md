# 🛰️ GeoSentinel AI
### Satellite-Based Flood Detection Using Sentinel-1 SAR Imagery and Deep Learning

![Project Status](https://img.shields.io/badge/Status-Research%20Prototype-blue)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-PyTorch-red)
![Architecture](https://img.shields.io/badge/Architecture-U--Net-orange)
![Domain](https://img.shields.io/badge/Domain-Remote%20Sensing-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 🌍 Project Overview

GeoSentinel AI is a deep learning-based satellite intelligence project designed to identify flood-affected regions using Sentinel-1 Synthetic Aperture Radar (SAR) imagery and U-Net semantic segmentation.

The project explores how satellite imagery and deep learning can support flood monitoring, environmental observation, and disaster assessment.

Unlike optical satellite imagery, Sentinel-1 SAR can provide useful observations even under cloudy conditions, making it valuable for flood-monitoring applications.

GeoSentinel AI uses a custom U-Net architecture implemented with PyTorch to perform pixel-level flood segmentation.

## 🎯 Project Objectives

- Detect flood-affected regions from Sentinel-1 SAR imagery.
- Apply deep learning to satellite image segmentation.
- Generate pixel-level flood prediction masks.
- Compare model predictions with ground-truth flood masks.
- Evaluate segmentation performance using IoU and pixel-level error analysis.
- Explore the potential of AI-assisted disaster monitoring.

## 🛰️ Dataset

**Dataset:** SEN1Floods11

The project uses Sentinel-1 SAR satellite imagery and corresponding flood annotations.

The dataset pipeline includes:

- Sentinel-1 VV and VH polarization imagery.
- Ground-truth flood masks.
- Image and mask matching.
- Data validation and missing-data checks.
- Invalid pixel handling using a validity mask.
- Image normalization and preprocessing.

Dataset access: [SEN1Floods11 Dataset](https://github.com/cloudtostreet/Sen1Floods11)

*The dataset must be obtained separately and configured according to the paths used in the training notebook.*

## 🧠 Model Architecture

**Model:** Custom U-Net  
**Framework:** PyTorch  
**Task:** Binary Semantic Segmentation

GeoSentinel AI uses a U-Net encoder-decoder architecture to identify flood regions at the pixel level.

### Model Configuration

| Component | Configuration |
|---|---|
| Architecture | U-Net |
| Input channels | 3 |
| Input data | VV, VH and validity mask |
| Output channels | 2 |
| Task | Binary segmentation |
| Loss function | Weighted CrossEntropyLoss |
| Optimizer | AdamW |
| Learning-rate strategy | Learning-rate scheduler |

### How It Works

1. Sentinel-1 satellite imagery is loaded and preprocessed.
2. VV and VH polarization channels are prepared.
3. A validity mask is incorporated into the model input.
4. The U-Net model extracts spatial features.
5. The decoder generates pixel-level segmentation predictions.
6. Predicted masks are compared with ground-truth annotations.

## ⚙️ Training Pipeline

The training notebook implements the following workflow:

1. Dataset loading and inspection.
2. Image-mask correspondence validation.
3. Missing and invalid pixel analysis.
4. Data preprocessing and normalization.
5. Custom PyTorch Dataset implementation.
6. DataLoader preparation.
7. U-Net model initialization.
8. Loss function and optimizer configuration.
9. Model training and validation.
10. Checkpoint saving and evaluation.
11. Prediction visualization and error analysis.

## 📊 Model Evaluation

The project evaluates segmentation predictions using pixel-level metrics.

The evaluation workflow includes:

- Intersection over Union (IoU).
- True Positives (TP).
- False Positives (FP).
- False Negatives (FN).
- Ground-truth versus prediction comparison.
- Pixel-level error visualization.

These metrics help analyze how effectively the model identifies flood regions and where its predictions differ from the reference masks.

**Note:** Individual sample IoU values can vary significantly depending on the flood distribution and difficulty of the test image. The visualizations show both successful and challenging predictions.

## 🖼️ Visual Results

GeoSentinel AI generates visual comparisons to inspect model behavior on satellite imagery.

### 1. Test Predictions and Error Maps

Compares Sentinel-1 imagery, ground-truth masks, model predictions, and pixel-level errors.

![Test Predictions and Error Maps]
<img width="786" height="1474" alt="sample_level_error_analysis" src="https://github.com/user-attachments/assets/7092efee-78b0-40d5-a8eb-2ca09c5527bc" />


### 2. Ground Truth vs Model Predictions

Visual comparison of reference flood masks and predicted segmentation outputs.

![Ground Truth vs Prediction]
<img width="1240" height="1234" alt="satellite_ground_truth_prediction_examples" src="https://github.com/user-attachments/assets/6ff9b4fb-6b06-4cee-9066-f0c935b44884" />

### 3.Selected_Flood_POsitive_sample
<img width="1226" height="1614" alt="selected_flood_positive_samples" src="https://github.com/user-attachments/assets/76dcce62-aa2a-4e52-9c8a-52a991890546" />

### 4. Sample-Level Error Analysis

Visualizes false positives, false negatives, and correctly detected flood pixels.

![Sample Error Analysis]
<img width="2750" height="1570" alt="test_predictions_error_maps" src="https://github.com/user-attachments/assets/744d9b40-c12b-4dfd-86bd-21f2a595722e" />


**Error Map Legend:**
- 🔵 Blue: False Negative (FN)
- 🔴 Red: False Positive (FP)
- 🟢 Green: True Positive (TP)

### 4. Selected Flood-Positive Samples

Examples of flood-positive satellite images and their corresponding segmentation predictions.

![Flood Positive Samples](images/flood_positive_samples.png)

*All visualizations are generated from the project's actual model evaluation outputs.*

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming |
| PyTorch | Deep learning framework |
| NumPy | Numerical operations |
| Pandas | Data handling |
| Matplotlib | Visualization |
| Jupyter Notebook | Development and experimentation |
| Sentinel-1 SAR | Satellite imagery |
| U-Net | Semantic segmentation |

## 📁 Project Structure

```text
GeoSentinel-AI/
│
├── README.md
├── geosentinel-ai.ipynb
├── project_metadata.json
├── requirements.txt
│
└── images/
    ├── test_predictions_error_maps.png
    ├── ground_truth_prediction_comparison.png
    ├── sample_level_error_analysis.png
    └── flood_positive_samples.png
```

**Main Files**

- `geosentinel-ai.ipynb` — Complete data preprocessing, model training, validation and evaluation workflow.
- `project_metadata.json` — Project and model metadata.
- `requirements.txt` — Python dependencies.
- `images/` — Model evaluation visualizations.

The trained model checkpoint is maintained separately from the main source files to avoid unnecessarily increasing the repository size.

## 🚀 Installation and Usage

### 1. Clone the Repository

```bash
git clone https://github.com/AmanAgrawalAI/GeoSentinel-AI.git
```

```bash
cd GeoSentinel-AI
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it:

**Windows**
```bash
venv\Scripts\activate
```

**Linux / macOS**
```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Dataset

Download the SEN1Floods11 dataset and configure the dataset paths according to the training notebook.

### 5. Open the Training Notebook

```bash
jupyter notebook geosentinel-ai.ipynb
```

Run the notebook cells sequentially to reproduce the preprocessing, training and evaluation workflow.

## 🔬 Research and Practical Applications

GeoSentinel AI explores potential applications in:

- Flood-affected area identification.
- Satellite-based environmental monitoring.
- Disaster assessment and response support.
- Remote sensing research.
- AI-assisted geographical analysis.

The project is an experimental research prototype and is not a validated operational flood-warning or emergency-response system.

## 🚧 Limitations

- Prediction quality depends on satellite image quality and ground-truth annotations.
- Small or sparse flood regions can be difficult to segment accurately.
- SAR imagery may contain noise and complex surface patterns.
- Model generalization across different geographical regions requires further testing.
- Operational deployment would require additional validation and integration with real-world monitoring systems.

## 🔮 Future Improvements

- Improve segmentation performance on challenging flood samples.
- Explore advanced segmentation architectures.
- Expand geographical and environmental validation.
- Develop an interactive satellite flood-monitoring dashboard.
- Integrate geospatial visualization and mapping.
- Explore near-real-time satellite-based disaster analysis.

## 👨‍💻 Author

**Aman Kumar**  
Aspiring Data Scientist | AI/ML Engineer | Computer Vision Enthusiast

- [LinkedIn](https://www.linkedin.com/in/aman-kumar-788677378)
- [GitHub](https://github.com/AmanAgrawalAI)
- [Email](mailto:amanagrawal06922@gmail.com)

---

⭐ If you find this project interesting, consider giving the repository a star!

**GeoSentinel AI — Turning Satellite Imagery into Intelligent Flood Insights.** 🛰️🌍

