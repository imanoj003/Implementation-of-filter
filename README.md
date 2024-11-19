# Implementation-of-filter
### EXP : 5
### DATE : 23 / 9 / 24
## Aim:
To implement filters for smoothing and sharpening the images in the spatial domain.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step 1: 
Import necessary libraries (cv2, NumPy, Matplotlib) for image loading, filtering, and visualization.

### Step 2: 
Load the image using cv2.imread() and convert it to RGB format using cv2.cvtColor() for proper display in Matplotlib.

### Step 3: 
Apply different filters:
1. Averaging Filter: Define an averaging kernel using np.ones() and apply it to the image using cv2.filter2D().
2. Weighted Averaging Filter: Define a weighted kernel (e.g., 3x3 Gaussian-like) and apply it with cv2.filter2D().
3. Gaussian Filter: Use cv2.GaussianBlur() to apply Gaussian blur.
4. Median Filter: Use cv2.medianBlur() to reduce noise.
5. Laplacian Operator: Use cv2.Laplacian() to apply edge detection.
    
### Step 4: 
Display each filtered image using plt.subplot() and plt.imshow() for side-by-side comparison of the original and processed images.

### Step 5: 
Save or show the images using plt.show() after applying each filter to visualize the effects of smoothing and sharpening.

## Program:
#### Developed By   : MANOJ M
#### Register Number: 212221240027
```
import cv2
import matplotlib.pyplot as plt
import numpy as np
image1 = cv2.imread("dog.jpg")
image2 = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")
```

![Screenshot 2024-10-28 151132](https://github.com/user-attachments/assets/62ee21c7-7977-4084-9c06-7c475479dd29)

### 1. Smoothing Filters

i) Using Averaging Filter
```
kernel = np.ones((11, 11), np.float32) / 121
averaging_image = cv2.filter2D(image2, -1, kernel)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(averaging_image)
plt.title("Averaging Filter Image")
plt.axis("off")
plt.show()

```

![Screenshot 2024-10-28 151139](https://github.com/user-attachments/assets/e2a95562-56e5-4096-b433-523c853a8f34)



ii) Using Weighted Averaging Filter
```Python
kernel1 = np.array([[1, 2, 1],
                    [2, 4, 2],
                    [1, 2, 1]]) / 16

weighted_average_image = cv2.filter2D(image2, -1, kernel1)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(weighted_average_image)
plt.title("Weighted Average Filter Image")
plt.axis("off")
plt.show()

```
![Screenshot 2024-10-28 151146](https://github.com/user-attachments/assets/9031284c-2b3e-4a6c-b6c9-2f8812167522)



iii) Using Minimum Filter
```Python
min_filter = cv2.erode(image1, np.ones((5, 5), np.uint8))
min_filter_rgb = cv2.cvtColor(min_filter, cv2.COLOR_BGR2RGB)
plt.imshow(min_filter_rgb)
plt.title("Minimum Filter")
plt.show()
```
![Screenshot 2024-10-28 151151](https://github.com/user-attachments/assets/7b168593-4b95-4031-875c-0de529e5b78e)




iv) Using Maximum Filter
```
max_filter = cv2.dilate(image1, np.ones((5, 5), np.uint8))
max_filter_rgb = cv2.cvtColor(max_filter, cv2.COLOR_BGR2RGB)
plt.imshow(max_filter_rgb)
plt.title("Maximum Filter")
plt.show()
```



![Screenshot 2024-10-28 151157](https://github.com/user-attachments/assets/89de408d-5cea-4d7e-aeb1-6431cccb7d64)


v) Using Median Filter
```
median_filter = cv2.medianBlur(image1, 5)
median_filter_rgb = cv2.cvtColor(median_filter, cv2.COLOR_BGR2RGB)
plt.imshow(median_filter_rgb)
plt.title("Median Filter")
plt.show()
```


![Screenshot 2024-10-28 151202](https://github.com/user-attachments/assets/ebe8becd-d750-4101-af71-cf36a2cdfe22)



### 2. Sharpening Filters
i) Using Laplacian Linear Kernal
```
sharpened_image = cv2.filter2D(image1, -1, kernel1)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(sharpened_image)
plt.title("Sharpened Image (Laplacian Kernel)")
plt.axis("off")
plt.show()
```

![Screenshot 2024-10-28 151208](https://github.com/user-attachments/assets/67d7473a-8f83-40c3-99c9-b50198f831cc)




ii) Using Laplacian Operator
```
laplacian = cv2.Laplacian(image1, cv2.CV_64F)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Operator Image")
plt.axis("off")
plt.show()
```
![Screenshot 2024-10-28 151212](https://github.com/user-attachments/assets/9dc96e26-ee20-4508-ae9a-d0ada3add72a)



## Result:
Thus the filters are designed for smoothing and sharpening the images in the spatial domain.
