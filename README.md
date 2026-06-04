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

---

# Tautan Model ML

Model AI yang digunakan dapat diunduh melalui tautan berikut:

**[Download eye_model_22mei.keras (Google Drive)](https://drive.google.com/file/d/1zBbghewFnN1MpiwN7oHsJB3gthOHTmdC/view?usp=drive_link)**

---

# Petunjuk Setup Environment

## Prasyarat

Pastikan perangkat telah terinstal:
- Python 3.9 atau lebih baru
- Node.js 18 atau lebih baru
- npm atau yarn
- Git

## Clone Repository

```bash
git clone https://github.com/KeisyaNazalia0108/CC26-PSU369-KEMUDI.git
cd CC26-PSU369-KEMUDI
```

---

## Setup Data Scientist

```bash
cd data_scientist
pip install -r requirements.txt
```

---

## Setup AI Engineer

```bash
cd ai_engineer/api_deployment
pip install -r requirements.txt
```

Buat file `.env` di dalam folder `api_deployment/`:

```bash
GEMINI_API_KEY=your_gemini_api_key_here
```

Contoh template tersedia pada file `.env.example`.

---

## Setup Full-Stack Developer

### Frontend

```bash
cd full_stack_developer/frontend/drowsiness-app
npm install
```

### Backend

```bash
cd full_stack_developer/backend
npm install
```

Buat file `.env` di folder backend sesuai template yang tersedia.

---

# Cara Menjalankan Aplikasi

## Data Scientist — Dashboard Streamlit

```bash
cd data_scientist
streamlit run app.py
```

Dashboard akan berjalan pada:

```
http://localhost:8501
```

Dashboard yang sudah dideploy:

```
https://cc26-psu369-kemudi-data-scientist-ttoqnxqw5cvd2tcqkspafq.streamlit.app/
```

---

## AI Engineer — REST API

```bash
cd ai_engineer/api_deployment
uvicorn app:app --reload
```

API akan berjalan pada:

```
http://127.0.0.1:8000
```

Swagger Documentation:

```
http://127.0.0.1:8000/docs
```

API yang sudah dideploy:

```
https://web-production-f21ddd.up.railway.app/docs
```

---

## Full-Stack Developer — Aplikasi Web

### Jalankan Backend

```bash
cd full_stack_developer/backend
npm run dev
```

### Jalankan Frontend

```bash
cd full_stack_developer/frontend/drowsiness-app
npm run dev
```

Aplikasi akan berjalan pada:

```
http://localhost:5173
```

---

# Teknologi yang Digunakan

## Data Science

* Python, Pandas, NumPy, Matplotlib, Streamlit

## Artificial Intelligence

* TensorFlow, Keras, OpenCV, Scikit-Learn, FastAPI

## Full-Stack Development

* React, Vite, Express, JavaScript, REST API

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
│   ├── TensorBoard Results/
│   ├── api_deployment/
│   ├── logs/
│   ├── url api testing/
│   ├── notebook model.ipynb
│   ├── eye_model_22mei.keras
│   └── README.md
│
├── full_stack_developer/
│   ├── frontend/
│   ├── backend/
│   ├── dataset/
│   ├── docs/
│   └── README.md
│
└── README.md
```

---

# Tim Pengembang

## Data Scientist
Bertanggung jawab dalam pengolahan data, analisis, dan dashboard interaktif.

## AI Engineer
- Nicke Damayanti Safitri (CACC008D6X2616)
- Rifka Alya Damayanti (CACC008D6X1433)

Bertanggung jawab dalam pengembangan model Deep Learning, training, evaluasi, dan deployment REST API.

## Full-Stack Developer
Bertanggung jawab dalam pengembangan aplikasi web dan integrasi model AI.

---

# Future Development

* Menambahkan deteksi yawning sebagai indikator tambahan kantuk.
* Mengintegrasikan Eye Aspect Ratio (EAR).
* Meningkatkan performa model pada kondisi low-light.
* Menambahkan dukungan pengguna berkacamata.
* Mengembangkan aplikasi mobile berbasis Android maupun iOS.

---

# Kesimpulan

KEMUDI berhasil mengintegrasikan proses Data Science, Artificial Intelligence, dan Full-Stack Development untuk membangun sistem pemantauan kantuk pengemudi berbasis Computer Vision yang dapat mendukung deteksi dini kantuk dan meningkatkan keselamatan berkendara.
