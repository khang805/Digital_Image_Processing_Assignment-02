## Manual Edge Detection: Canny vs. Marr-Hildreth

Author: M Abdurrahman Khan
Roll No: 22i-1148
Course: Digital Image Processing (DIP)
Assignment: #02

## 📖 Overview

This project presents manual implementations of two classical edge detection algorithms:

1) Canny Edge Detector

2) Marr–Hildreth (Laplacian of Gaussian – LoG)

Both algorithms are implemented from scratch in Python, without using high-level edge detection functions such as cv2.Canny. The purpose of this assignment is to develop a deep understanding of the mathematical and algorithmic foundations of edge detection techniques.

The implementations are evaluated on a dataset of 200 images, and their outputs are quantitatively compared against provided ground truth edge maps using standard performance metrics.

## 📂 Project Structure

All outputs are generated automatically when the notebook is executed.

├── 22i-1148_DIP_A-02.ipynb      # Main Jupyter Notebook (Source Code)
├── Report.pdf                  # Detailed project report
├── dataset/                    # Input dataset
│   ├── images/                 # Input images (.jpg / .png)
│   └── ground_truth/           # Ground truth edge maps (.mat)
├── output/                     # Auto-generated outputs
│   ├── detailed_results.csv    # Precision, Recall, F1 for each image
│   ├── metrics_comparison.png  # Average performance comparison plot
│   ├── canny_edges/            # Generated Canny edge maps
│   ├── marr_hildreth_edges/    # Generated LoG edge maps
│   └── comparisons/            # Side-by-side visual comparisons
└── README.md

## ⚙️ Methodology
## 1️⃣ Canny Edge Detector (Manual Implementation)

The Canny algorithm follows a multi-stage pipeline to detect edges accurately while minimizing noise:

Gaussian Smoothing

Reduces image noise using a Gaussian kernel.

Gradient Computation

Uses Sobel operators to compute horizontal and vertical gradients

Gradient magnitude and direction are calculated.

Non-Maximum Suppression (NMS)

Thins edges to a single-pixel width by suppressing non-maximal values.

Double Thresholding

Pixels are classified as:

Strong edges

Weak edges

Non-edges

Edge Tracking by Hysteresis:

Weak edges are retained only if connected to strong edges.

## 2️⃣ Marr–Hildreth (Laplacian of Gaussian – LoG)

This method detects edges by identifying zero-crossings in the second derivative of the image.

LoG Kernel Convolution

The image is smoothed and differentiated using a Laplacian of Gaussian kernel.

Zero-Crossing Detection

Edge points are detected where pixel values change sign
(positive → negative or negative → positive).

## 📊 Evaluation & Results

The algorithms were tested on a dataset of 200 images.
For each image, Precision, Recall, and F1 Score were computed by comparing detected edges with the ground truth.

All per-image metrics are saved in:

output/detailed_results.csv

📈 Average Performance Summary
Metric	Canny Edge Detector	Marr-Hildreth (LoG)
Precision	0.3163	0.2982
Recall	0.1470	0.6095
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
