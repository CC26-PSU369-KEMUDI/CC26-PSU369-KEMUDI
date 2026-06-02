# CC26-PSU369-KEMUDI

# KEMUDI: Sistem Pemantauan Kantuk Pengemudi Berbasis Artificial Intelligence

KEMUDI (Kendali Mengemudi untuk Deteksi Kantuk) merupakan proyek Capstone yang dikembangkan untuk membantu mendeteksi indikasi awal kantuk pengemudi menggunakan teknologi Artificial Intelligence dan Computer Vision.

Proyek ini mengusung tema **Healthy Lives & Well-Being** dengan tujuan meningkatkan keselamatan berkendara melalui sistem pemantauan kondisi mata pengemudi secara otomatis. Sistem dirancang untuk mendeteksi kondisi mata terbuka (*Open Eye*) dan tertutup (*Closed Eye*) sebagai indikator awal kantuk sehingga dapat memberikan peringatan sebelum terjadi risiko kecelakaan akibat kelelahan maupun *microsleep*.

---

# Latar Belakang

Kecelakaan lalu lintas masih menjadi salah satu penyebab utama cedera dan kematian di berbagai negara. Salah satu faktor yang sering menjadi penyebab kecelakaan adalah menurunnya konsentrasi akibat kelelahan dan kantuk saat berkendara.

Fenomena *microsleep*, yaitu kondisi ketika seseorang tertidur selama beberapa detik tanpa disadari, dapat menyebabkan hilangnya kendali kendaraan dalam waktu singkat. Meskipun durasinya sangat singkat, dampaknya dapat berakibat fatal.

Berdasarkan permasalahan tersebut, tim mengembangkan KEMUDI sebagai sistem deteksi dini kantuk pengemudi berbasis Artificial Intelligence dan Computer Vision yang memanfaatkan kondisi mata sebagai indikator utama.

---

# Permasalahan yang Diangkat

Permasalahan utama yang ingin diselesaikan dalam proyek ini adalah:

* Sulitnya mendeteksi kondisi kantuk pengemudi secara dini.
* Tingginya risiko kecelakaan akibat kelelahan dan microsleep.
* Belum tersedianya solusi yang mudah diakses masyarakat luas tanpa memerlukan perangkat khusus yang mahal.
* Perlunya sistem pemantauan yang dapat bekerja secara otomatis dan real-time.

---

# Solusi yang Dikembangkan

KEMUDI memanfaatkan teknologi Computer Vision dan Deep Learning untuk mengidentifikasi kondisi mata pengemudi.

Alur kerja sistem:

1. Kamera menangkap wajah pengguna secara real-time.
2. Sistem mendeteksi area mata pengguna.
3. Model AI mengklasifikasikan kondisi mata menjadi Open atau Closed.
4. Sistem menghitung durasi mata tertutup secara berkelanjutan.
5. Jika terindikasi kantuk, sistem memberikan peringatan kepada pengguna.

Keunggulan solusi:

* Tidak memerlukan perangkat tambahan khusus.
* Dapat menggunakan kamera bawaan laptop maupun smartphone.
* Berbasis web sehingga mudah diakses.
* Mendukung implementasi real-time.
* Biaya implementasi relatif rendah.

---

# Tim Pengembang

Proyek KEMUDI dikembangkan melalui kolaborasi tiga Learning Path yang saling terintegrasi.

## 1. Data Scientist

Learning Path Data Scientist bertanggung jawab dalam mengolah data, melakukan analisis, serta menghasilkan insight yang menjadi dasar pengembangan model Artificial Intelligence.

### Tanggung Jawab

* Mengidentifikasi permasalahan dan menentukan solusi yang akan dikembangkan.
* Melakukan Data Wrangling (Gathering, Assessing, Cleaning Data).
* Mendefinisikan Business Questions.
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

Learning Path AI Engineer bertanggung jawab dalam membangun, melatih, mengevaluasi, dan mengoptimalkan model Artificial Intelligence.

### Tanggung Jawab

* Mengembangkan model Deep Learning menggunakan TensorFlow.
* Menyesuaikan arsitektur model dengan kebutuhan bisnis.
* Mengimplementasikan komponen kustom seperti Custom Callback, Custom Layer, atau Custom Loss Function.
* Melatih dan mengevaluasi model.
* Mengoptimalkan model agar siap digunakan pada lingkungan produksi.
* Mengekspor model ke format TensorFlow SavedModel atau Keras.
* Mengembangkan pipeline inference.

