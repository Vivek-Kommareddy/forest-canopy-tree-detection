# 🌿 Quantifying Forest Canopy: A Drone-Assisted Approach to Tree Counting

> Automated tree detection and counting in regional landscapes using drone imagery and computer vision.

**🔗 Complete Info in this URL → [Research Findings Webpage](https://canopyvivek.netlify.app/)**

---

## Overview

Traditional tree counting methods are slow, labor-intensive, and prone to human error — especially across large or difficult terrain. This project presents an automated pipeline that processes high-resolution drone aerial images to detect and count individual tree crowns with **95% accuracy**, using classical computer vision techniques implemented in Python and OpenCV.

The system was validated on two real-world datasets captured over campuses in Vijayawada, Andhra Pradesh, and ships with a fully functional GUI application accessible to non-technical field users.

---

## How It Works

The pipeline runs in four stages:

```
Drone Image (TIFF)
      ↓
Image Pre-processing   →  Grayscale conversion + Gaussian blur (noise reduction)
      ↓
Tree Detection         →  Canny edge detection + Morphological closing + Contour filtering (≥500px²)
      ↓
Tree Counting          →  Contour count = tree count
      ↓
GUI Output             →  tkinter interface displays result + intermediate images
```

---

## Results

Four algorithms were benchmarked on the same drone datasets:

| Algorithm | Trees Detected | Accuracy |
|---|---|---|
| ✅ **Canny Edge Detection** | 16 / 38 / 0 (3 test cases) | **95%** |
| Watershed Segmentation | 17 | 92% |
| Region-based Segmentation | 11 | 88% |
| Adaptive Thresholding | 12 | 80% |

**Canny Edge Detection was selected** as the final method — best accuracy, handles mixed scenes (trees + buildings + bare ground), and correctly returns 0 when no trees are present.

---

## Test Cases

| Test Case | Scene | Trees Detected |
|---|---|---|
| TC1 | Dense tree boundary along red-soil road | **16** |
| TC2 | Mixed campus scene — building rooftop + foliage | **38** |
| TC3 | Bare ground, no vegetation | **0** ✓ |

---

## Tech Stack

| Tool | Role |
|---|---|
| Python | Core language |
| OpenCV | Image processing — edge detection, morphology, contours |
| Tkinter | GUI application |
| GDAL | Segmenting large TIFF drone images into tiles |
| QGIS | Geospatial visualization and KML/shapefile export |
| ERDAS IMAGINE | Remote sensing preprocessing |
| Google Earth | On-ground tree distribution estimation |

---

## Key Techniques

- **Grayscale conversion** — weighted sum formula: `Gray = 0.299R + 0.587G + 0.114B`
- **Gaussian blur** — noise suppression before edge analysis
- **Canny edge detection** — multi-stage: gradient → non-max suppression → hysteresis thresholding
- **Morphological closing** — elliptical structuring element (7×7) to fill canopy gaps
- **Contour filtering** — area threshold of 500px² to reject noise and small artifacts

---

## About

**Vivek Kommareddy**
Computer Science & Engineering


*This is a government-affiliated academic research project. The original source code is not publicly available. This repository hosts the research portfolio and findings.*

---

## Applications

- 🌲 Forest inventory and deforestation monitoring
- 🏙️ Urban tree census and planning
- 🦎 Wildlife habitat assessment
- 🌾 Agricultural canopy analysis
- 🛰️ Environmental impact monitoring
