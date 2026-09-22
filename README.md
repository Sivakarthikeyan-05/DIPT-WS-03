# Canny Edge Detection

## Student Details

**Name:** Sivakarthikeyan V.
**Reg. No.:** 212225220098

---

## Aim

To implement the **Canny Edge Detection algorithm** on a sample image and analyse how different threshold parameter values affect the detected edges.

---

## Requirements

Install the required Python libraries:

```text
pip install opencv-python matplotlib
```

---

## Python Code

```python
# ============================================================
# IMPLEMENTATION OF CANNY EDGE DETECTION
# Name    : Sivakarthikeyan V.
# Reg No. : 212225220098
# ============================================================

import cv2
import matplotlib.pyplot as plt

# ============================================================
# STEP 1: READ THE IMAGE
# ============================================================

# Change "photo.jpg" to your image filename
image = cv2.imread("photo.jpg")

if image is None:
    raise FileNotFoundError(
        "Image not found! Put the image in the same folder "
        "as the Jupyter Notebook and check the filename."
    )

# Convert BGR image to RGB for displaying
imageRGB = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# ============================================================
# STEP 2: CONVERT IMAGE TO GRAYSCALE
# ============================================================

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# ============================================================
# STEP 3: APPLY GAUSSIAN BLUR
# ============================================================

# Gaussian blur reduces noise before edge detection
blur = cv2.GaussianBlur(
    gray,
    (5, 5),
    0
)

# ============================================================
# STEP 4: APPLY CANNY EDGE DETECTION
# ============================================================

# Different threshold values

edges1 = cv2.Canny(
    blur,
    50,
    100
)

edges2 = cv2.Canny(
    blur,
    100,
    200
)

edges3 = cv2.Canny(
    blur,
    150,
    250
)

# ============================================================
# STEP 5: DISPLAY ORIGINAL, GRAYSCALE AND BLURRED IMAGE
# ============================================================

plt.figure(figsize=(18, 6))

plt.subplot(1, 3, 1)
plt.imshow(imageRGB)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(gray, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(blur, cmap="gray")
plt.title("Gaussian Blurred Image")
plt.axis("off")

plt.tight_layout()
plt.show()

# ============================================================
# STEP 6: DISPLAY CANNY EDGE RESULTS
# ============================================================

plt.figure(figsize=(18, 6))

plt.subplot(1, 3, 1)
plt.imshow(edges1, cmap="gray")
plt.title("Canny Edges: Low=50, High=100")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(edges2, cmap="gray")
plt.title("Canny Edges: Low=100, High=200")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(edges3, cmap="gray")
plt.title("Canny Edges: Low=150, High=250")
plt.axis("off")

plt.tight_layout()
plt.show()

# ============================================================
# FINAL RESULT
# ============================================================

print("=" * 55)
print("CANNY EDGE DETECTION RESULTS")
print("=" * 55)

print("Parameter Set 1: Low Threshold = 50, High Threshold = 100")
print("Result: Detects more edges, including weak edges and noise.")

print("\nParameter Set 2: Low Threshold = 100, High Threshold = 200")
print("Result: Provides a balanced detection of strong and important edges.")

print("\nParameter Set 3: Low Threshold = 150, High Threshold = 250")
print("Result: Detects only strong edges and removes many weak edges.")

print("\nObservation:")
print("Lower threshold values produce more detected edges but may include noise.")
print("Higher threshold values produce fewer and stronger edges.")
print("Gaussian blur helps reduce noise before applying the Canny algorithm.")
```

---

## Canny Edge Detection Process

The Canny Edge Detection algorithm is performed using the following steps:

1. **Read the input image**
2. **Convert the image to grayscale**
3. **Apply Gaussian Blur to reduce noise**
4. **Calculate image intensity changes**
5. **Apply lower and upper threshold values**
6. **Detect strong and weak edges**
7. **Display the final edge image**

---

## Parameter Settings

| **Low Threshold** | **High Threshold** | **Result**                                                  |
| ----------------- | ------------------ | ----------------------------------------------------------- |
| 50                | 100                | Detects more edges, including weak edges and possible noise |
| 100               | 200                | Provides balanced edge detection                            |
| 150               | 250                | Detects mainly strong edges and removes weak details        |

---

## Detected Edges

The Canny algorithm detects locations where there is a significant change in pixel intensity.

The detected edges can include:

* Object boundaries
* Shapes
* Corners
* Strong intensity changes
* Important structural details in the image

The final output displays the detected edges as white pixels on a black background.

---

## Impact of Different Parameters

### Low Threshold Values

Lower threshold values detect more edges.

**Advantages:**

* Detects fine details
* Detects weak edges

**Disadvantages:**

* May detect unwanted noise
* Can produce too many edges

---

### Medium Threshold Values

Medium threshold values provide a balance between detecting important edges and reducing noise.

In this implementation:

```text
Low Threshold = 100
High Threshold = 200
```

This parameter setting generally produces a balanced edge detection result.

---

### High Threshold Values

Higher threshold values detect only strong intensity changes.

**Advantages:**

* Reduces noise
* Produces cleaner edges

**Disadvantages:**

* Fine and weak edges may disappear
* Some object details may not be detected

---

## Gaussian Blur

Gaussian Blur is applied before Canny Edge Detection.

```python
blur = cv2.GaussianBlur(
    gray,
    (5, 5),
    0
)
```

It reduces image noise and helps prevent unwanted edges from appearing in the final result.

A larger blur kernel removes more noise but may also remove fine image details.

---

## Output

The program displays:

### Original Image, Grayscale Image and Gaussian Blurred Image

<img width="1022" height="389" alt="image" src="https://github.com/user-attachments/assets/caa50a4e-4c9f-4aa3-b177-749b979b2cf9" />


### Canny Edge Detection Results
<img width="1027" height="385" alt="image" src="https://github.com/user-attachments/assets/01002c52-c4d0-4b10-a971-89da7b7d654e" />

* Detects mainly strong edges and removes weak details.

---

## Project Structure

```text
Canny-Edge-Detection/
│
├── photo.jpg
├── canny_edge_detection.ipynb
└── README.md
```

---

## How to Run

Clone the repository:

```text
git clone <repository-url>
```

Install the required libraries:

```text
pip install opencv-python matplotlib
```

Place the input image inside the project folder and use:

```python
image = cv2.imread("photo.jpg")
```

Then open the Jupyter Notebook and run the code.

---

## Conclusion

The Canny Edge Detection algorithm successfully detects object boundaries and significant intensity changes in an image.

Different threshold values significantly affect the output:

* **Lower thresholds** detect more edges but may include noise.
* **Medium thresholds** provide a balanced result.
* **Higher thresholds** detect fewer but stronger edges.

Gaussian Blur improves the results by reducing noise before edge detection.
