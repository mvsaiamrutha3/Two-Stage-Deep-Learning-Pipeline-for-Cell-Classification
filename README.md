# Two-Stage Cell Classification Framework

This repository implements a **two-stage deep learning framework for cell classification**, designed to improve overall classification accuracy by breaking the problem into meaningful sub-tasks instead of performing direct end-to-end classification.

The approach first detects and classifies **individual cells**, followed by a **pole-level (half-cell) classification**, and then aggregates the results to infer the final cell-level class.

---

## Project Overview

Traditional single-stage cell classification often struggles with complex cellular structures and subtle morphological differences.
This project addresses that limitation by introducing a **hierarchical classification pipeline**:

1. **Stage 1 – Individual Cell Detection & Classification**

   * Detects individual cells using oriented bounding boxes.
   * Performs initial cell-level classification.
   * Trained using enhanced microscopy images.

2. **Stage 2 – Half-Cell (Pole) Classification**

   * Each detected cell is split into two poles (half-cells).
   * Pole-level features are classified independently.
   * Pole predictions are combined to improve final cell classification.

This staged design improves robustness and accuracy compared to single-pass classification.

---

## Repository Structure

```
.
├── Individual_cell_train.ipynb
│   - Training notebook for individual cell detection and classification
│
├── Half_Cell_Pole_Classification.ipynb
│   - Pole (half-cell) extraction and classification logic
│
├── Cell Classification.ipynb
│   - End-to-end pipeline combining both stages for final prediction
│
└── README.md
```

---

## Data Preprocessing

* Microscopy images are enhanced using:

  * **Gamma correction**
  * **CLAHE (Contrast Limited Adaptive Histogram Equalization)**
* Oriented bounding boxes (OBB) are used to better capture cell orientation and morphology.
* Pole regions are extracted based on detected cell geometry.

---

## Models & Techniques

* **YOLO (OBB variant)** for cell detection
* Deep learning–based classifiers for:

  * Individual cells
  * Cell poles (half-cells)
* Modular pipeline enabling independent evaluation of each stage

---

## Key Highlights

* Two-level classification strategy for improved accuracy
* Robust handling of oriented and elongated cell structures
* Modular notebooks for training, evaluation, and inference
* Easily extendable to other microscopy datasets

---

## Usage

Run the notebooks in the following order:

1. `Individual_cell_train.ipynb`
2. `Half_Cell_Pole_Classification.ipynb`
3. `Cell Classification.ipynb`

Each notebook is self-contained and includes required preprocessing and evaluation steps.

---

## Future Improvements

* Automating pole aggregation strategies
* Cross-dataset generalization experiments
* Integration with real-time inference pipelines

---

## Author

Developed as part of an academic research project as a student research assistant focused on **biological image analysis and multi-stage deep learning pipelines**.

---

