# Prediksi Ketepatan Penempatan Karir Mahasiswa Menggunakan Algoritma Machine Learning
Anggota Kelompok:

- Muhamad Ar Rasyid Rizki Oktavian (NIM 2306045)
- Pandu Alghani (NIM 2306130)

# Business Understanding
## Permasalahan Dunia Nyata
Di tengah kompleksitas pasar kerja yang terus berubah, penempatan karir yang tepat menjadi salah satu tantangan utama bagi individu dan organisasi. Kesalahan dalam menempatkan individu pada peran tertentu tidak hanya menurunkan produktivitas dan kepuasan karyawan, tetapi juga berdampak negatif pada kesuksesan organisasi secara keseluruhan. Keputusan penempatan karir seringkali bersifat subjektif dan memakan waktu. Proses rekrutmen tradisional mungkin tidak sepenuhnya dapat mengungkap potensi tersembunyi dari seorang kandidat berdasarkan riwayat pendidikan, pengalaman, dan minat mereka.

## Tujuan Proyek
Tujuan utama dari proyek ini adalah untuk menerapkan dan mengevaluasi model prediksi Machine Learning (ML) untuk memprediksi apakah seorang mahasiswa akan berhasil ditempatkan di sebuah karir (mendapatkan pekerjaan) berdasarkan data akademik dan non-akademik mereka. Secara spesifik, proyek ini bertujuan untuk:
- Membangun model untuk memprediksi status penempatan kerja (Placed atau Not Placed).
- Mengevaluasi dan membandingkan performa dari dua algoritma prediksi: Regresi Logistik dan Random Forest.
- Memberikan alat bantu pengambilan keputusan yang lebih objektif dan efisien bagi pemangku kepentingan.

## Siapa User/Pengguna Sistem
Sistem prediksi ini memiliki beberapa calon pengguna utama, antara lain:
- Departemen Sumber Daya Manusia (SDM) Perusahaan: Untuk membantu proses penyaringan kandidat karyawan secara lebih efisien dan akurat.
- Lembaga Pendidikan & Pusat Karir Universitas: Untuk memberikan rekomendasi kepada mahasiswa mengenai potensi karir mereka dan area yang perlu ditingkatkan.
- Mahasiswa dan Pencari Kerja: Sebagai alat bantu untuk mengevaluasi profil diri dan memprediksi peluang mereka dalam mendapatkan penempatan karir yang sesuai.

## Manfaat Implementasi AI
Penerapan Machine Learning dalam prediksi penempatan karir menawarkan beberapa manfaat signifikan:
- Efisiensi Proses Rekrutmen: Mengotomatisasi penyaringan awal, memungkinkan tim SDM fokus pada kandidat yang paling potensial.
- Pengambilan Keputusan Berbasis Data: Mengurangi bias subjektif dalam proses seleksi dengan mengandalkan pola data historis yang tersembunyi.
- Peningkatan Akurasi Prediksi: Model ML dapat mengungkap hubungan kompleks antara berbagai faktor (seperti nilai akademis, pengalaman kerja, dan spesialisasi) yang mungkin terlewat oleh analisis manual.

# Data Understanding
## Sumber Data
Data yang digunakan dalam proyek ini bersumber dari dataset publik yang tersedia di repositori Kaggle, yaitu "Job Placement Dataset". 

## Deskripsi Setiap Fitur (Atribut)
Dataset ini terdiri dari 215 baris data dan 13 atribut, di mana 12 atribut berfungsi sebagai fitur (prediktor) dan satu atribut sebagai target prediksi.
| Atribut                 | Keterangan                                            | Tipe Data (Asli)     |
|-------------------------|-------------------------------------------------------|----------------------|
| gender                  | Jenis kelamin kandidat                                | Object (Kategorik)   |
| ssc_percentage          | Persentase ujian sekolah menengah atas (Kelas 10)     | Float64 (Numerik)    |
| ssc_board               | Dewan pendidikan untuk ujian SSC                      | Object (Kategorik)   |
| hsc_percentage          | Persentase ujian sekolah menengah atas (Kelas 12)     | Float64 (Numerik)    |
| hsc_board               | Dewan pendidikan untuk ujian HSC                      | Object (Kategorik)   |
| hsc_subject             | Mata pelajaran untuk HSC                              | Object (Kategorik)   |
| degree_percentage       | Persentase nilai dalam gelar sarjana                  | Float64 (Numerik)    |
| undergrad_degree        | Jurusan gelar sarjana                                 | Object (Kategorik)   |
| work_experience         | Pengalaman kerja sebelumnya                           | Object (Kategorik)   |
| emp_test_percentage     | Persentase tes bakat                                  | Float64 (Numerik)    |
| specialisation          | Jurusan pasca sarjana (spesialisasi MBA)              | Object (Kategorik)   |
| mba_percent             | Persentase nilai dalam gelar MBA                      | Float64 (Numerik)    |
| status (Target)         | Ditempatkan / Tidak Ditempatkan                       | Object (Kategorik)   |

