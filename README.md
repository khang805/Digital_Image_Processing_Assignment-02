# Manual Edge Detection: Canny vs. Marr-Hildreth

**Author:** M Abdurrahman Khan (22i-1148)  
**Course:** Digital Image Processing (DIP)  
**Assignment:** #02

## 📖 Overview

This project implements two fundamental edge detection algorithms—**Canny Edge Detector** and **Marr-Hildreth (Laplacian of Gaussian)**—completely from scratch using Python.

The primary goal is to understand the mathematical underpinnings of edge detection without relying on high-level library functions (like `cv2.Canny`). The project evaluates these manual implementations on a dataset of **200 images** by comparing the generated edge maps against ground truth data using quantitative metrics.

## 📂 Project Structure

The project is designed to process the dataset and automatically generate all analysis files into an `output/` directory.

```text
├── 22i-1148_DIP_A-02.ipynb   # Main Jupyter Notebook (Source Code)
├── Report.pdf                # Detailed project report
├── dataset/                  # Input Data
│   ├── images/               # Source images (.jpg/.png)
│   └── ground_truth/         # Ground truth binary maps (.mat)
├── output/                   # Generated Artifacts (Auto-created on run)
│   ├── detailed_results.csv  # Precision/Recall/F1 metrics for EVERY image
│   ├── metrics_comparison.png# Bar chart comparing average performance
│   ├── canny_edges/          # Generated Canny edge maps
│   ├── marr_hildreth_edges/  # Generated LoG edge maps
│   └── comparisons/          # Side-by-side visual comparisons
└── README.md
'''text

## Methodology
## Canny Edge Detector (Manual Implementation)

The Canny detector follows a multi-stage pipeline to detect true edges while minimizing noise:

1) Gaussian Smoothing
Reduce image noise using a Gaussian filter.

2) Gradient Computation
Compute horizontal and vertical gradients using Sobel operators.
Calculate gradient magnitude and direction.

3) Non-Maximum Suppression (NMS)
Thin edges to single-pixel width by suppressing non-maximal values.

4) Double Thresholding
Classify pixels as:

Strong edges
Weak edges
Non-edges

5) Edge Tracking by Hysteresis
Retain weak edges only if connected to strong edges to finalize the edge map.

## Marr–Hildreth (Laplacian of Gaussian – LoG)

This method detects edges by identifying zero-crossings in the second derivative:

1) LoG Filtering
Smooth the image and compute the second derivative using a Laplacian of Gaussian kernel.

2) Zero-Crossing Detection
Identify pixels where the filtered image changes sign (positive → negative or negative → positive), which correspond to edges.

## 📊 Evaluation & Results

The algorithms were tested on a dataset of 200 images.
For each image, Precision, Recall, and F1 Score were computed by comparing detected edges with the ground truth.

All per-image metrics are saved in:

output/detailed_results.csv

📈 Average Performance Summary
Metric	Canny Edge Detector	Marr-Hildreth (LoG)
Precision	0.3163	0.2982
Recall	  0.1470	0.6095
F1 Score	0.1766	0.3665

A visual comparison of average metrics is also generated:

output/metrics_comparison.png

## 🧠 Analysis
Canny Edge Detector

Produces thin and clean edges

Higher precision compared to recall

Conservative thresholding causes missed faint edges

Marr–Hildreth (LoG)

Achieves significantly higher recall (≈ 61%)

Detects most image features

More sensitive to noise, resulting in thicker edges

## 🛠️ Dependencies

Ensure the following Python libraries are installed:

pip install numpy opencv-python matplotlib pandas scipy tqdm

## 🚀 Usage Instructions
1️⃣ Prepare the Dataset

Place input images in:

dataset/images/

Place ground truth .mat files in:

dataset/ground_truth/

2️⃣ Run the Notebook

Open 22i-1148_DIP_A-02.ipynb using:

Jupyter Notebook

Google Colab

3️⃣ Execute All Cells

The notebook will:

Process all images

Generate edge maps

Compute evaluation metrics

Save all outputs automatically

4️⃣ View Results

Navigate to the output/ directory to access:

comparisons/ → Side-by-side visual comparisons

detailed_results.csv → Per-image performance metrics

metrics_comparison.png → Average metric comparison
