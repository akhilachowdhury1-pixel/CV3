# Image Filtering and Blurring — Spatial Domain

## Overview

This project implements and analyzes **spatial-domain image filtering** techniques for smoothing and blurring grayscale images. Different **averaging (Box Filter) kernels** of sizes **3×3, 5×5, 7×7, and 11×11** are applied to study their effect on image details and sharpness.

The filtering process is implemented using two approaches:

* **OpenCV** using `cv2.filter2D()`
* **NumPy** using manual matrix operations and nested loops

The project demonstrates the mathematical concept of **image convolution** and shows how increasing the kernel size progressively increases the smoothing effect.

---
  <img width="1031" height="989" alt="image" src="https://github.com/user-attachments/assets/08527e1a-b148-4426-a949-a72b7dc7aec1" />
  

## Aim

To implement and analyze the effect of various spatial filtering kernels (**3×3, 5×5, 7×7, and 11×11**) on grayscale images to achieve smoothing and blurring effects using both **OpenCV** and **NumPy-based matrix operations**.

---

## Theory

A **Box Filter**, also known as an **Averaging Filter**, replaces each pixel with the average value of its neighboring pixels.

For a 3×3 kernel, the averaging mask is:

```text
1/9 × | 1  1  1 |
      | 1  1  1 |
      | 1  1  1 |
```

For a general `N × N` averaging kernel:

```text
K(i,j) = 1 / N²
```

Each output pixel is calculated by multiplying the neighboring pixel values by the corresponding kernel values and summing the results.

---

## Kernel Sizes and Their Effects

| Kernel Size | Filtering Effect   | Image Appearance                 |
| ----------- | ------------------ | -------------------------------- |
| **3×3**     | Mild smoothing     | Most details are preserved       |
| **5×5**     | Moderate smoothing | Fine details begin to disappear  |
| **7×7**     | Strong smoothing   | Edges and textures become softer |
| **11×11**   | Heavy smoothing    | Significant loss of fine details |

As the **kernel size increases**, a larger neighborhood of pixels is averaged. Therefore, the image becomes progressively smoother and more blurred.

---

## Implementation

### 1. OpenCV Implementation

OpenCV provides the `cv2.filter2D()` function for performing 2D convolution efficiently.

```python
filtered_img = cv2.filter2D(image, -1, kernel)
```

Different kernels are generated according to the required kernel size and applied to the grayscale image.

---

### 2. Manual NumPy Implementation

To understand the underlying convolution process, the filtering operation is also implemented manually using NumPy.

The basic procedure is:

1. Select a pixel neighborhood according to the kernel size.
2. Extract the corresponding image window.
3. Multiply the image window with the kernel.
4. Calculate the sum of the resulting values.
5. Assign the result to the corresponding output pixel.
6. Repeat the process for the complete image.

This implementation demonstrates how spatial convolution works at the matrix level.

---

# Experimental Results

## Image 1 — Puppy

The original puppy image contains considerable **high-frequency information**, particularly in the fur texture and facial features.

![Puppy Filtering Results](https://github.com/user-attachments/assets/9b5d8534-af1c-4463-b724-bf7a6196dccc)

### Observations

* **3×3 Kernel:** Produces slight smoothing while preserving most of the fur texture.
* **5×5 Kernel:** Produces noticeable smoothing and reduces some fine details.
* **7×7 Kernel:** Produces stronger blur, causing features such as the eyes and nose to become less sharp.
* **11×11 Kernel:** Produces heavy smoothing and significantly reduces fine image details.

---

## Image 2 — Couple with Umbrella

The second image contains a complex background with **trees, leaves, and distinct edges** between the subjects and the background.

![Couple with Umbrella — 11×11 NumPy Filter](https://github.com/user-attachments/assets/0f3801d2-79e4-4383-aedb-5248593da217)

### Observations

The manually implemented **11×11 NumPy filter** produces a strong blurring effect.

The following changes can be observed:

* Fine leaves and background textures become less distinct.
* Sharp edges become smoother.
* The outlines of the subjects become more diffused.
* Small image details are significantly reduced.
* The overall image appears softer and smoother.

---

## Analysis

The experiment demonstrates the relationship between **kernel size and blur intensity**:

```text
Kernel Size ↑
      ↓
Larger Neighborhood
      ↓
More Pixels Averaged
      ↓
Fine Details ↓
      ↓
Blur Intensity ↑
```

Thus, a larger averaging kernel produces stronger smoothing because each output pixel is influenced by a larger number of neighboring pixels.

---

## Low-Pass Filtering

The Box Filter acts as a **low-pass filter**.

It reduces high-frequency components of an image, such as:

* Fine textures
* Noise
* Sharp transitions
* Small details

At the same time, low-frequency information such as broad regions and gradual intensity variations is retained.

---

## OpenCV vs. Manual NumPy Implementation

| Feature        | OpenCV           | Manual NumPy                 |
| -------------- | ---------------- | ---------------------------- |
| Implementation | High-level       | Low-level                    |
| Function       | `cv2.filter2D()` | Nested loops                 |
| Speed          | Faster           | Slower                       |
| Complexity     | Simple           | More computation             |
| Learning Value | Practical        | Helps understand convolution |
| Control        | Library-managed  | Full control over operations |

The OpenCV implementation is useful for efficient image processing, while the NumPy implementation provides a better understanding of the underlying mathematical operation.

---

## Conclusion

The project successfully demonstrates **spatial-domain image filtering and blurring** using both OpenCV and NumPy.

The experimental results show that increasing the kernel size from **3×3 to 11×11** progressively increases the smoothing effect and reduces high-frequency image details.

The observations confirm that:

* **3×3** → Mild blur
* **5×5** → Moderate blur
* **7×7** → Strong blur
* **11×11** → Heavy blur

Therefore, the experiment clearly illustrates the **low-pass filtering property of the averaging filter** and provides both a practical and mathematical understanding of **spatial convolution and image smoothing**.
