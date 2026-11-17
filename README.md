# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** Narendhiran P  
- **Register No:**  212224230177

## Program
```py

import cv2
import numpy as np
import matplotlib.pyplot as plt
from google.colab import files

# Upload Image
uploaded = files.upload()

# Read Image
img = cv2.imread(list(uploaded.keys())[0])
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# 1. Averaging Filter
avg = cv2.blur(img, (5, 5))

# 2. Weighted Averaging Filter
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], dtype=np.float32) / 16

weighted = cv2.filter2D(img, -1, kernel)

# 3. Gaussian Filter
gaussian = cv2.GaussianBlur(img, (5, 5), 0)

# 4. Median Filter
median = cv2.medianBlur(img, 5)

# 5. Laplacian Sharpening using Kernel
lap_kernel = np.array([[0, -1, 0],
                       [-1, 5, -1],
                       [0, -1, 0]])

lap_sharp = cv2.filter2D(img, -1, lap_kernel)

# 6. Laplacian Operator
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)

lap = cv2.Laplacian(gray, cv2.CV_64F)
lap = cv2.convertScaleAbs(lap)

# Display All Results
images = [img, avg, weighted, gaussian,
          median, lap_sharp, lap]

titles = ["Original Image",
          "Averaging Filter",
          "Weighted Averaging Filter",
          "Gaussian Filter",
          "Median Filter",
          "Laplacian Kernel",
          "Laplacian Operator"]

plt.figure(figsize=(15, 10))

for i in range(7):
    plt.subplot(3, 3, i + 1)

    if i == 6:
        plt.imshow(images[i], cmap='gray')
    else:
        plt.imshow(images[i])

    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()

print("Image Smoothing and Sharpening Completed Successfully!")

```
---

##  Output

<img width="946" height="617" alt="image" src="https://github.com/user-attachments/assets/976d0e56-8a27-4f8a-92e2-c0879f7dca52" />


### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  

---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
