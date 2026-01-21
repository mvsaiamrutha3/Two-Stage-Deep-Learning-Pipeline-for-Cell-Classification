# Two-Stage Cell Classification Framework

This repository implements a **two-stage deep learning framework for cell classification**, designed to improve overall classification accuracy by breaking the problem into meaningful sub-tasks instead of performing direct end-to-end classification.

The approach first detects and classifies **individual cells**, followed by a **pole-level (half-cell) classification**, and then aggregates the results to infer the final cell-level class.

---

## Project Overview

Direct end-to-end cell classification achieved an initial accuracy of ~40%, indicating limitations in capturing subtle morphological variations using a single-stage approach.

To address this, a hierarchical two-stage pipeline was introduced, resulting in an average classification accuracy of ~70%, demonstrating a significant improvement in robustness and prediction quality.

**Two-Stage Pipeline**

1. **Stage 1 – Individual Cell Detection**

   * Detects individual cells using oriented bounding boxes.
   * Performs initial cell-level classification.
   * Trained using enhanced microscopy images.

<img width="317" height="326" alt="image" src="https://github.com/user-attachments/assets/60300701-54d4-4fdc-a192-833518e116bf" />


2. **Stage 2 – Half-Cell (Pole) Classification**

   * Each detected cell is split into two poles (half-cells).
   * Pole-level features are classified independently.
   * Pole predictions are combined to improve final cell classification.

<img width="317" height="337" alt="image" src="https://github.com/user-attachments/assets/53742126-1f58-4c2c-8bae-122e1c218a1f" />


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

