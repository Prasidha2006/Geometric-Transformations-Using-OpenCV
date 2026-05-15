# Geometric Transformations Using OpenCV


---

# Developed By

**Name:** PRASIDHA A

**Register Number:** 212224230204

---


## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation
- Image Scaling
- Image Shearing
- Image Reflection
- Image Rotation

---

# Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

---

# Algorithm

## Step 1
Import the required libraries: OpenCV, NumPy, and Matplotlib.

## Step 2
Read the input image in color mode.

## Step 3: Image Translation
- Create a translation matrix
- Move the image 50 pixels right and 80 pixels down
- Apply transformation using `cv2.warpAffine()`
- Display original and translated images

## Step 4: Image Scaling
- Resize the image to 0.5×
- Resize the image to 2×
- Use `cv2.resize()`
- Display original, downscaled, and upscaled images

## Step 5: Image Shearing
- Apply horizontal shearing
- Apply vertical shearing
- Display sheared images

## Step 6: Image Reflection
- Apply horizontal reflection
- Apply vertical reflection
- Apply both-axis reflection
- Display reflected images

## Step 7: Image Rotation
- Rotate image by 45°
- Rotate image by 90°
- Display rotated images

---

# Program

```python
# Import Required Libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread('image.jpg')

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Get image dimensions
rows, cols = img.shape[:2]

# =====================================================
# IMAGE TRANSLATION
# =====================================================

tx = 50
ty = 80

translation_matrix = np.float32([
    [1, 0, tx],
    [0, 1, ty]
])

translated_img = cv2.warpAffine(
    img_rgb,
    translation_matrix,
    (cols, rows)
)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated_img)
plt.title("Translated Image")
plt.axis("off")

plt.show()

# =====================================================
# IMAGE SCALING
# =====================================================

downscaled_img = cv2.resize(
    img_rgb,
    None,
    fx=0.5,
    fy=0.5
)

upscaled_img = cv2.resize(
    img_rgb,
    None,
    fx=2,
    fy=2
)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled_img)
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled_img)
plt.title("Upscaled Image")
plt.axis("off")

plt.show()

# =====================================================
# IMAGE SHEARING
# =====================================================

horizontal_shear = np.float32([
    [1, 0.5, 0],
    [0, 1, 0]
])

vertical_shear = np.float32([
    [1, 0, 0],
    [0.5, 1, 0]
])

horizontal_sheared = cv2.warpAffine(
    img_rgb,
    horizontal_shear,
    (int(cols*1.5), rows)
)

vertical_sheared = cv2.warpAffine(
    img_rgb,
    vertical_shear,
    (cols, int(rows*1.5))
)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal_sheared)
plt.title("Horizontally Sheared")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical_sheared)
plt.title("Vertically Sheared")
plt.axis("off")

plt.show()

# =====================================================
# IMAGE REFLECTION
# =====================================================

horizontal_flip = cv2.flip(img_rgb, 1)

vertical_flip = cv2.flip(img_rgb, 0)

both_flip = cv2.flip(img_rgb, -1)

plt.figure(figsize=(10,10))

plt.subplot(2,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.imshow(horizontal_flip)
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2,2,3)
plt.imshow(vertical_flip)
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2,2,4)
plt.imshow(both_flip)
plt.title("Both-axis Reflection")
plt.axis("off")

plt.show()

# =====================================================
# IMAGE ROTATION
# =====================================================

rotation_matrix_45 = cv2.getRotationMatrix2D(
    (cols/2, rows/2),
    45,
    1
)

rotated_45 = cv2.warpAffine(
    img_rgb,
    rotation_matrix_45,
    (cols, rows)
)

rotation_matrix_90 = cv2.getRotationMatrix2D(
    (cols/2, rows/2),
    90,
    1
)

rotated_90 = cv2.warpAffine(
    img_rgb,
    rotation_matrix_90,
    (cols, rows)
)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotated_45)
plt.title("45 Degree Rotated Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotated_90)
plt.title("90 Degree Rotated Image")
plt.axis("off")

plt.show()
```

# Output

## 1. Image Translation

### Output:

<img width="1421" height="478" alt="image" src="https://github.com/user-attachments/assets/959be9dd-62f4-498c-ac0f-3d981f756a39" />

---

## 2. Image Scaling

### Output:

<img width="1808" height="432" alt="image" src="https://github.com/user-attachments/assets/ce6a525a-541f-44b6-9b8f-f4ba36a09865" />

---

## 3. Image Shearing

### Output:

<img width="1797" height="557" alt="image" src="https://github.com/user-attachments/assets/f390b11e-9817-42f2-9125-56df83077282" />

---

## 4. Image Reflection

### Output:

<img width="1073" height="909" alt="image" src="https://github.com/user-attachments/assets/c3763df2-9242-4fb2-abce-d03fa21bbc92" />

---

## 5. Image Rotation

### Output:

<img width="1867" height="406" alt="image" src="https://github.com/user-attachments/assets/4e1ee2d5-2a1c-4334-92d5-48c997879eb4" />

---

# Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV.

