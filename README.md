# Langkah 1: Instal dan import pustaka yang dibutuhkan
!pip install opencv-python-headless matplotlib

import cv2
import matplotlib.pyplot as plt
from google.colab import files
import numpy as np

# Langkah 2: Upload gambar ikan
uploaded = files.upload()

# Ambil nama file
for filename in uploaded.keys():
    img_path = filename

# Langkah 3: Baca gambar dan konversi ke grayscale
img = cv2.imread(img_path)
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Langkah 4: Terapkan thresholding
# Threshold global: Otsu
_, thresh = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Langkah 5: Tampilkan hasil
plt.figure(figsize=(10,4))

plt.subplot(1,3,1)
plt.title('Citra Asli')
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.subplot(1,3,2)
plt.title('Grayscale')
plt.imshow(gray, cmap='gray')
plt.axis('off')

plt.subplot(1,3,3)
plt.title('Hasil Thresholding')
plt.imshow(thresh, cmap='gray')
plt.axis('off')

plt.tight_layout()
plt.show()
