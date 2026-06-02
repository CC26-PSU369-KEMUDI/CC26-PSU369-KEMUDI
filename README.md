# CC26-PSU369-KEMUDI

# KEMUDI: Sistem Pemantauan Kantuk Pengemudi Berbasis Artificial Intelligence

KEMUDI (Kendali Mengemudi untuk Deteksi Kantuk) merupakan proyek Capstone yang dikembangkan untuk membantu mendeteksi indikasi awal kantuk pengemudi menggunakan teknologi Artificial Intelligence dan Computer Vision.

Proyek ini mengusung tema **Healthy Lives & Well-being** dengan tujuan meningkatkan keselamatan berkendara melalui sistem pemantauan kondisi mata pengemudi secara otomatis. Sistem dirancang untuk mendeteksi kondisi mata terbuka (*Open Eye*) dan tertutup (*Closed Eye*) sebagai indikator awal kantuk sehingga dapat memberikan peringatan sebelum terjadi risiko kecelakaan akibat kelelahan atau *microsleep*.

---

# Tim Pengembang

Proyek KEMUDI dikembangkan melalui kolaborasi tiga Learning Path yang saling terintegrasi untuk menghasilkan sistem deteksi kantuk pengemudi berbasis Artificial Intelligence dan Computer Vision.

## 1. Data Scientist

Learning Path Data Scientist bertanggung jawab dalam mengolah data, melakukan analisis, serta menghasilkan insight yang menjadi dasar pengembangan model Artificial Intelligence.

### Tanggung Jawab

* Mengidentifikasi permasalahan dan menentukan solusi yang akan dikembangkan.
* Melakukan proses Data Wrangling yang mencakup Gathering Data, Assessing Data, dan Cleaning Data.
* Mendefinisikan Business Questions yang dapat diukur.
* Melakukan Exploratory Data Analysis (EDA).
* Membuat visualisasi data dan explanatory analysis.
* Menyusun Data Dictionary.
* Melakukan Feature Engineering.
* Mengimplementasikan A/B Testing menggunakan Python.
* Mengembangkan dashboard interaktif menggunakan Streamlit.
* Melakukan deployment dashboard ke Streamlit Cloud.
* Menyusun laporan teknis proyek.

### Hasil yang Dihasilkan

* Dataset siap digunakan oleh model AI.
* Insight dan hasil analisis data.
* Dashboard interaktif Data Science.
* Hasil A/B Testing dan Latency Testing.
* Dokumentasi teknis proyek.

---

## 2. AI Engineer

Learning Path AI Engineer bertanggung jawab dalam membangun, melatih, mengevaluasi, dan mengoptimalkan model Artificial Intelligence yang digunakan untuk mendeteksi kondisi mata terbuka dan tertutup.

### Tanggung Jawab

* Mengembangkan model Deep Learning menggunakan TensorFlow Functional API atau Model Subclassing.
* Menyesuaikan arsitektur model dengan kebutuhan bisnis dan karakteristik dataset.
* Mengimplementasikan komponen kustom seperti Custom Layer, Custom Callback, atau Custom Loss Function.
* Melatih dan mengevaluasi performa model.
* Melakukan optimasi model agar siap digunakan pada lingkungan produksi.
* Mengekspor model ke format TensorFlow SavedModel atau Keras.
* Membuat pipeline inference untuk kebutuhan integrasi aplikasi.

### Hasil yang Dihasilkan

* Model klasifikasi kondisi mata Open dan Closed.
* Model siap produksi dalam format TensorFlow.
* Script inference model.
* Dokumentasi pengembangan dan evaluasi model.

---

## 3. Full-Stack Developer

Learning Path Full-Stack Developer bertanggung jawab dalam membangun aplikasi web, REST API, serta mengintegrasikan model AI ke dalam sistem yang dapat digunakan oleh pengguna.

### Tanggung Jawab

* Mengembangkan frontend aplikasi menggunakan React.
* Menggunakan Vite sebagai module bundler.
* Mengembangkan RESTful API menggunakan Express.
* Mengimplementasikan komunikasi frontend dan backend menggunakan networking call.
* Mengintegrasikan model AI ke dalam aplikasi.
* Mengimplementasikan webcam untuk deteksi kantuk secara real-time.
* Membuat mockup dan desain antarmuka aplikasi.
* Mengembangkan tampilan yang responsif pada berbagai perangkat.
* Melakukan deployment aplikasi ke layanan hosting.

