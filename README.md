# andika-surya-saputra_202231050_PCD-A
-import library

import cv2
import matplotlib.pyplot as plt
import skimage.io
import numpy as np
from skimage.feature import graycomatrix, graycoprops

Kode ini menggunakan pustaka OpenCV, Matplotlib, scikit-image, dan NumPy untuk pemrosesan gambar dan analisis fitur tekstur. OpenCV dipakai untuk mengonversi gambar menjadi grayscale, Matplotlib untuk menampilkan gambar, dan scikit-image untuk membaca gambar dari file. NumPy digunakan untuk operasi numerik. Fungsi graycomatrix dan graycoprops dari scikit-image menghitung matriks ko-okurensi tingkat abu-abu (GLCM) serta propertinya, seperti kontras dan homogenitas, yang membantu dalam analisis tekstur gambar.

-membaca gambar
``` Python img = skimage.io.imread('2.jpg')```
untuk memasukan gambar


