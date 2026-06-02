# KEMUDI – Data Science Dashboard

## Tentang Proyek

KEMUDI (Kendali Mengemudi untuk Deteksi Kantuk) merupakan proyek berbasis Computer Vision yang dikembangkan untuk membantu mendeteksi indikasi awal kantuk pengemudi melalui analisis kondisi mata (*Open* dan *Closed*). Proyek ini mendukung tema **Healthy Lives & Well-being** dengan tujuan meningkatkan keselamatan berkendara melalui sistem pemantauan kantuk yang dapat diimplementasikan secara real-time.

Repository ini berisi seluruh hasil pekerjaan Learning Path Data Scientist, mulai dari proses data wrangling, exploratory data analysis (EDA), feature engineering, evaluasi model, A/B testing, latency testing, hingga pengembangan dashboard interaktif menggunakan Streamlit.

---

# Latar Belakang

Kantuk saat berkendara merupakan salah satu faktor yang dapat meningkatkan risiko kecelakaan lalu lintas. Salah satu fenomena yang sering terjadi adalah *microsleep*, yaitu kondisi ketika seseorang tertidur dalam waktu sangat singkat tanpa disadari. Meskipun hanya berlangsung beberapa detik, kondisi ini dapat menyebabkan hilangnya konsentrasi saat mengemudi.

Berdasarkan permasalahan tersebut, proyek KEMUDI dikembangkan untuk mengeksplorasi apakah kondisi mata terbuka (*Open*) dan tertutup (*Closed*) dapat digunakan sebagai indikator awal dalam sistem deteksi kantuk berbasis Computer Vision.

---

# Business Understanding

## Business Questions

1. Apakah kondisi mata terbuka dan tertutup dapat digunakan sebagai indikator awal dalam mendeteksi kantuk pengemudi?
2. Bagaimana karakteristik dan keseimbangan dataset (*Open* vs *Closed*) memengaruhi performa model?
3. Apakah feature engineering melalui preprocessing citra mampu menghasilkan input gambar yang seragam dan siap digunakan untuk model klasifikasi?
4. Seberapa baik performa model dalam mengklasifikasikan kondisi mata berdasarkan metrik evaluasi seperti Accuracy, Precision, Recall, F1-Score, dan Confusion Matrix?
5. Threshold prediksi berapa yang paling optimal untuk membedakan kondisi mata *Open* dan *Closed* berdasarkan validation set?
6. Apakah model memiliki latency yang cukup rendah untuk mendukung sistem deteksi kantuk secara real-time?

---

# Dataset

## Sumber Dataset

Dataset diperoleh dari sumber publik Kaggle yang berisi citra mata terbuka (*Open Eye*) dan tertutup (*Closed Eye*).

## Karakteristik Dataset

* Total data: 4.000 gambar
* Kelas Open: 2.000 gambar
* Kelas Closed: 2.000 gambar
* Dataset seimbang (*balanced dataset*)
* Tidak ditemukan missing value
* Tidak ditemukan duplicate image path
* Tidak ditemukan corrupt image

---

# Data Wrangling

## 1. Gathering Data

Mengumpulkan dataset citra mata Open dan Closed dari sumber publik yang relevan dengan kebutuhan pengembangan sistem deteksi kantuk.

## 2. Assessing Data

Melakukan evaluasi terhadap:

* Distribusi kelas
* Missing value
* Duplicate image path
* Corrupt image
* Variasi ukuran gambar

## 3. Cleaning Data

Melakukan pembersihan data dengan memastikan seluruh gambar valid, dapat dibaca oleh sistem, dan siap digunakan pada tahap analisis serta pemodelan.

---

# Exploratory Data Analysis (EDA)

Analisis eksploratif dilakukan untuk memahami karakteristik dataset sebelum digunakan dalam proses pemodelan.

## Hasil EDA

* Dataset memiliki distribusi kelas yang seimbang.
* Tidak ditemukan masalah kualitas data yang signifikan.
* Seluruh data layak digunakan untuk proses training dan evaluasi model.
* Ukuran gambar bervariasi sehingga diperlukan preprocessing untuk menyeragamkan dimensi input.

---

# Feature Engineering

Feature engineering dilakukan melalui preprocessing citra untuk menghasilkan input yang konsisten dan sesuai dengan kebutuhan model CNN.

## Tahapan Preprocessing

1. Resize gambar menjadi 96 × 96 piksel.
2. Konversi gambar menjadi grayscale.
3. Normalisasi nilai piksel ke rentang 0–1.
4. Penyesuaian dimensi input sesuai kebutuhan model CNN.
5. Pembagian dataset menggunakan stratified split.

## Data Split

| Subset     | Proporsi |
| ---------- | -------- |
| Train      | 70%      |
| Validation | 15%      |
| Test       | 15%      |

---

# Model Evaluation

Evaluasi model dilakukan menggunakan test set untuk mengukur kemampuan klasifikasi kondisi mata Open dan Closed.

## Metrik Evaluasi

| Metrik    | Nilai  |
| --------- | ------ |
| Accuracy  | 1.0000 |
| Precision | 1.0000 |
| Recall    | 1.0000 |
| F1-Score  | 1.0000 |

## Confusion Matrix

Hasil confusion matrix menunjukkan seluruh data pada test set berhasil diklasifikasikan dengan benar sehingga tidak ditemukan False Positive maupun False Negative selama proses evaluasi.

---

# Threshold Analysis

Threshold digunakan untuk mengubah probabilitas hasil prediksi menjadi label klasifikasi.

Eksperimen dilakukan untuk membandingkan:

* Threshold default = 0.5
* Threshold hasil analisis validation set

