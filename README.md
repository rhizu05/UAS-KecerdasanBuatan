# Model Prediksi untuk Ketepatan Penempatan Karir Mahasiswa Menggunakan Algoritma Machine Learning

## Deskripsi Singkat
Proyek ini bertujuan untuk membangun dan mengevaluasi model machine learning yang dapat memprediksi status penempatan kerja (Placed atau Not Placed) seorang mahasiswa berdasarkan data akademis, demografis, dan pengalaman kerja. Dua model prediksi, yaitu Regresi Logistik dan Random Forest, diimplementasikan dan dievaluasi untuk menemukan model dengan performa terbaik.

## Prasyarat (Prerequisites)
Sebelum menjalankan proyek, pastikan Anda telah menginstal perangkat lunak dan library berikut:
- Python 3.x
- Library Python:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scikit-learn

Anda dapat menginstal semua library yang diperlukan dengan menjalankan perintah berikut di terminal Anda:
```
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

## Struktur Proyek
Pastikan Anda memiliki file-file berikut dalam direktori kerja Anda:
```
.
├── notebook_model.ipynb
├── README.md
└── data
    └── dataset.csv
```
- notebook_model.ipynb: File utama berisi seluruh kode analisis, dari pemuatan data hingga evaluasi model.
- dataset.csv: Dataset mentah yang digunakan untuk melatih dan menguji model.
- README.md: File ini, berisi penjelasan proyek.

## Langkah-langkah Pengerjaan
Berikut adalah langkah-langkah untuk mereplikasi hasil dari proyek ini:

### Langkah 1: Persiapan Lingkungan
Pastikan semua library yang tercantum di bagian Prasyarat sudah terinstal. Jika belum, gunakan perintah pip install di atas.

### Langkah 2: Menyiapkan Dataset
1. Unduh file dataset.csv dan letakkan dalam direktori yang sama dengan file notebook.
2. Buka file notebook_model.ipynb.
3. Temukan sel kode yang memuat dataset. Path asli dalam notebook mungkin spesifik untuk Google Colab, seperti ini:
```
df = pd.read_csv('/content/drive/MyDrive/2306130/Semester 4/dataset/Job_Placement_Data.csv')
```
4. PENTING: Ubah path tersebut agar sesuai dengan lokasi file Anda. Jika file CSV berada di direktori yang sama, cukup ubah menjadi:
```
df = pd.read_csv('Job_Placement_Data.csv')
```

### Langkah 3: Menjalankan Notebook
Buka dan jalankan file Prediksi_Ketepatan_Penempatan_Karir.ipynb menggunakan Jupyter Notebook, JupyterLab, atau Google Colab. Jalankan setiap sel kode secara berurutan dari atas ke bawah.

Berikut adalah alur pengerjaan yang ada di dalam notebook:

1. Impor Library: Sel pertama mengimpor semua library yang dibutuhkan untuk analisis.
2. Memuat Dataset: Membaca file Job_Placement_Data.csv ke dalam DataFrame pandas.
3. Analisis Data Eksplorasi (EDA): Beberapa sel berikutnya akan menghasilkan visualisasi data (seperti countplot dan histogram) untuk memahami distribusi dan hubungan antar fitur.
4. Pra-pemrosesan Data: Fitur-fitur kategorikal (tipe data object) diubah menjadi format numerik menggunakan LabelEncoder.
5. Pemisahan Fitur dan Target: Dataset dipisahkan menjadi variabel fitur (X) dan variabel target (y).
6. Membagi Data Latih dan Uji: Data dibagi menjadi data latih (80%) dan data uji (20%) untuk melatih dan mengevaluasi model secara objektif.
7. Membangun dan Melatih Model:
    - Model Regresi Logistik dibangun dan dilatih.
    - Model Random Forest Classifier dibangun dan dilatih.
8. Mengevaluasi Model: Kinerja kedua model dievaluasi pada data uji. Hasil evaluasi, termasuk akurasi, laporan klasifikasi (precision, recall, f1-score), dan confusion matrix, akan ditampilkan sebagai output.
9. Perbandingan Hasil: Sel terakhir menampilkan tabel perbandingan akurasi antara kedua model.

## Hasil (Output)
Setelah menjalankan semua sel, output yang akan Anda lihat meliputi:
- Tampilan beberapa baris pertama dari dataset.
- Grafik dan plot dari tahap EDA.
- Metrik evaluasi kinerja untuk model Regresi Logistik dan Random Forest.
- Visualisasi confusion matrix untuk kedua model.
- Perbandingan akhir akurasi kedua model, yang menunjukkan bahwa Random Forest memiliki performa sedikit lebih baik untuk dataset ini.

## Kontributor
- Muhamad Ar Rasyid Rizki Oktavian (2306045)
- Pandu Alghani (2306130)