### Hasil yang Dihasilkan

* Frontend aplikasi KEMUDI.
* Backend dan REST API.
* Integrasi webcam dan model AI.
* Aplikasi web yang dapat digunakan secara real-time.

---

# Integrasi Antar Learning Path

Ketiga Learning Path bekerja secara terintegrasi:

1. Data Scientist menyiapkan data, insight, dashboard, dan hasil eksperimen.
2. AI Engineer mengembangkan model klasifikasi berdasarkan data yang telah diproses.
3. Full-Stack Developer mengintegrasikan model ke dalam aplikasi web sehingga dapat digunakan secara real-time oleh pengguna.

Kolaborasi ketiga Learning Path menghasilkan sistem KEMUDI yang mampu mendukung deteksi dini kantuk pengemudi melalui teknologi Artificial Intelligence dan Computer Vision.

---

# Permasalahan yang Diangkat

Kantuk saat berkendara merupakan salah satu faktor yang meningkatkan risiko kecelakaan lalu lintas. Banyak pengemudi mengalami kelelahan atau microsleep tanpa menyadarinya sehingga berpotensi menyebabkan hilangnya konsentrasi selama beberapa detik.

KEMUDI dikembangkan untuk membantu mendeteksi indikasi awal kantuk melalui pemantauan kondisi mata pengemudi menggunakan kamera perangkat dan model Artificial Intelligence.

---

# Solusi yang Dikembangkan

KEMUDI memanfaatkan teknologi Computer Vision dan Deep Learning untuk mengidentifikasi kondisi mata pengemudi.

Alur sistem:

1. Kamera menangkap wajah pengguna secara real-time.
2. Sistem mendeteksi area mata.
3. Model AI mengklasifikasikan kondisi mata menjadi Open atau Closed.
4. Sistem menghitung durasi mata tertutup.
5. Jika terindikasi kantuk, sistem memberikan peringatan kepada pengguna.

---

# Struktur Repository

```text
CC26-PSU369-KEMUDI/
│
├── data_scientist/
│   ├── app.py
│   ├── requirements.txt
│   ├── README.md
│   ├── streamlit_assets/
│   └── docs/
│
├── ai_engineer/
│   ├── model/
│   ├── notebooks/
│   ├── inference/
│   └── README.md
│
├── full_stack_developer/
│   ├── frontend/
│   ├── backend/
│   └── README.md
│
└── README.md
```

---

# Teknologi yang Digunakan

## Data Science

* Python
* Pandas
* NumPy
* Matplotlib
* Streamlit

## Artificial Intelligence

* TensorFlow
* Keras
* OpenCV
* Scikit-Learn

## Full-Stack Development

* React
* Vite
* Express
* JavaScript
* REST API
* MediaDevices.getUserMedia()

---

# Dokumentasi Learning Path

## Data Scientist

Dashboard Streamlit:

https://cc26-psu369-kemudi-data-scientist-ttoqnxqw5cvd2tcqkspafq.streamlit.app/

Dokumentasi lengkap dapat dilihat pada folder:

```text
data_scientist/
```

---

## AI Engineer

Dokumentasi lengkap dapat dilihat pada folder:

```text
ai_engineer/
```

---

## Full-Stack Developer

Dokumentasi lengkap dapat dilihat pada folder:

```text
full_stack_developer/
```

---

# Future Development

Beberapa pengembangan yang dapat dilakukan pada versi berikutnya:

* Menambahkan deteksi yawning (menguap) sebagai indikator tambahan kantuk.
* Mengintegrasikan Eye Aspect Ratio (EAR) untuk meningkatkan akurasi deteksi.
* Meningkatkan performa model pada kondisi pencahayaan rendah dan pengguna berkacamata.
* Mengintegrasikan sistem dengan perangkat mobile agar dapat digunakan secara lebih luas.
* Mengembangkan monitoring performa model secara real-time setelah sistem diimplementasikan.
---

# Kesimpulan

KEMUDI berhasil mengintegrasikan proses Data Science, Artificial Intelligence, dan Full-Stack Development untuk membangun sistem pemantauan kantuk pengemudi berbasis Computer Vision.

Melalui analisis kondisi mata terbuka dan tertutup, sistem mampu mendukung deteksi dini kantuk pengemudi dan memiliki potensi untuk meningkatkan keselamatan berkendara pada implementasi dunia nyata.
