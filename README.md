## AIM:
Write a Python program using OpenCV that performs the following tasks:

1. Read and Display an Image.
2. Adjust the brightness of an image.
3. Modify the image contrast.
4. Generate a third image using bitwise operations.

---

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook

---

## Algorithm:

### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type uint8) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.

### Step 4:
Modify the image contrast using scaling factors.

### Step 5:
Split the image into B, G, R and H, S, V channels and display them.

---

## Program Developed By:

- **Name:** Thamizh S
- **Register Number:** 212224040350

## Ex. No. 01

### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('4e1af01377a347b3a0455cc921d4793c.jpg', cv2.IMREAD_COLOR)
```

---

### 2. Print the image width, height & Channel.

```python
height, width, channel = img.shape

print("Width :", width)
print("Height :", height)
print("Channel :", channel)
```

---

### 3. Display the image using matplotlib imshow().

```python
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```

---

### 4. Save the image as a PNG file using OpenCV imwrite().

```python
cv2.imwrite("Eagle.png", img)
```

---

### 5. Read the saved image above as a color image using cv2.cvtColor().

```python
img_color = cv2.imread("Eagle.png")
img_color = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)
```

---

### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.

```python
h, w, c = img_color.shape

print("Width :", w)
print("Height :", h)
print("Channel :", c)

plt.imshow(img_color)
plt.title("Colour Image")
plt.axis('off')
plt.show()
```

---

### 7. Crop the image to extract any specific (Eagle alone) object from the image.

```python
cropped = img[50:350,100:400]

plt.imshow(cv2.cvtColor(cropped,cv2.COLOR_BGR2RGB))
plt.title("Cropped Image")
plt.axis('off')
plt.show()
```

---

### 8. Resize the image up by a factor of 2x.

```python
resized = cv2.resize(img,None,fx=2,fy=2)

plt.imshow(cv2.cvtColor(resized,cv2.COLOR_BGR2RGB))
plt.title("Resized Image")
plt.axis('off')
plt.show()
```

---

### 9. Flip the cropped/resized image horizontally.

```python
flipped = cv2.flip(cropped,1)

plt.imshow(cv2.cvtColor(flipped,cv2.COLOR_BGR2RGB))
plt.title("Flipped Image")
plt.axis('off')
plt.show()
```

---

### 10. Read in the image ('Apollo-11-launch.jpg').

```python
apollo = cv2.imread("Apollo-11-launch.jpg")
apollo_rgb = cv2.cvtColor(apollo,cv2.COLOR_BGR2RGB)
```

---

### 11. Add the following text to the dark area at the bottom of the image.

```python
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN

cv2.putText(apollo,
            text,
            (80,apollo.shape[0]-20),
            font_face,
            1.5,
            (255,255,255),
            2)
```

---

### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.

```python
rect_color = (255,0,255)

cv2.rectangle(apollo,
              (220,40),
              (420,650),
              rect_color,
              3)
```

---

### 13. Display the final annotated image.

```python
plt.imshow(cv2.cvtColor(apollo,cv2.COLOR_BGR2RGB))
plt.title("Apollo 11 Launch")
plt.axis('off')
plt.show()
```

---

### 14. Read the image ('Boy.jpg').

```python
img = cv2.imread("Boy.jpg")
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```

---

### 15. Adjust the brightness of the image.

```python
matrix = np.ones(img.shape,dtype="uint8")*50
```

---

### 16. Create brighter and darker images.

```python
img_brighter = cv2.add(img,matrix)
img_darker = cv2.subtract(img,matrix)
```

---

### 17. Display the images (Original Image, Darker Image, Brighter Image).

```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img,cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis('off')

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_darker,cv2.COLOR_BGR2RGB))
plt.title("Darker")
plt.axis('off')

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_brighter,cv2.COLOR_BGR2RGB))
plt.title("Brighter")
plt.axis('off')

plt.show()
```

---

### 18. Modify the image contrast.

```python
matrix1 = np.uint8(img*1.1)
matrix2 = np.uint8(img*1.2)

