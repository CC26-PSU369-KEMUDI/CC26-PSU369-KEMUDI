# KEMUDI – Data Science Dashboard

## Tentang Proyek

KEMUDI (Kendali Mengemudi untuk Deteksi Kantuk) merupakan proyek berbasis Computer Vision yang dikembangkan untuk membantu mendeteksi indikasi awal kantuk pengemudi melalui analisis kondisi mata (Open dan Closed). Proyek ini mendukung tema **Healthy Lives & Well-being** dengan tujuan meningkatkan keselamatan berkendara melalui sistem pemantauan kantuk yang dapat diimplementasikan secara real-time.

Repository ini berisi seluruh hasil pekerjaan Learning Path Data Scientist, mulai dari proses data wrangling, exploratory data analysis (EDA), feature engineering, evaluasi model, A/B testing, latency testing, hingga pengembangan dashboard interaktif menggunakan Streamlit.

---

## Latar Belakang

Kantuk saat berkendara merupakan salah satu faktor yang dapat meningkatkan risiko kecelakaan lalu lintas. Salah satu fenomena yang sering terjadi adalah *microsleep*, yaitu kondisi ketika seseorang tertidur dalam waktu sangat singkat tanpa disadari. Meskipun hanya berlangsung beberapa detik, kondisi ini dapat menyebabkan hilangnya konsentrasi saat mengemudi.

Berdasarkan permasalahan tersebut, proyek KEMUDI dikembangkan untuk mengeksplorasi apakah kondisi mata terbuka (*Open*) dan tertutup (*Closed*) dapat digunakan sebagai indikator awal dalam sistem deteksi kantuk berbasis Computer Vision.

---

## Business Understanding

### Business Questions

1. Apakah kondisi mata terbuka dan tertutup dapat digunakan sebagai indikator awal dalam sistem deteksi kantuk pengemudi?
2. Bagaimana karakteristik dan keseimbangan dataset yang digunakan?
3. Apakah preprocessing citra mampu menghasilkan data yang siap digunakan oleh model klasifikasi?
4. Seberapa baik performa model dalam mengklasifikasikan kondisi mata Open dan Closed?
5. Threshold prediksi berapa yang paling optimal untuk digunakan?
6. Apakah model memiliki latency yang cukup rendah untuk mendukung implementasi real-time?

---

## Dataset

### Sumber Dataset

Dataset diperoleh dari sumber publik Kaggle yang berisi citra mata terbuka dan tertutup.

### Karakteristik Dataset

* Total data: 4.000 gambar
* Kelas Open: 2.000 gambar
* Kelas Closed: 2.000 gambar
* Dataset seimbang (balanced dataset)
* Tidak ditemukan missing value
* Tidak ditemukan duplicate image path
* Tidak ditemukan corrupt image

---

## Data Wrangling

### 1. Gathering Data

Mengumpulkan dataset citra mata Open dan Closed dari sumber publik.

### 2. Assessing Data

Melakukan evaluasi terhadap:

* Distribusi kelas
* Missing value
* Duplicate image path
* Corrupt image
* Variasi ukuran gambar

### 3. Cleaning Data

Melakukan pembersihan data dengan memastikan seluruh gambar valid dan siap digunakan pada tahap berikutnya.

---

## Exploratory Data Analysis (EDA)

Analisis eksploratif dilakukan untuk memahami karakteristik dataset sebelum digunakan dalam proses pemodelan.

Hasil EDA menunjukkan bahwa:

* Dataset memiliki distribusi kelas yang seimbang.
* Tidak ditemukan masalah kualitas data yang signifikan.
* Seluruh data layak digunakan untuk proses training dan evaluasi model.
* Ukuran gambar bervariasi sehingga diperlukan preprocessing untuk menyeragamkan dimensi input.

---

## Feature Engineering

Feature engineering dilakukan melalui preprocessing citra untuk menghasilkan input yang konsisten dan sesuai dengan kebutuhan model CNN.

Tahapan preprocessing:

