# andika-surya-saputra_202231050_PCD-A
-import library

```Python
 import cv2
import matplotlib.pyplot as plt
import skimage.io
import numpy as np
from skimage.feature import graycomatrix, graycoprops
```

Kode ini menggunakan pustaka OpenCV, Matplotlib, scikit-image, dan NumPy untuk pemrosesan gambar dan analisis fitur tekstur. OpenCV dipakai untuk mengonversi gambar menjadi grayscale, Matplotlib untuk menampilkan gambar, dan scikit-image untuk membaca gambar dari file. NumPy digunakan untuk operasi numerik. Fungsi graycomatrix dan graycoprops dari scikit-image menghitung matriks ko-okurensi tingkat abu-abu (GLCM) serta propertinya, seperti kontras dan homogenitas, yang membantu dalam analisis tekstur gambar.

-membaca gambar
 img = skimage.io.imread('2.jpg')
untuk memasukan gambar

-Konversi Gambar RGB ke HSV
img_hsv = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
Kode ini mengonversi gambar dari RGB ke HSV menggunakan `cv2.cvtColor` dari pustaka OpenCV. Gambar input `img` dalam format RGB diubah menjadi ruang warna HSV, dan hasilnya disimpan dalam variabel `img_hsv`. Ini memisahkan informasi warna dari intensitas, membuat analisis dan manipulasi gambar menjadi lebih mudah.

-Melakukan Ekstraksi Kanal V Dari Gambar HSV
img_v = img_hsv[:, :, 2]



