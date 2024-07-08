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
 ```Python
img = skimage.io.imread('2.jpg')
```
untuk memasukan gambar

-Gambar RGB ke HSV
``` python
img_hsv = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
```
Kode ini mengonversi gambar dari RGB ke HSV menggunakan cv2.cvtColor dari pustaka OpenCV. Gambar input img dalam format RGB diubah menjadi ruang warna HSV, dan hasilnya disimpan dalam variabel img_hsv. Ini memisahkan informasi warna dari intensitas, membuat analisis dan manipulasi gambar menjadi lebih mudah.

-Ekstraksi Kanal V Dari Gambar HSV
``` python
img_v = img_hsv[:, :, 2]
```
Kode ini mengekstrak kanal Value (V) dari gambar dalam ruang warna HSV. Dengan menggunakan img_hsv[:, :, 2], kode ini mengambil keseluruhan gambar img_hsv dan memilih kanal ketiga (indeks 2), yang menunjukkan tingkat kecerahan atau intensitas, dan menyimpannya dalam variabel img_v.

-GLCM Pada Kanal V
``` python
glcm = graycomatrix(img_v, distances=[1], angles=[0], levels=256, symmetric=True, normed=True)
```
Kode ini menghitung matriks ko-okurensi tingkat abu-abu (GLCM) dari kanal Value (V) gambar HSV yang disimpan dalam img_v. Menggunakan graycomatrix, GLCM dihitung untuk jarak piksel 1 dan sudut 0 derajat, dengan 256 tingkat abu-abu. Parameter symmetric=True memastikan GLCM simetris, dan normed=True menormalkan matriks, menghasilkan frekuensi relatif. Hasilnya disimpan dalam variabel glcm.

-Melakukan Plot Gambar RGB dan HRV
``` python
fig, axs = plt.subplots(1, 3, figsize=(20, 10))

ax = axs.ravel()

ax[0].imshow(img)
ax[0].set_title("RGB")

ax[1].imshow(img_hsv)
ax[1].set_title("HSV")

ax[2].imshow(img_v, cmap='gray')
ax[2].set_title("Kanal V dari HSV")

plt.show()
```
Kode ini menggunakan Matplotlib untuk membuat subplot yang menampilkan tiga gambar berbeda dalam satu figur. Subplot pertama menunjukkan gambar asli dalam ruang warna RGB (img). Subplot kedua menampilkan gambar yang telah dikonversi ke ruang warna HSV (img_hsv). Subplot ketiga menunjukkan kanal Value (V) dari gambar dalam ruang warna HSV (img_v), dengan menggunakan colormap 'gray' untuk memperlihatkan intensitas piksel. Ukuran figur diatur dengan figsize=(20, 10). Setiap subplot diberi judul yang sesuai dengan jenis gambar yang ditampilkan. Hasilnya adalah tiga gambar yang ditampilkan berdampingan untuk membandingkan ruang warna RGB dan HSV, serta visualisasi kanal V dari ruang warna HSV.

-Menghitung Properti dari GLCM
``` python
contrast = graycoprops(glcm, 'contrast')[0, 0]
dissimilarity = graycoprops(glcm, 'dissimilarity')[0, 0]
homogeneity = graycoprops(glcm, 'homogeneity')[0, 0]
energy = graycoprops(glcm, 'energy')[0, 0]
correlation = graycoprops(glcm, 'correlation')[0, 0]
ASM = graycoprops(glcm, 'ASM')[0, 0]
```
Kode ini menghitung beberapa karakteristik dari matriks ko-okurensi tingkat abu-abu (GLCM) yang sudah dihitung sebelumnya (glcm). Properti yang dihitung mencakup kontras, dissimilaritas, homogenitas, energi, korelasi, dan ASM (Angular Second Moment). Setiap nilai properti diambil dari hasil yang dikembalikan oleh fungsi graycoprops untuk posisi piksel [0, 0] dalam matriks GLCM. Properti ini memberikan informasi tentang pola dan distribusi nilai piksel dalam gambar, yang sangat penting dalam analisis tekstur gambar.

-Lalu Print Properti GLCM
``` python
print(f"Contrast: {contrast}")
print(f"Dissimilarity: {dissimilarity}")
print(f"Homogeneity: {homogeneity}")
print(f"Energy: {energy}")
print(f"Correlation: {correlation}")
print(f"ASM: {ASM}")
```
Kode ini mencetak nilai properti yang telah dihitung sebelumnya dari matriks ko-okurensi tingkat abu-abu (GLCM). Properti yang dicetak meliputi kontras, dissimilaritas, homogenitas, energi, korelasi, dan ASM (Angular Second Moment). Setiap nilai properti dicetak menggunakan f-string untuk memformat output secara jelas dan terstruktur.