img_higher1 = matrix1
img_higher2 = matrix2
```

---

### 19. Display the images (Original, Lower Contrast, Higher Contrast).

```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img,cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis('off')

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_higher1,cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.1")
plt.axis('off')

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_higher2,cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.2")
plt.axis('off')

plt.show()
```

---

### 20. Split the image (Boy.jpg) into the B,G,R components & Display the channels.

```python
b,g,r = cv2.split(img)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(b,cmap='gray')
plt.title("Blue")

plt.subplot(1,3,2)
plt.imshow(g,cmap='gray')
plt.title("Green")

plt.subplot(1,3,3)
plt.imshow(r,cmap='gray')
plt.title("Red")

plt.show()
```

---

### 21. Merge the R, G, B displays along with the original image.

```python
merged = cv2.merge((b,g,r))

plt.figure(figsize=(8,4))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img,cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(merged,cv2.COLOR_BGR2RGB))
plt.title("Merged RGB")

plt.show()
```

---

### 22. Split the image into the H, S, V components & Display the channels.

```python
hsv = cv2.cvtColor(img,cv2.COLOR_BGR2HSV)

h,s,v = cv2.split(hsv)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(h,cmap='gray')
plt.title("Hue")

plt.subplot(1,3,2)
plt.imshow(s,cmap='gray')
plt.title("Saturation")

plt.subplot(1,3,3)
plt.imshow(v,cmap='gray')
plt.title("Value")

plt.show()
```

---

### 23. Merge the H, S, V displays along with the original image.

```python
merged_hsv = cv2.merge((h,s,v))

rgb = cv2.cvtColor(merged_hsv,cv2.COLOR_HSV2RGB)

plt.figure(figsize=(8,4))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img,cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(rgb)
plt.title("Merged HSV")

plt.show()
```

---

## Output:
<img width="721" height="418" alt="image" src="https://github.com/user-attachments/assets/67452006-9ebd-4c03-a2dc-8b20cf4b3558" />

<img width="648" height="400" alt="image" src="https://github.com/user-attachments/assets/c688ab48-a6ce-4e9c-9c2e-6f0aad0ad1fa" />

<img width="638" height="394" alt="image" src="https://github.com/user-attachments/assets/fca9d5f8-a94b-44de-b25f-13fbe0b164ec" />

<img width="691" height="401" alt="image" src="https://github.com/user-attachments/assets/a1967597-8679-4c4f-af7b-c2756e89fb08" />

<img width="649" height="397" alt="image" src="https://github.com/user-attachments/assets/14e3f92e-db3e-4c0b-ada2-c08cd416ddea" />

<img width="632" height="375" alt="image" src="https://github.com/user-attachments/assets/463d78c2-4b73-4651-9b17-283a691e57b8" />

<img width="668" height="392" alt="image" src="https://github.com/user-attachments/assets/0345c05a-01ba-4d6a-846e-dea88a9805fc" />

<img width="632" height="406" alt="image" src="https://github.com/user-attachments/assets/915dc13b-2758-4b7e-a294-116c834ee1f9" />

<img width="630" height="373" alt="image" src="https://github.com/user-attachments/assets/c2ee4e88-e552-49c5-8a53-62b1f3f6bd56" />

<img width="625" height="377" alt="image" src="https://github.com/user-attachments/assets/36995c1a-9c51-4c4d-9e93-b69fef2bd666" />

<img width="644" height="383" alt="image" src="https://github.com/user-attachments/assets/9d9739d6-9c56-4161-88a2-d76790600ba8" />

<img width="655" height="492" alt="image" src="https://github.com/user-attachments/assets/8e0b1395-5646-46ea-8658-844673669f78" />

<img width="504" height="477" alt="image" src="https://github.com/user-attachments/assets/a8cd656c-582f-4d01-9f31-d9016df53cd4" />

<img width="674" height="384" alt="image" src="https://github.com/user-attachments/assets/4ba429bb-b230-4dd5-b4ab-e80df4898f15" />

<img width="670" height="386" alt="image" src="https://github.com/user-attachments/assets/91e66afc-8c3e-474c-a32e-7ca2f367b9bc" />


## Result:

Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