1. Resize gambar menjadi 96 × 96 piksel.
2. Konversi gambar menjadi grayscale.
3. Normalisasi nilai piksel ke rentang 0–1.
4. Penyesuaian dimensi input menjadi format yang sesuai dengan model CNN.
5. Pembagian dataset menggunakan stratified split.

### Data Split

| Subset     | Proporsi |
| ---------- | -------- |
| Train      | 70%      |
| Validation | 15%      |
| Test       | 15%      |

---

## Model Evaluation

Evaluasi model dilakukan menggunakan test set untuk mengukur kemampuan klasifikasi kondisi mata Open dan Closed.

### Metrik Evaluasi

| Metrik    | Nilai  |
| --------- | ------ |
| Accuracy  | 1.0000 |
| Precision | 1.0000 |
| Recall    | 1.0000 |
| F1-Score  | 1.0000 |

### Confusion Matrix

Hasil confusion matrix menunjukkan seluruh data pada test set berhasil diklasifikasikan dengan benar sehingga tidak ditemukan False Positive maupun False Negative pada proses evaluasi.

---

## Threshold Analysis

Threshold digunakan untuk mengubah probabilitas hasil prediksi menjadi label klasifikasi.

Eksperimen dilakukan untuk membandingkan:

* Threshold default = 0.5
* Threshold hasil analisis validation set

Hasil menunjukkan kedua threshold menghasilkan performa yang setara sehingga threshold 0.5 dipilih sebagai threshold final karena lebih sederhana dan mudah diinterpretasikan.

---

## A/B Testing

A/B Testing dilakukan untuk membandingkan dua strategi threshold:

### Strategy A

Threshold = 0.5

### Strategy B

Threshold hasil analisis validation set

### Hasil

Kedua strategi menghasilkan nilai Accuracy, Precision, Recall, dan F1-Score yang sama sehingga tidak terdapat perbedaan performa yang signifikan.

---

## Latency Testing

Latency testing dilakukan untuk mengukur kecepatan inferensi model.

Tujuan pengujian:

* Mengukur waktu prediksi rata-rata per gambar.
* Mengestimasi Frame Per Second (FPS).
* Mengevaluasi potensi implementasi real-time.

Hasil pengujian menunjukkan bahwa model memiliki latency yang rendah dan berpotensi digunakan dalam sistem pemantauan kantuk secara real-time.

---

## Dashboard Interaktif

Dashboard dikembangkan menggunakan Streamlit untuk menampilkan hasil analisis secara interaktif.

### Live Dashboard

https://cc26-psu369-kemudi-eoeh3ydqy8zbn9s7ie66sh.streamlit.app/

### Fitur Dashboard

* Project Overview
* Data Insight
* Feature Engineering
* Model Evaluation
* Threshold Analysis
* A/B Testing
* Latency Testing
* Conclusion

---

## Struktur Repository

```text
Data Scientist/
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
    └── screenshots/
```

---

## Menjalankan Dashboard Secara Lokal

### Clone Repository

```bash
git clone <repository-url>
cd "Data Scientist"
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Jalankan Streamlit

```bash
streamlit run app.py
```

Dashboard akan berjalan pada browser lokal.

---

## Technology Stack

* Python
* Streamlit
* Pandas
* NumPy
* Matplotlib
* TensorFlow
* OpenCV
* Scikit-Learn

---

## Scope Learning Path Data Scientist

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

Integrasi webcam, backend API, serta aplikasi utama dikembangkan secara terpisah oleh anggota tim pada learning path lainnya.

---

## Kesimpulan

Berdasarkan hasil analisis, kondisi mata Open dan Closed dapat digunakan sebagai indikator awal untuk mendukung sistem deteksi kantuk pengemudi berbasis Computer Vision. Model menunjukkan performa yang sangat baik pada dataset yang digunakan dan memiliki potensi untuk diterapkan pada sistem pemantauan kantuk secara real-time setelah melalui pengujian lebih lanjut pada kondisi dunia nyata.