## Hasil

Kedua threshold menghasilkan performa yang setara sehingga threshold 0.5 dipilih sebagai threshold final karena lebih sederhana, stabil, dan mudah diinterpretasikan.

---

# A/B Testing

A/B Testing dilakukan untuk membandingkan dua strategi threshold.

## Strategy A

Threshold = 0.5

## Strategy B

Threshold hasil analisis validation set

## Hasil

Kedua strategi menghasilkan nilai Accuracy, Precision, Recall, dan F1-Score yang sama sehingga tidak terdapat perbedaan performa yang signifikan.

---

# Latency Testing

Latency testing dilakukan untuk mengukur kecepatan inferensi model.

## Tujuan Pengujian

* Mengukur waktu prediksi rata-rata per gambar.
* Mengestimasi Frame Per Second (FPS).
* Mengevaluasi potensi implementasi real-time.

## Hasil

Model menunjukkan latency yang rendah dan estimasi FPS yang tinggi sehingga memiliki potensi untuk digunakan pada sistem deteksi kantuk secara real-time.

---

# Dashboard Interaktif

Dashboard dikembangkan menggunakan Streamlit untuk menampilkan hasil analisis secara interaktif.

## Live Dashboard

https://cc26-psu369-kemudi-data-scientist-ttoqnxqw5cvd2tcqkspafq.streamlit.app/

## Fitur Dashboard

* Project Overview
* Data Insight
* Feature Engineering
* Model Evaluation
* Threshold Analysis
* A/B Testing
* Latency Testing
* Conclusion

---

# Struktur Repository

```text
data_scientist/
│
├── app.py
├── requirements.txt
├── README.md
│
├── streamlit_assets/
│   ├── ab_testing.csv
│   ├── class_counts.csv
│   ├── confusion_summary.csv
│   ├── data_dictionary.csv
│   ├── eda_summary.csv
│   ├── latency_result.csv
│   ├── latency_summary.csv
│   ├── model_metrics.csv
│   ├── preprocessing_summary.csv
│   ├── split_distribution.csv
│   └── threshold_decision.csv
│
└── docs/
    ├── screenshots/
    │   ├── overview.png
    │   ├── data_insight.png
    │   ├── feature_engineering.png
    │   ├── model_evaluation.png
    │   ├── ab_testing_dan_latency.png
    │   └── conclusion.png
    │
    ├── Laporan_Teknis_Komprehensif_CC26-PSU369/
    └── Notebook_Lengkap_Data_Scientist/
```

---

# Replikasi Proyek

Langkah-langkah berikut dapat digunakan untuk mereplikasi proses analisis dan dashboard Data Science pada proyek KEMUDI.

## 1. Clone Repository

```bash
git clone https://github.com/KeisyaNazalia0108/CC26-PSU369-KEMUDI.git
cd CC26-PSU369-KEMUDI/data_scientist
```

## 2. Install Dependencies

Pastikan Python 3.10 atau versi yang lebih baru telah terpasang.

```bash
pip install -r requirements.txt
```

## 3. Pastikan Struktur Folder Sesuai

Pastikan seluruh file CSV berada di folder `streamlit_assets/` sesuai struktur repository.

## 4. Menjalankan Dashboard

```bash
streamlit run app.py
```

Dashboard akan tersedia pada browser lokal:

```text
http://localhost:8501
```

---

# Replikasi Analisis Data

Tahapan analisis yang dilakukan pada proyek ini dapat direplikasi melalui langkah berikut:

1. Mengumpulkan dataset citra mata Open dan Closed.
2. Melakukan Data Assessing untuk memeriksa kualitas data.
3. Melakukan Data Cleaning dan validasi dataset.
4. Menyusun Data Dictionary.
5. Melakukan Exploratory Data Analysis (EDA).
6. Melakukan Feature Engineering melalui preprocessing citra.
7. Melakukan evaluasi model menggunakan metrik klasifikasi.
8. Melakukan Threshold Analysis.
9. Melakukan A/B Testing.
10. Melakukan Latency Testing.
11. Menyajikan seluruh hasil analisis melalui dashboard Streamlit.

---

# Dokumentasi Tambahan

Repository ini juga menyediakan dokumentasi pendukung untuk memudahkan proses reproduksi dan evaluasi proyek:

* Laporan Teknis Komprehensif
* Notebook Lengkap Data Scientist
* Screenshot Dashboard Streamlit
* Dataset hasil pengolahan dan evaluasi model

---

# Technology Stack

* Python
* Streamlit
* Pandas
* NumPy
* Matplotlib
* TensorFlow
* OpenCV
* Scikit-Learn

---

# Scope Learning Path Data Scientist

Repository ini berfokus pada pekerjaan Learning Path Data Scientist yang meliputi:

* Data Wrangling
* Exploratory Data Analysis (EDA)
* Data Visualization
* Feature Engineering
* Model Evaluation
* Threshold Analysis
* A/B Testing
* Latency Testing
* Dashboard Development
* Dashboard Deployment

Integrasi webcam, backend API, model deployment, dan aplikasi utama dikembangkan secara terpisah oleh anggota tim pada learning path lainnya.

---

# Kesimpulan

Berdasarkan hasil analisis, kondisi mata Open dan Closed dapat digunakan sebagai indikator awal untuk mendukung sistem deteksi kantuk pengemudi berbasis Computer Vision. Model menunjukkan performa yang sangat baik pada dataset yang digunakan serta memiliki latency yang rendah sehingga berpotensi diterapkan pada sistem pemantauan kantuk secara real-time setelah melalui pengujian lebih lanjut pada kondisi dunia nyata.
