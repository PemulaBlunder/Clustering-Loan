# Analisis Clustering Aplikasi Pinjaman

Proyek machine learning komprehensif yang melakukan segmentasi pelanggan pada data aplikasi pinjaman menggunakan algoritma clustering Self-Organizing Map (SOM).

## 📋 Daftar Isi

- [Gambaran Umum](#gambaran-umum)
- [Fitur](#fitur)
- [Dataset](#dataset)
- [Instalasi](#instalasi)
- [Penggunaan](#penggunaan)
- [Metodologi](#metodologi)
- [Hasil](#hasil)
- [Struktur Proyek](#struktur-proyek)
- [Dependencies](#dependencies)
- [Kontribusi](#kontribusi)
- [Lisensi](#lisensi)

## 🎯 Gambaran Umum

Proyek ini menganalisis data aplikasi pinjaman untuk mengidentifikasi segmen pelanggan yang berbeda menggunakan teknik machine learning tanpa supervisi. Analisis ini membantu institusi keuangan memahami basis pelanggan mereka dan membuat keputusan berbasis data untuk persetujuan pinjaman dan penilaian risiko.

## ✨ Fitur

- **Preprocessing Data**: Pembersihan data dan feature engineering yang komprehensif
- **Deteksi Outlier**: Penghapusan outlier statistik menggunakan metode IQR
- **Implementasi SOM Custom**: Algoritma clustering Self-Organizing Map dari nol
- **Visualisasi**: Plot interaktif dan heatmap untuk eksplorasi data
- **Analisis Cluster**: Karakterisasi dan profiling cluster yang detail
- **Metrik Performa**: Evaluasi kualitas cluster dengan silhouette score

## 📊 Dataset

Analisis menggunakan dataset aplikasi pinjaman (`loan_applications.csv`) dengan fitur utama berikut:

- **Informasi Pemohon**: Usia, pendapatan, status pekerjaan, tanggungan
- **Detail Pinjaman**: Jumlah yang diminta, tenor, suku bunga, tujuan
- **Metrik Keuangan**: Skor CIBIL, EMI yang ada, rasio hutang terhadap pendapatan
- **Informasi Properti**: Status kepemilikan, alamat tempat tinggal

### Fitur Turunan

Proyek ini membuat beberapa fitur engineering penting:

- `interest_loan_per_month`: Bunga pinjaman bulanan
- `loan_per_month`: Cicilan pinjaman bulanan
- `emi_with_loan_per_month`: Total EMI bulanan termasuk pinjaman baru
- `ratio_to_pay_per_month`: Rasio pembayaran bulanan terhadap pendapatan

## 🛠️ Instalasi

### Prasyarat

Pastikan Anda memiliki Python 3.7+ terinstal di sistem Anda.

### Clone Repository

```bash
git clone https://github.com/username/loan-application-clustering.git
cd loan-application-clustering
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Dependencies yang Diperlukan

```
pandas>=1.3.0
numpy>=1.21.0
seaborn>=0.11.0
matplotlib>=3.4.0
scikit-learn>=1.0.0
openpyxl>=3.0.0
```

## 🚀 Penggunaan

### Menjalankan Analisis Lengkap

```bash
python loan_clustering_analysis.py
```

### Input yang Diperlukan

- File `loan_applications.csv` harus berada di direktori yang sama dengan script

### Output yang Dihasilkan

- **Visualisasi**: Berbagai plot dan heatmap disimpan sebagai gambar
- **File Excel**: `cluster_loan8.xlsx` berisi data dengan label cluster
- **Metrik**: Silhouette score dan ringkasan cluster di console

## 🔬 Metodologi

### 1. Preprocessing Data

- **Pembersihan Kolom**: Menghapus kolom yang tidak relevan
- **Feature Engineering**: Membuat fitur finansial baru
- **Encoding**: Mengubah variabel kategorikal menjadi numerik
- **Scaling**: Normalisasi menggunakan MinMaxScaler

### 2. Deteksi dan Penanganan Outlier

```python
# Metode IQR untuk outlier detection
Q1 = data.quantile(0.25)
Q3 = data.quantile(0.75)
IQR = Q3 - Q1
outlier_mask = (data >= (Q1 - 1.5 * IQR)) & (data <= (Q3 + 1.5 * IQR))
```

### 3. Implementasi SOM

- **Arsitektur**: Grid 3x1 neuron
- **Learning Rate**: Adaptive (menurun seiring iterasi)
- **Neighborhood Function**: Gaussian dengan sigma yang menurun
- **Iterasi**: 1000 epoch pelatihan

### 4. Evaluasi Cluster

- **Visualisasi PCA**: Proyeksi 2D untuk visualisasi cluster
- **Silhouette Score**: Metrik kualitas clustering
- **Profil Cluster**: Analisis karakteristik rata-rata setiap cluster

## 📈 Hasil

### Metrik Performa

- **Silhouette Score**: ~0.XX (nilai akan muncul saat menjalankan script)
- **Jumlah Cluster**: 3 cluster berbeda

### Karakteristik Cluster

Setiap cluster memiliki profil yang berbeda berdasarkan:

- **Usia Pemohon**: Distribusi usia yang berbeda
- **Rasio Pembayaran**: Kemampuan bayar bulanan
- **Skor CIBIL**: Tingkat kredibilitas
- **Jumlah Pinjaman**: Nilai pinjaman yang diminta
- **Pendapatan**: Tingkat pendapatan bulanan

### Visualisasi

- **Correlation Matrix**: Heatmap korelasi antar fitur
- **Distribusi Data**: Histogram sebelum dan sesudah pembersihan
- **Cluster Visualization**: Scatter plot dengan proyeksi PCA
- **Cluster Heatmap**: Karakteristik rata-rata setiap cluster

## 📁 Struktur Proyek

```
loan-application-clustering/
│
├── loan_clustering_analysis.py    # Script utama
├── loan_applications.csv          # Dataset input
├── cluster_loan8.xlsx             # Hasil clustering
├── requirements.txt               # Dependencies
├── README.md                      # Dokumentasi
└── images/                        # Folder untuk visualisasi
    ├── correlation_matrix.png
    ├── cluster_visualization.png
    └── cluster_heatmap.png
```

## 🔧 Kustomisasi

### Mengubah Parameter SOM

```python
# Dalam implementasi SimpleSOM
som = SimpleSOM(
    x=3,                    # Tinggi grid
    y=1,                    # Lebar grid
    input_len=X.shape[1],   # Dimensi input
    sigma=1.0,              # Neighborhood radius
    learning_rate=0.5       # Learning rate awal
)
```

### Menambah Fitur Baru

1. Tambahkan kolom baru ke `df_digunakan`
2. Sesuaikan preprocessing jika diperlukan
3. Update array `X` untuk clustering

## 🤝 Kontribusi

Kontribusi sangat diterima! Silakan:

1. Fork repository
2. Buat feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit perubahan (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buka Pull Request

### Area untuk Kontribusi

- Implementasi algoritma clustering lain (K-Means, DBSCAN)
- Optimisasi hyperparameter otomatis
- Dashboard interaktif dengan Streamlit/Dash
- API untuk prediksi cluster real-time
- Unit testing dan validasi

## 📝 Lisensi

Proyek ini dilisensikan di bawah MIT License - lihat file [LICENSE](LICENSE) untuk detail.

## 📞 Kontak

Jika Anda memiliki pertanyaan atau saran, silakan buat issue di repository ini atau hubungi:

- **Email**: your.email@example.com
- **LinkedIn**: [Your LinkedIn Profile]
- **GitHub**: [@yourusername]

## 🙏 Acknowledgments

- Dataset digunakan untuk tujuan pendidikan dan penelitian
- Implementasi SOM terinspirasi dari penelitian tentang neural networks
- Terima kasih kepada komunitas open source untuk library yang digunakan

---

**⭐ Jangan lupa untuk memberikan star jika proyek ini membantu Anda!**