### Hasil yang Dihasilkan

* Model klasifikasi kondisi mata Open dan Closed.
* Model siap produksi.
* Script inference.
* Dokumentasi pelatihan dan evaluasi model.

---

## 3. Full-Stack Developer

Learning Path Full-Stack Developer bertanggung jawab dalam membangun aplikasi web serta mengintegrasikan model AI ke dalam sistem.

### Tanggung Jawab

* Mengembangkan frontend menggunakan React.
* Menggunakan Vite sebagai module bundler.
* Mengembangkan REST API menggunakan Express.
* Mengimplementasikan komunikasi frontend dan backend.
* Mengintegrasikan model AI ke dalam aplikasi.
* Mengimplementasikan webcam menggunakan MediaDevices.getUserMedia().
* Membuat mockup dan desain antarmuka aplikasi.
* Mengembangkan tampilan yang responsif.
* Melakukan deployment aplikasi.

### Hasil yang Dihasilkan

* Frontend aplikasi KEMUDI.
* Backend dan REST API.
* Integrasi webcam dan model AI.
* Aplikasi web siap digunakan secara real-time.

---

# Integrasi Antar Learning Path

Ketiga Learning Path bekerja secara terintegrasi:

1. Data Scientist menyiapkan data, analisis, dashboard, dan hasil eksperimen.
2. AI Engineer membangun model klasifikasi berdasarkan dataset yang telah diproses.
3. Full-Stack Developer mengintegrasikan model ke dalam aplikasi web.
4. Sistem melakukan deteksi kondisi mata secara real-time melalui webcam.
5. Hasil prediksi digunakan sebagai indikator awal kantuk pengemudi.

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

# Dokumentasi Learning Path

## Data Scientist

Dashboard Streamlit:

https://cc26-psu369-kemudi-data-scientist-ttoqnxqw5cvd2tcqkspafq.streamlit.app/

Dokumentasi lengkap tersedia pada folder:

```text
data_scientist/
```

## AI Engineer

Dokumentasi lengkap tersedia pada folder:

```text
ai_engineer/
```

## Full-Stack Developer

Dokumentasi lengkap tersedia pada folder:

```text
full_stack_developer/
```

---

# Cara Mereplikasi Proyek

## 1. Clone Repository

```bash
git clone https://github.com/KeisyaNazalia0108/CC26-PSU369-KEMUDI.git
cd CC26-PSU369-KEMUDI
```

---

## Data Scientist

Masuk ke folder Data Scientist:

```bash
cd data_scientist
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Jalankan dashboard:

```bash
streamlit run app.py
```

Dashboard akan berjalan pada:

```text
http://localhost:8501
```

---

## AI Engineer

Dokumentasi lengkap tersedia pada folder:

```text
ai_engineer/
```

Bagian ini akan dilengkapi oleh tim AI Engineer, termasuk:

* Training pipeline
* Hyperparameter
* Arsitektur model
* Evaluasi model
* Cara menjalankan inference

---

## Full-Stack Developer

Dokumentasi lengkap tersedia pada folder:

```text
full_stack_developer/
```

Bagian ini akan dilengkapi oleh tim Full-Stack Developer, termasuk:

* Setup frontend
* Setup backend
* Environment variables
* Integrasi API
* Deployment aplikasi

---

# Future Development

Beberapa pengembangan yang dapat dilakukan pada versi berikutnya:

* Menambahkan deteksi yawning (menguap) sebagai indikator tambahan kantuk.
* Mengintegrasikan Eye Aspect Ratio (EAR).
* Meningkatkan performa model pada kondisi low-light.
* Menambahkan dukungan pengguna berkacamata.
* Mengembangkan monitoring performa model secara real-time.
* Menyediakan riwayat tingkat kantuk pengguna.
* Mengembangkan aplikasi mobile berbasis Android maupun iOS.

---

# Kesimpulan

KEMUDI berhasil mengintegrasikan proses Data Science, Artificial Intelligence, dan Full-Stack Development untuk membangun sistem pemantauan kantuk pengemudi berbasis Computer Vision.

Melalui analisis kondisi mata terbuka dan tertutup, sistem mampu mendukung deteksi dini kantuk pengemudi dan memiliki potensi untuk meningkatkan keselamatan berkendara pada implementasi dunia nyata.
