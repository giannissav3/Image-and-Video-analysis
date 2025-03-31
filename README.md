# Laplacian Pyramid Image Analysis – NTUA Assignment

This repository contains the implementation and experimentation of the **Laplacian Pyramid** technique for image representation and compression. It is based on the concepts introduced by Burt and Adelson (1983) and implemented as part of an NTUA undergraduate assignment.

---

## Description

The goal of the project is to:
- Implement Laplacian and Gaussian pyramids
- Perform reduction and expansion of images
- Reconstruct images from pyramid representations
- Analyze the behavior of the Laplacian pyramid using entropy metrics
- Apply quantization for compression
- Compare performance under different parameters

---

## Implemented Functions

The following core functions are implemented from scratch (without using OpenCV or SciPy pyramids):

- `GKernel(a)`: Generates a 5x5 separable Gaussian kernel parameterized by `a`
- `GREDUCE(I, h)`: Reduces image size by convolving with kernel `h` and subsampling
- `GPyramid(I, a, depth)`: Constructs the Gaussian pyramid
- `GEXPAND(I, h)`: Expands the image by upsampling and convolving with `h`
- `LPyramid(I, a, depth)`: Constructs the Laplacian pyramid
- `L_Pyramid_Decode(lpyr, a)`: Reconstructs image from Laplacian pyramid
- `L_Quantization(lpyr, bin_size)`: Quantizes Laplacian coefficients using a specified bin size

---

## Experiments

### ✅ Step 1: Reconstruction
Tested the `LPyramid` and `L_Pyramid_Decode` functions on grayscale (camera) and RGB (lena) images. Reconstruction quality is visually very close to the original.

### ✅ Step 2: Effect of Parameter `a`
We evaluated the impact of varying `a ∈ [0.3, 0.7]` on reconstruction quality. The best values were typically around `a = 0.5`.

### ✅ Step 3: Effect of Pyramid Depth
Depths from 3 to 6 were tested. Increasing depth has small visual impact on reconstruction but increases compression.

### ✅ Step 4: Entropy Analysis
We calculated Shannon entropy on the first Laplacian level for different `a` and `depth`. Entropy was minimized for `a ≈ 0.5–0.6`.

### ✅ Step 5: Optimal `a` per Level
We identified the `a` value that minimized entropy at each pyramid level. Results showed that `a = 0.5` is a good overall choice.

### ✅ Step 6: Quantization
We applied Laplacian coefficient quantization using two `bin_size` values (e.g. 10 and 30). Higher bin sizes led to stronger compression but lower visual quality.

---

## 📷 Test Images
- **Lena**: RGB image loaded from `lena.png`
- **Camera**: Grayscale image from `skimage.data`

---

## References
- Burt, P. J., & Adelson, E. H. (1983). *The Laplacian Pyramid as a Compact Image Code*. IEEE Transactions on Communications.

---

## Environment
- Python 3.x
- Google Colab
- Numpy, OpenCV, Matplotlib, Scikit-image

---

## ✍Author
This project was developed as part of coursework at NTUA, School of Electrical and Computer Engineering.
