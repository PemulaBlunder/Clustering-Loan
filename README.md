# 📌 Analisis Clustering Aplikasi Pinjaman (Jupyter Notebook)

Proyek machine learning komprehensif yang melakukan segmentasi pelanggan pada data aplikasi pinjaman menggunakan algoritma Self-Organizing Map (SOM), sepenuhnya dikerjakan dalam notebook Jupyter.

## 📋 Daftar Isi

* [🎯 Gambaran Umum](#-gambaran-umum)
* [✨ Fitur](#-fitur)
* [📊 Dataset](#-dataset)
* [🛠️ Instalasi](#️-instalasi)
* [🚀 Penggunaan](#-penggunaan)
* [🔬 Metodologi](#-metodologi)
* [📈 Hasil](#-hasil)
* [📁 Struktur Proyek](#-struktur-proyek)
* [🔧 Kustomisasi](#-kustomisasi)
* [🤝 Kontribusi](#-kontribusi)
* [📝 Lisensi](#-lisensi)
* [📞 Kontak](#-kontak)
* [🙏 Acknowledgments](#-acknowledgments)

---

## 🎯 Gambaran Umum

Proyek ini menganalisis data aplikasi pinjaman untuk mengidentifikasi segmen pelanggan yang berbeda menggunakan teknik machine learning tanpa supervisi (Unsupervised Learning). Pendekatan clustering menggunakan Self-Organizing Map (SOM) membantu lembaga keuangan memahami perilaku pelanggan dan mengoptimalkan pengambilan keputusan terkait pinjaman dan risiko.

---

## ✨ Fitur

* ✅ Preprocessing data dan feature engineering lengkap
* 🔍 Deteksi dan penanganan outlier dengan metode IQR
* 🧠 Implementasi algoritma Self-Organizing Map dari nol
* 📊 Visualisasi interaktif dalam notebook
* 📋 Analisis mendalam terhadap hasil cluster
* 📈 Evaluasi kualitas dengan Silhouette Score

---

## 📊 Dataset

Menggunakan dataset `loan_applications.csv` yang mencakup:

* **Informasi Pemohon**: Usia, pekerjaan, pendapatan, tanggungan
* **Informasi Pinjaman**: Jumlah pinjaman, tenor, suku bunga, tujuan
* **Data Finansial**: Skor CIBIL, EMI aktif, rasio pembayaran
* **Properti**: Kepemilikan dan alamat tempat tinggal

### Fitur Turunan

* `interest_loan_per_month`
* `loan_per_month`
* `emi_with_loan_per_month`
* `ratio_to_pay_per_month`

---

## 🛠️ Instalasi

### Prasyarat

* Python 3.7+
* Jupyter Notebook atau JupyterLab

### Instalasi Paket

Instal pustaka yang dibutuhkan:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

---

## 🚀 Penggunaan

### Menjalankan Notebook

1. Clone repository ini:

```bash
git clone https://github.com/username/loan-application-clustering.git
cd loan-application-clustering
```

2. Jalankan Jupyter Notebook:

```bash
jupyter notebook loan_clustering_analysis.ipynb
```

3. Jalankan semua sel secara berurutan untuk menjalankan preprocessing, training SOM, visualisasi, dan evaluasi.

---

## 🔬 Metodologi

### 1. Preprocessing Data

* Menghapus kolom tidak relevan
* Feature engineering finansial
* Encoding data kategorikal
* Normalisasi menggunakan MinMaxScaler

### 2. Deteksi Outlier

Menggunakan metode IQR:

```python
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
mask = (df >= (Q1 - 1.5 * IQR)) & (df <= (Q3 + 1.5 * IQR))
```

### 3. Self-Organizing Map (SOM)

* Grid 3x1
* Learning rate adaptif
* Gaussian neighborhood
* Iterasi: 1000 epoch

### 4. Evaluasi

* PCA untuk visualisasi 2D
* Silhouette Score sebagai metrik kualitas
* Profil karakteristik tiap cluster

---

## 📈 Hasil

### Metrik

* **Silhouette Score**: \~0.XX (didapat saat eksekusi notebook)
* **Cluster Terbentuk**: 3 cluster

### Visualisasi

* 🔵 Korelasi antar fitur (Heatmap)
* 🔶 Histogram distribusi data
* 🟢 Scatter plot hasil PCA
* 🔴 Heatmap profil cluster

---

## 📁 Struktur Proyek

```
loan-application-clustering/
│
├── loan_clustering_analysis.ipynb    # Notebook utama
├── loan_applications.csv             # Dataset input
├── cluster_loan8.xlsx                # Output hasil cluster
├── README.md                         # Dokumentasi proyek
├── requirements.txt                  # (Opsional) daftar pustaka
└── images/                           # Hasil visualisasi
    ├── correlation_matrix.png
    ├── cluster_visualization.png
    └── cluster_heatmap.png
```

---

## 🔧 Kustomisasi

### Ubah Parameter SOM

```python
som = SimpleSOM(
    x=3, y=1,
    input_len=X.shape[1],
    sigma=1.0,
    learning_rate=0.5
)
```

### Tambah Fitur Baru

1. Tambahkan kolom baru di `df_digunakan`
2. Update tahap preprocessing
3. Tambahkan ke array `X` untuk pelatihan SOM

---

## 🤝 Kontribusi

Sangat terbuka untuk kontribusi! Kamu bisa:

1. Fork repo ini
2. Buat branch: `git checkout -b fitur-baru`
3. Commit: `git commit -m 'Menambahkan fitur baru'`
4. Push: `git push origin fitur-baru`
5. Buka Pull Request

### Ide Kontribusi

* Tambah algoritma lain (K-Means, DBSCAN)
* Dashboard interaktif (Streamlit, Dash)
* API prediksi cluster
* Unit test dan evaluasi model

---

## 📝 Lisensi

Proyek ini berada di bawah lisensi **MIT**. Silakan lihat [LICENSE](LICENSE) untuk detail.

---

## 📞 Kontak

* Email: [ian.teuku05@gmail.com](mailto:ian.teuku05@gmail.com)
* GitHub: [@PemulaBlunder](https://github.com/PemulaBlunder)

---

## 🙏 Acknowledgments

* Dataset untuk tujuan edukasi dan riset
* Inspirasi implementasi SOM dari berbagai studi neural network
* Terima kasih komunitas open source atas library yang digunakan

---

⭐ **Bantu bintang repository ini jika bermanfaat untukmu!**

---