## Ukuran dan Format Data
- Jumlah Data: 215 sampel (baris)
- Jumlah Fitur: 12 fitur + 1 target
- Format: CSV (Job_Placement_Data.csv)

## Tipe Data dan Target Klasifikasi
- Tipe Data Fitur: Terdiri dari 5 fitur numerik (float64) dan 7 fitur kategorikal (object).
- Target Klasifikasi: Atribut status, yang merupakan klasifikasi biner (binary classification) dengan dua kelas utama: Placed (Ditempatkan) dan Not Placed (Tidak Ditempatkan).

# Exploratory Data Analysis (EDA)
Analisis data eksplorasi dilakukan untuk mendapatkan pemahaman mendalam mengenai karakteristik dan distribusi data.

## Distribusi Variabel Target (status)
Visualisasi distribusi kelas target menunjukkan adanya ketidakseimbangan data (imbalanced data), di mana jumlah mahasiswa yang Placed (ditempatkan) lebih banyak dibandingkan yang Not Placed (tidak ditempatkan). Hal ini perlu diperhatikan karena dapat mempengaruhi kinerja model.

![image](https://github.com/user-attachments/assets/a1057f5b-530c-48b8-8b0b-6f570dee8e15)

## Status Penempatan Berdasarkan Pengalaman Kerja (work_experience)
Dari visualisasi, terlihat jelas bahwa mahasiswa yang memiliki pengalaman kerja (Yes) memiliki tingkat penempatan yang jauh lebih tinggi dibandingkan dengan yang tidak memiliki pengalaman kerja (No). Ini mengindikasikan bahwa work_experience adalah fitur yang sangat prediktif.

![image](https://github.com/user-attachments/assets/79fa2bbe-ee77-4c4c-9592-9af3fce67087)

## Status Penempatan Berdasarkan Spesialisasi MBA (specialisation)
Mahasiswa dengan spesialisasi Marketing & Finance (Mkt&Fin) menunjukkan jumlah penempatan yang lebih tinggi dibandingkan dengan spesialisasi Marketing & HR (Mkt&HR).

![image](https://github.com/user-attachments/assets/a6f9d92d-6713-46d7-9d50-a87e18b665cd)

## Distribusi Persentase Nilai S1 (degree_percentage)
Histogram menunjukkan bahwa persentase nilai S1 untuk mahasiswa yang Placed cenderung terkonsentrasi pada rentang nilai yang lebih tinggi (sekitar 65% ke atas) dibandingkan dengan yang Not Placed. Ini menunjukkan korelasi positif antara nilai S1 dengan peluang penempatan kerja.

![image](https://github.com/user-attachments/assets/3dc5a7a8-e05c-453c-9822-c3cc2b9a25d6)

# Data Preparation
Tahap ini sangat penting untuk memastikan data siap digunakan untuk pemodelan dan tidak mengandung informasi yang dapat mengganggu hasil.

## Pembersihan Data
Pemeriksaan nilai yang hilang (missing values) dilakukan pada seluruh kolom. Hasilnya menunjukkan bahwa dataset ini tidak memiliki nilai yang hilang (null value), sehingga tidak diperlukan proses imputasi atau penghapusan baris.
```
print("\nJumlah Nilai yang Hilang per Kolom:")
print(df.isnull().sum())
```

## Encoding Data Kategorik
Model Machine Learning memerlukan input numerik. Oleh karena itu, semua fitur yang bertipe data object (kategorikal) diubah menjadi numerik menggunakan LabelEncoder dari Scikit-learn. Proses ini mengubah setiap kategori unik dalam sebuah kolom menjadi sebuah angka integer.
- Kolom yang di-encode: gender, ssc_board, hsc_board, hsc_subject, undergrad_degree, work_experience, specialisation, dan status.
```
label_encoder = LabelEncoder()
for col in categorical_cols:
    df_processed[col] = label_encoder.fit_transform(df_processed[col])
```

## Normalisasi / Standardisasi Data Numerik
Dalam proyek ini, proses normalisasi atau standardisasi data numerik tidak dilakukan. Algoritma berbasis pohon seperti Random Forest tidak sensitif terhadap skala fitur, meskipun Regresi Logistik dapat memperoleh manfaat dari proses ini.

## Split Data (Train-Test)
Dataset dibagi menjadi data latih (training data) dan data uji (testing data) dengan rasio 80:20.
- Data Latih: 172 sampel (80%)
- Data Uji: 43 sampel (20%)

Pembagian ini menggunakan stratify=y untuk memastikan proporsi kelas target (status) pada data latih dan data uji sama dengan proporsi pada dataset asli. Penggunaan random_state=42 memastikan hasil pembagian data selalu konsisten setiap kali kode dijalankan.
```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)
```

# Modeling
## Pemilihan Algoritma
Dua algoritma klasifikasi dipilih untuk proyek ini:
- Regresi Logistik (Logistic Regression): Dipilih sebagai model dasar (baseline) karena kesederhanaannya, kemudahan interpretasi, dan performa yang baik untuk masalah klasifikasi biner.
- Random Forest Classifier: Dipilih karena merupakan metode ensemble yang kuat, mampu menangani hubungan non-linear antar fitur, dan cenderung tahan terhadap overfitting. Referensi ilmiah juga menunjukkan bahwa Random Forest seringkali memberikan hasil unggul untuk kasus klasifikasi penempatan karir.

## Implementasi Model
Model dilatih menggunakan data latih (X_train, y_train).

### A. Logistic Regression
```
print("\n--- Melatih Model Logistic Regression ---")
lr_model = LogisticRegression(max_iter=2000, random_state=42)
lr_model.fit(X_train, y_train)
print("Model Logistic Regression berhasil dilatih.")
```
### B. Random Forest Classifier
```
print("\n--- Melatih Model Random Forest Classifier ---")
rf_model = RandomForestClassifier(n_estimators=150, random_state=42)
rf_model.fit(X_train, y_train)
print("Model Random Forest Classifier berhasil dilatih.")
```

# Evaluation
Kinerja model dievaluasi pada data uji menggunakan beberapa metrik standar untuk masalah klasifikasi.

## Confusion Matrix
Confusion matrix digunakan untuk memberikan informasi mengenai prediksi aktual dan prediksi yang dibuat oleh model.
- Logistic Regression:
  - True Positive (Placed): 25
  - True Negative (Not Placed): 10
  - False Positive: 3
  - False Negative: 5
  
![image](https://github.com/user-attachments/assets/9e0c1da3-0dbe-4f22-af14-77e66536a7a0)

- Random Forest Classifier:
  - True Positive (Placed): 28
  - True Negative (Not Placed): 8
  - False Positive: 5
  - False Negative: 2

 ![image](https://github.com/user-attachments/assets/ce7e530a-c711-4170-972d-12eeabcc05a0)

## Metrik Evaluasi: Accuracy, Precision, Recall, F1-score
Metrik ini memberikan gambaran yang lebih komprehensif tentang performa model:
- Accuracy: Seberapa sering model membuat prediksi yang benar secara keseluruhan.
- Precision: Dari semua yang diprediksi 'Placed', berapa persen yang benar-benar 'Placed'.
- Recall (Sensitivity): Dari semua yang seharusnya 'Placed', berapa persen yang berhasil dideteksi oleh model.
- F1-Score: Rata-rata harmonik dari Precision dan Recall.
  
| Model                 | Accuracy   | Precision (Placed)    | Recall (Placed) | F1-score (Placed) |
|-----------------------|------------|-----------------------|-----------------|-------------------|
| Random Forest         | 0.8372     | 0.85                  | 0.93            | 0.89              |
| Logistic Regression   | 0.8140     | 0.89                  | 0.83            | 0.86              |

## Penjelasan Kinerja Model
Berdasarkan tabel perbandingan, Random Forest Classifier menunjukkan kinerja yang sedikit lebih unggul secara keseluruhan dengan akurasi 83.72%, dibandingkan dengan Regresi Logistik (81.40%). Model Random Forest juga memiliki Recall dan F1-score yang lebih tinggi untuk kelas 'Placed', yang berarti model ini lebih baik dalam mengidentifikasi mahasiswa yang benar-benar mendapatkan penempatan kerja. Hasil ini sejalan dengan penelitian referensi yang juga menemukan bahwa Random Forest lebih superior dibandingkan model lain dalam kasus serupa.

# Kesimpulan dan Rekomendasi
## Ringkasan Hasil
Proyek ini berhasil membangun dua model machine learning untuk memprediksi ketepatan penempatan karir mahasiswa. Model Random Forest Classifier memberikan hasil terbaik dengan akurasi sebesar 83.72% pada data uji. Model Regresi Logistik juga menunjukkan performa yang baik sebagai model dasar dengan akurasi 81.40%.

## Apakah Tujuan Proyek Tercapai?
Ya, tujuan proyek tercapai. Model yang dikembangkan mampu memprediksi status penempatan kerja dengan akurasi yang baik, sehingga dapat dijadikan sebagai alat bantu dalam pengambilan keputusan.

## Kelebihan dan Keterbatasan Model
- Kelebihan:
  - Model Random Forest terbukti efektif dan kuat untuk dataset ini.
  - Prosesnya berbasis data, mengurangi bias subjektif.
- Keterbatasan:
  - Ukuran Dataset: Dataset yang digunakan relatif kecil (215 sampel), yang dapat membatasi kemampuan generalisasi model pada data baru yang lebih bervariasi.
  - Encoding: Penggunaan LabelEncoder untuk semua fitur kategorik mungkin bukan pendekatan yang optimal, terutama untuk fitur nominal yang tidak memiliki urutan inheren (misalnya, hsc_subject).

## Rekomendasi Perbaikan
- Dataset: Menggunakan dataset yang lebih besar dan lebih beragam untuk meningkatkan robustisitas model.
- Algoritma: Mengeksplorasi algoritma lain yang juga terbukti baik dalam studi referensi, seperti K-Nearest Neighbors (KNN) dan Support Vector Machine (SVM).
- Feature Engineering & Selection: Melakukan analisis feature importance seperti yang disarankan dalam studi referensi untuk menemukan fitur paling berpengaruh (misalnya ssc_percentage)  dan mungkin menyederhanakan model.
- Metode Encoding: Mencoba metode One-Hot Encoding untuk fitur-fitur nominal untuk menghindari model salah menginterpretasikan urutan pada data.

# Referensi
Berikut adalah sumber ilmiah yang digunakan sebagai acuan dalam laporan ini:
- Nawawi, H. M., Hikmah, A. B., Mustopa, A., & Wijaya, G. (2024). Model Klasifikasi Machine Learning untuk Prediksi Ketepatan Penempatan Karir. Jurnal SAINTEKOM, 14(1), 13-25. https://doi.org/10.33020/saintekom.v14i1.512
- Afiasari, N., Suarna, N., & Rahaningsi, N. (2023). Implementasi Data Mining Transaksi Penjualan Menggunakan Algoritma Clustering dengan Metode K-Means. Jurnal SAINTEKOM, 13(1), 100-110. https://doi.org/10.33020/saintekom.v13i1.402
- Pusporani, E., Qomariyah, S., & Irhamah, I. (2019). Klasifikasi Pasien Penderita Penyakit Liver dengan Pendekatan Machine Learning. Inferensi, 2(1), 25. https://doi.org/10.12962/j27213862.v2i1.6810
- Sihombing, P. R., & Yuliati, I. F. (2021). Penerapan Metode Machine Learning dalam Klasifikasi Risiko Kejadian Berat Badan Lahir Rendah di Indonesia. MATRIK: Jurnal Manajemen, Teknik Informatika Dan Rekayasa Komputer, 20(2), 417–426. https://doi.org/10.30812/matrik.v20i2.1174
- Sukmawati, S., Sulastri, S., Februariyanti, H., & Jananto, A. (2022). Perbandingan Algoritma C4.5 Dan Algoritma Naive Bayes Untuk Klasifikasi Pekerja Migran Indonesia. INFORMATIKA, 14(1), 7. https://doi.org/10.36723/juri.v14i1.280
