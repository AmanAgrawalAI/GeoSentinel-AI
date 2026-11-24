# 🛰️ GeoSentinel AI
### Satellite-Based Flood Detection Using Sentinel-1 SAR Imagery and Deep Learning

GeoSentinel AI is a deep learning-based satellite intelligence project designed to detect flood-affected regions using Sentinel-1 Synthetic Aperture Radar (SAR) imagery and a U-Net semantic segmentation architecture.

The project demonstrates how satellite imagery and deep learning can support flood monitoring and disaster assessment, including situations where cloud cover limits the usefulness of optical satellite imagery.

---

## 🌍 Project Overview

Floods are among the most destructive natural disasters, causing significant damage to infrastructure, agriculture, and human settlements.

Traditional flood monitoring methods can be time-consuming and difficult to scale.

**GeoSentinel AI** explores an automated approach to flood detection by analyzing Sentinel-1 SAR satellite imagery and generating pixel-level flood segmentation predictions using a trained U-Net model.

## 🎯 Project Objectives

- Detect flood-affected regions from satellite imagery.
- Apply deep learning to remote sensing applications.
- Perform pixel-level semantic segmentation.
- Explore practical applications of AI in disaster monitoring.
- Build a foundation for future satellite-based disaster intelligence systems.

## 🧠 Model Architecture

The project uses a custom U-Net architecture implemented with PyTorch.

**Architecture Details:**

| Parameter | Configuration |
|---|---|
| Model | U-Net |
| Framework | PyTorch |
| Input Channels | 3 |
| Output Classes | 2 |
| Image Size | 512 × 512 |
| Training Epochs | 60 |
| Total Parameters | 7,766,018 |
| Optimizer | AdamW |
| Loss Function | Weighted Cross Entropy |

### Input Channels

The model receives three input channels:

1. Normalized VV polarization.
2. Normalized VH polarization.
3. Image validity mask.

The validity channel helps the model distinguish valid image pixels from invalid or missing image regions.

## 🛰️ Dataset

**Dataset:** Sen1Floods11

The project uses the hand-labeled portion of the Sen1Floods11 dataset.

The dataset contains Sentinel-1 SAR imagery and corresponding flood labels.

### Dataset Processing

- Original hand-labeled Sentinel-1 images: 446
- Original corresponding label images: 446
- Training samples: 252
- Validation samples: 86 usable images
- Testing samples: 89 usable images

Invalid images and samples with unusable labels were excluded during preprocessing.

### Data Preprocessing

- VV and VH polarization extraction.
- Training-set-based normalization.
- NaN and invalid-pixel handling.
- Flood and background label preparation.
- Ignoring invalid label pixels during training and evaluation.

## 📊 Model Performance

The trained model was evaluated on 89 test images.

### Test Results

| Evaluation Metric | Result |
|---|---:|
| Accuracy | 94.33% |
| Precision | 73.77% |
| Recall | 83.68% |
| Dice Score / F1 | 78.41% |
| Flood IoU | 64.49% |
| Background IoU | 93.68% |
| Mean IoU | 79.09% |
| Specificity | 95.83% |

### Performance Highlights

- Achieved 94.33% pixel-level accuracy.
- Achieved 83.68% flood detection recall.
- Achieved 64.49% Flood Intersection over Union.
- Demonstrated semantic segmentation capabilities on geographically diverse test imagery.

*Note: Mean IoU is calculated from the global two-class confusion matrix. It is different from the average per-image flood IoU.*

## 🛠️ Technologies Used

| Technology | Application |
|---|---|
| Python | Core programming |
| PyTorch | Deep learning framework |
| NumPy | Numerical computation |
| Pandas | Dataset management |
| Rasterio | Geospatial raster processing |
| Matplotlib | Visualization |
| Sentinel-1 SAR | Satellite imagery |

## 📁 Repository Structure

```text
GeoSentinel-AI/
│
├── geosentinel-ai.ipynb
│
├── project_metadata.json
│
├── README.md
│
└── Model Weights
    └── Available in GitHub Releases
```

## 🚀 Model Download

The trained model weights are available in the GitHub Releases section.

**Release:** v1.0.0

**Model File:** `best_model.pth`

The release also contains details about the model architecture and evaluation results.

## 🔬 Training and Implementation

The complete training and evaluation workflow is documented in the Jupyter Notebook:

`geosentinel-ai.ipynb`

The notebook covers:

- Dataset loading and exploration.
- Satellite image preprocessing.
- Data normalization.
- U-Net model implementation.
- Model training and validation.
- Performance evaluation.
- Model checkpoint saving.

## 🔮 Future Improvements

Potential future development includes:

- Real-time flood monitoring.
- Interactive flood segmentation maps.
- Integration with GIS platforms.
- Geographic flood-risk analysis.
- Building damage assessment using satellite imagery.
- Integration with additional satellite datasets.
- Automated disaster monitoring dashboards.

## ⚠️ Disclaimer

GeoSentinel AI is an experimental research and portfolio project.

Its predictions should not be considered a replacement for official disaster management systems, ground-based verification, or authoritative emergency information.

## 👨‍💻 Author

**Aman Kumar**

GitHub: [AmanAgrawalAI](https://github.com/AmanAgrawalAI)

---

⭐ If you find this project interesting, consider starring the repository.

**Built with Python, PyTorch, Deep Learning & Satellite Intelligence.**
