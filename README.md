# low-light-image-enhancement
Comparative analysis of HE, CLAHE, and Gamma Correction for low-light image enhancement using PSNR, SSIM, and MSE metrics.
# Low-Light Image Enhancement — Comparative Analysis

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)](https://python.org)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?logo=opencv)](https://opencv.org)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)
[![Dataset](https://img.shields.io/badge/Dataset-LOL-orange)](https://daooshee.github.io/BMVC2018website/)

A comparative evaluation of three classical low-light image enhancement
methods benchmarked on the LOL dataset using reference-based image
quality metrics.

---

## Overview

Images captured under dim conditions suffer from low contrast, suppressed
detail, and elevated noise. This project benchmarks three classical
enhancement techniques — **Histogram Equalization (HE)**, **CLAHE**, and
**Gamma Correction** — against 20 paired test images from the LOL dataset,
evaluated using MSE, PSNR, and SSIM.

---

## Methods

| Method | Strategy | Complexity |
|---|---|---|
| Histogram Equalization | Global CDF-based redistribution | O(N) |
| CLAHE | Local tile equalization (8×8, clip=2.0) | O(N·tiles) |
| Gamma Correction (γ=0.7) | Power-law transform via 256-LUT | O(N) |

---

## Results Summary

| Method | Avg MSE ↓ | Avg PSNR (dB) ↑ | Avg SSIM ↑ |
|---|---|---|---|
| **Histogram EQ** | **107.11** | **27.84** | **0.369** |
| CLAHE | 107.06 | 27.84 | 0.321 |
| Gamma (γ=0.7) | 109.52 | 27.74 | 0.035 |

> **Key finding:** HE achieves the best average numerical scores. CLAHE
> outperforms HE on scenes with spatially uneven illumination (e.g.,
> image 179.png: CLAHE PSNR = 18.68 dB vs. HE PSNR = 9.53 dB).
> Gamma Correction produces smooth, artifact-free outputs but cannot
> adapt to local illumination variation.

---

## Repository Structure

```
low-light-enhancement/
├── notebook/
│   └── low_light_enhancement.ipynb   # Full pipeline + experiments
├── results/
│   ├── figures/                      # Bar charts, visual comparisons
│   └── per_image_metrics.csv         # Full 20-image metric table
├── report/
│   └── LowLight_Report_Final.pdf     # Course report
└── README.md
```

---

## Setup & Usage

```bash
# No local install required — designed for Google Colab
# 1. Upload notebook to Colab
# 2. Mount Google Drive and set dataset path:
#    /content/drive/MyDrive/lol_dataset/our485/

pip install opencv-python numpy matplotlib scikit-image
```

Run all cells in `notebook/low_light_enhancement.ipynb`.

---

## Dataset

[LOL (Low-Light) Dataset](https://daooshee.github.io/BMVC2018website/)
— 20 paired test images (low-light input + normal-light ground truth).
Scenes include indoor rooms, desks, and hallways captured under genuine
low-light conditions.

---

## Tech Stack

`Python` · `OpenCV` · `NumPy` · `Matplotlib` · `scikit-image` · `Google Colab`

---

## Authors

Raghad (169028) · Jana (173110) — AI375 Digital Image Processing
