# OPENING--AND-CLOSING

## Aim
To implement Opening and Closing operations using Python and OpenCV.

---

## Software Required
- Anaconda – Python 3.7
- OpenCV
- NumPy
- Matplotlib

---

## Algorithm

### Step 1
Import the required libraries such as OpenCV, NumPy, and Matplotlib.

### Step 2
Create a text image using the `cv2.putText()` function.

### Step 3
Create a structuring element for morphological operations.

### Step 4
Apply the Opening operation on the noisy image.

### Step 5
Apply the Closing operation on the noisy image and display the results.

---

# Program

## Import the Necessary Packages
```python
import cv2
import numpy as np
from matplotlib import pyplot as plt
```

## Create the Text using cv2.putText
```python
# Replace 'ABCDE' with your name (only the first 5 characters)

def load_img():

    blank_img = np.zeros((600,600))

    font = cv2.FONT_HERSHEY_SIMPLEX

    cv2.putText(blank_img,
                text='JAGAN',
                org=(50,300),
                fontFace=font,
                fontScale=5,
                color=(255,255,255),
                thickness=25,
                lineType=cv2.LINE_AA)

    return blank_img
```

## Display the Image
```python
def display_img(img):

    fig = plt.figure(figsize=(12,10))

    ax = fig.add_subplot(111)

    ax.imshow(img, cmap='gray')

    plt.show()
```

## Create the Structuring Element
```python
kernel = np.ones((5,5), dtype=np.uint8)

kernel
```

## Display the Input Image
```python
img = load_img()

display_img(img)
```

## Use the Opening Operation
```python
# Create white noise

white_noise = np.random.randint(low=0, high=2, size=(600,600))

white_noise = white_noise * 255

noise_img = white_noise + img

display_img(noise_img)

# Apply Opening

opening = cv2.morphologyEx(noise_img, cv2.MORPH_OPEN, kernel)

display_img(opening)
```

## Use the Closing Operation
```python
# Create black noise

img = load_img()

black_noise = np.random.randint(low=0, high=2, size=(600,600))

black_noise = black_noise * -255

black_noise_img = img + black_noise

black_noise_img[black_noise_img == -255] = 0

display_img(black_noise_img)

# Apply Closing

closing = cv2.morphologyEx(black_noise_img,
                           cv2.MORPH_CLOSE,
                           kernel)

display_img(closing)
```

---

# Output

## Display the Input Image
<img width="911" height="691" alt="image" src="https://github.com/user-attachments/assets/92b88b2e-36a4-45c8-b720-c353bdfb8f3b" />

## Display the Result of Opening
<img width="730" height="685" alt="image" src="https://github.com/user-attachments/assets/f1ef810e-d66f-4a4a-9ba4-226b60221de3" />
<img width="786" height="697" alt="image" src="https://github.com/user-attachments/assets/61779179-c66d-45d2-ae5a-d286c7c46479" />

## Display the Result of Closing
<img width="697" height="705" alt="image" src="https://github.com/user-attachments/assets/c450a2a5-758a-43b1-bc6b-473b873687e4" />


<img width="712" height="685" alt="image" src="https://github.com/user-attachments/assets/d9fe5fbf-f3f3-4331-b580-6d14881a1159" />
---

# Result
Thus, the Opening and Closing operations were successfully performed on the image using Python and OpenCV.

---
