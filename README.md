# Edge Detection Using OpenCV

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

**Step 1:** Import all the necessary modules for the program.

**Step 2:** Load an image using `cv2.imread()`.

**Step 3:** Convert the image to grayscale.

**Step 4:** Apply the Sobel operator using OpenCV to detect edges.

**Step 5:** Apply the Prewitt operator using custom kernels.

**Step 6:** Apply the Roberts operator using custom kernels.

**Step 7:** Apply the Laplacian operator using OpenCV.

**Step 8:** Apply the Canny edge detector using OpenCV.

**Step 9:** Display all edge-detected images for comparison.

## Python Program
### Developed by
#### NAME : MADHUMITHA R R
#### REG NO : 212224240083
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load input image
image = cv2.imread("spider.png")

# Convert image to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Sobel Edge Detection
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.magnitude(sobel_x, sobel_y)

# Prewitt Edge Detection
kernel_x = np.array([[-1, 0, 1],
                     [-1, 0, 1],
                     [-1, 0, 1]])

kernel_y = np.array([[-1, -1, -1],
                     [0, 0, 0],
                     [1, 1, 1]])

prewitt_x = cv2.filter2D(gray, cv2.CV_32F, kernel_x)
prewitt_y = cv2.filter2D(gray, cv2.CV_32F, kernel_y)
prewitt = cv2.magnitude(prewitt_x, prewitt_y)

# Roberts Edge Detection
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

roberts_x_result = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
roberts_y_result = cv2.filter2D(gray, cv2.CV_32F, roberts_y)
roberts = cv2.magnitude(roberts_x_result, roberts_y_result)

# Laplacian Edge Detection
laplacian = cv2.Laplacian(gray, cv2.CV_64F)

# Canny Edge Detection
canny = cv2.Canny(gray, 100, 200)

# Display all results
images = [gray, sobel, prewitt, roberts, laplacian, canny]
titles = ["Original Grayscale", "Sobel", "Prewitt",
          "Roberts", "Laplacian", "Canny"]

plt.figure(figsize=(12, 8))

for i in range(6):
    plt.subplot(2, 3, i + 1)
    plt.imshow(images[i], cmap="gray")
    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()
```

## Output

<img width="832" height="641" alt="image" src="https://github.com/user-attachments/assets/adc77b48-8bd9-4718-a51c-933e66aba7bb" />


## Result

Thus, edges were successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and image analysis.
