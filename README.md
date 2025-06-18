# glcm-lung-cancer-detector
Analisis Citra Kanker Paru Berbasis GLCM & Machine Learning

Proyek ini mengembangkan sistem klasifikasi gambar histopatologis paru-paru (kanker vs normal) dengan pendekatan **ekstraksi fitur tekstur menggunakan GLCM (Gray-Level Co-occurrence Matrix)** dan **model Machine Learning**.

<img src="https://img.shields.io/badge/Status-Active-blue" alt="status-badge">
<img src="https://img.shields.io/badge/Machine%20Learning-Random%20Forest-green" alt="ml-badge">
<img src="https://img.shields.io/badge/Interface-Gradio-orange" alt="gradio-badge">

---

Tujuan Proyek

- Mengubah citra mikroskopis menjadi bentuk fitur tekstur numerik menggunakan GLCM.
- Menggunakan model Machine Learning (Random Forest) untuk memprediksi apakah jaringan tersebut **normal** atau **kanker paru**.
- Menyediakan **antarmuka interaktif** menggunakan **Gradio** untuk pengguna mengunggah gambar dan menerima hasil analisis serta prediksi.

---

 Tools & Library

- `Gradio` - UI interaktif untuk prediksi real-time
- `OpenCV` - Pemrosesan gambar
- `Mahotas` & `Scikit-Image` - Ekstraksi fitur tekstur (GLCM)
- `Matplotlib` - Visualisasi histogram
- `scikit-learn` - Pelatihan model machine learning (Random Forest)

---

Alur Proses

1. Ekstraksi Dataset dari Kaggle:  
   Dataset "Lung and Colon Cancer Histopathological Images" digunakan dan difilter menjadi dua kelas: `normal` dan `kanker`.

2. Pra-pemrosesan Citra:
   - Konversi ke grayscale
   - Median filtering untuk mengurangi noise
   - Deteksi tepi Canny
   - Plotting histogram intensitas

3. Ekstraksi Fitur Tekstur:
   - Fitur GLCM: contrast, correlation, energy, homogeneity

4. Training Model:
   - Ekstraksi fitur dari dataset sample
   - Pelatihan model Random Forest

5. Prediksi via Gradio:
   - Upload gambar → Analisis visual → Prediksi kanker / normal

---

Tampilan Antarmuka

Interface Gradio menampilkan:

- Grayscale image
- Hasil filter median
- Deteksi tepi Canny
- Histogram
- Fitur GLCM (JSON)
- Prediksi klasifikasi

---

Struktur Folder Dataset

lung_data/
└── lung_colon_image_set/
└── lung_image_sets/
├── lung_aca/ # Kanker (adenokarsinoma)
├── lung_n/ # Normal
└── lung_scc/ # Kanker (sel skuamosa)


Cara Menjalankan (di Google Colab)

1. Unggah kaggle.json
2. Jalankan cell:
python
!kaggle datasets download -d andrewmvd/lung-and-colon-cancer-histopathological-images
Ekstrak & sampling data:
python
# Salin sebagian gambar ke sample_data_35
Jalankan seluruh pipeline Gradio

Contoh Output (Terminal)
markdown

Hasil evaluasi model:
              precision    recall  f1-score   support

      kanker       0.86      0.86      0.86         7
      normal       0.86      0.86      0.86         7

    accuracy                           0.86        14
