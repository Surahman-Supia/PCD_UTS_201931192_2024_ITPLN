#Soal_2

import cv2
import numpy as np
import matplotlib.pyplot as plt
# Baca image
image = cv2.imread('Surahman.jpg')
def detect_color(image, lower_red, upper_red, lower_blue, upper_blue):
    # Konversi citra ke ruang warna HSV
    hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
    
    # Buat mask untuk warna merah dan biru
    mask_red = cv2.inRange(hsv_image, lower_red, upper_red)
    mask_blue = cv2.inRange(hsv_image, lower_blue, upper_blue)
    mask_green = cv2.inRange(hsv_image, lower_green, upper_green)
    
    # Gabungkan mask biru dan mask merah
    mask_combined = cv2.bitwise_or(mask_red, mask_blue, mask_green)
    
    # Aplikasikan mask ke citra asli
    result = cv2.bitwise_and(image, image, mask=mask_combined)
    
    return result
def detect_colors(image, lower_red, upper_red, lower_blue, upper_blue, lower_green, upper_green):
    # Konversi citra ke ruang warna HSV
    hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
    
    # Buat mask untuk warna merah dan biru
    mask_red = cv2.inRange(hsv_image, lower_red, upper_red)
    mask_blue = cv2.inRange(hsv_image, lower_blue, upper_blue)
    mask_green = cv2.inRange(hsv_image, lower_green, upper_green)
    
    # Gabungkan mask biru dan mask merah
    mask_combined = cv2.bitwise_or(mask_red, mask_blue, mask_green)
    
    # Aplikasikan mask ke citra asli
    result = cv2.bitwise_and(image, image, mask=mask_combined)
    
    return result
lower_red = np.array([136, 87, 111])
upper_red = np.array([180, 255, 255])
lower_green = np.array([40, 50, 50])
upper_green = np.array([90, 255, 255])
lower_blue = np.array([100, 50, 50])
upper_blue = np.array([140, 255, 255])
a = detect_color(image, lower_red, upper_red, lower_blue, upper_blue)
b = detect_colors(image, lower_red, upper_red, lower_blue, upper_blue, lower_green, upper_green)

# Tampilkan gambar asli
plt.figure(figsize=(12,8))
plt.subplot(221)
plt.title('Normal')
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.axis()

# Tampilkan hasil deteksi warna campuran

plt.subplot(222)
plt.imshow(a, cmap='gray')
plt.title('Blue Red Image')

plt.subplot(223)
plt.imshow(cv2.cvtColor(b, cv2.COLOR_BGR2RGB))
plt.title('Red Green Blue Image')

plt.subplot(224)
plt.title('Blue')
plt.imshow(cv2.cvtColor (blue_objects, cv2.COLOR_BGR2RGB), cmap='gray')
plt.axis()

plt.show()
