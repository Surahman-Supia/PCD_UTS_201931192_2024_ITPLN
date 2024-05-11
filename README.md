
# Soal 1

import cv2
import numpy as np
import matplotlib.pyplot as plt
# Baca citra
image = cv2.imread('Surahman.jpg')
# Fungsi untuk mendeteksi warna tertentu dalam citra
def detect_color(image, lower_color, upper_color):
    # Konversi citra ke ruang warna HSV
    hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
    
    # Buat mask dengan menggunakan rentang warna yang ditentukan
    mask = cv2.inRange(hsv_image, lower_color, upper_color)
    
    # Aplikasikan mask ke citra asli
    result = cv2.bitwise_and(image, image, mask=mask)
    
    return result
lower_red = np.array([136, 87, 111])
upper_red = np.array([180, 255, 255])
lower_green = np.array([40, 50, 50])
upper_green = np.array([90, 255, 255])
lower_blue = np.array([100, 50, 50])
upper_blue = np.array([140, 255, 255])
# Deteksi warna dalam citra
red_objects = detect_color(image, lower_red, upper_red)
green_objects = detect_color(image, lower_green, upper_green)
blue_objects = detect_color(image, lower_blue, upper_blue)
# Tampilkan citra asli
plt.subplot(2, 2, 1)
plt.title('Original Image')
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.axis('off')

# Tampilkan hasil deteksi warna merah
plt.subplot(2, 2, 2)
plt.title('Detected Red Objects')
plt.imshow(cv2.cvtColor (red_objects, cv2.COLOR_BGR2RGB), cmap='gray')
plt.axis('off')

# Tampilkan hasil deteksi warna hijau
plt.subplot(2, 2, 3)
plt.title('Detected Green Objects')
plt.imshow(cv2.cvtColor (green_objects, cv2.COLOR_BGR2RGB), cmap='gray')
plt.axis('off')

# Tampilkan hasil deteksi warna
plt.subplot(2, 2, 4)
plt.title('Detected Blue Objects')
plt.imshow(cv2.cvtColor (blue_objects, cv2.COLOR_BGR2RGB), cmap='gray')
plt.axis('off')

plt.show()
#Original Image
fig, axs = plt.subplots(2,2, figsize=(15,5))
axs[0,0].imshow(image)
axs[0,1].hist(image.ravel(),256,[0,256])

#Cara 2
hist = cv2.calcHist([image],[0],None,[256],[0,256])
axs[1,0].imshow(image)
axs[1,1].plot(hist)
plt.show()

#Red Image
fig, axs = plt.subplots(2,2, figsize=(15,5))
axs[0,0].imshow(red_objects)
axs[0,1].hist(red_objects.ravel(),256,[0,256])

#Cara 2
hist = cv2.calcHist([red_objects],[0],None,[256],[0,256])
axs[1,0].imshow(red_objects)
axs[1,1].plot(hist)
plt.show()

#Blue Image
fig, axs = plt.subplots(2,2, figsize=(15,5))
axs[0,0].imshow(blue_objects)
axs[0,1].hist(blue_objects.ravel(),256,[0,256])

#Cara 2
hist = cv2.calcHist([blue_objects],[0],None,[256],[0,256])
axs[1,0].imshow(blue_objects)
axs[1,1].plot(hist)
plt.show()

#Green Image
fig, axs = plt.subplots(2,2, figsize=(15,5))
axs[0,0].imshow(green_objects)
axs[0,1].hist(green_objects.ravel(),256,[0,256])

#Cara 2
hist = cv2.calcHist([green_objects],[0],None,[256],[0,256])
axs[1,0].imshow(green_objects)
axs[1,1].plot(hist)
plt.show()