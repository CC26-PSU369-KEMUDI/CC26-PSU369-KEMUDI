# AI Engineering - KEMUDI

## Deskripsi

KEMUDI (Kendaraan Mengemudi Aman dengan Deteksi Kantuk) merupakan sistem deteksi kantuk pengemudi berbasis Artificial Intelligence yang memanfaatkan citra mata untuk mengidentifikasi kondisi pengemudi secara real-time.

Pada learning path AI Engineering, dilakukan pengembangan model Deep Learning, proses training dan evaluasi model, visualisasi performa menggunakan TensorBoard, integrasi Generative AI, serta deployment model melalui REST API berbasis FastAPI.

---

## Teknologi yang Digunakan

| Komponen             | Teknologi                 |
| -------------------- | ------------------------- |
| Deep Learning        | TensorFlow / Keras        |
| Model Training       | TensorFlow Functional API |
| Custom Training Loop | tf.GradientTape           |
| Monitoring Training  | TensorBoard               |
| REST API             | FastAPI                   |
| Deployment           | Railway                   |
| Generative AI        | Gemini API                |
| Bahasa Pemrograman   | Python                    |

---

## Tautan Model ML

Model yang telah dilatih dapat diunduh melalui tautan berikut:

**[Download eye_model_22mei.keras (Google Drive)](https://drive.google.com/file/d/1zBbghewFnN1MpiwN7oHsJB3gthOHTmdC/view?usp=drive_link)**

Setelah diunduh, letakkan file model pada:
- Root project: `eye_model_22mei.keras`
- Folder deployment: `api_deployment/eye_model_22mei.keras`

---

## Struktur Folder

```text
ai_engineer/
│
├── TensorBoard Results/
│   ├── accuracy.png
│   ├── loss.png
│   ├── mae.png
│   └── lr.png
│
├── api_deployment/
│   ├── app.py
│   ├── Procfile
│   ├── requirements.txt
│   ├── runtime.txt
│   ├── drowsiness.db
│   └── eye_model_22mei.keras
│
├── logs/fit/20260522-173637
│   ├── train/
│   └── val/
│
├── url api testing/
│   ├── eye.png
│   ├── response with generative ai.png
│   └── response_*.json
│
├── notebook model.ipynb
├── eye_model_22mei.keras
└── README.md
```

---

# Petunjuk Setup Environment

## Prasyarat

Pastikan perangkat telah terinstal:
- Python 3.9 atau lebih baru
- pip (Python package manager)
- Git

## Langkah Setup

### 1. Clone Repository

```bash
git clone <url-repository>
cd ai_engineer
```

### 2. Buat Virtual Environment (Disarankan)

```bash
python -m venv venv
```

Aktifkan virtual environment:

- **Windows:**
  ```bash
  venv\Scripts\activate
  ```
- **macOS / Linux:**
  ```bash
  source venv/bin/activate
  ```

### 3. Install Dependency

Untuk menjalankan notebook training:

```bash
pip install tensorflow numpy pandas matplotlib scikit-learn jupyter
```

Untuk menjalankan REST API:

```bash
cd api_deployment
pip install -r requirements.txt
```

### 4. Unduh Model

Unduh file model dari tautan di atas, lalu letakkan pada:
- `eye_model_22mei.keras` (root project, untuk notebook)
- `api_deployment/eye_model_22mei.keras` (untuk REST API)

### 5. Konfigurasi Gemini API Key (Opsional, untuk fitur AI advice)

Buat file `.env` di dalam folder `api_deployment/`:

```bash
GEMINI_API_KEY=your_gemini_api_key_here
```

---

# Cara Menjalankan Aplikasi

## A. Menjalankan Notebook Training

### 1. Jalankan Jupyter Notebook

```bash
jupyter notebook
```

### 2. Buka Notebook

```text
notebook model.ipynb
```

Kemudian jalankan seluruh sel notebook secara berurutan.

---

## B. Menjalankan REST API Secara Lokal

### 1. Masuk ke Folder Deployment

```bash
cd api_deployment
```

### 2. Install Dependency

```bash
pip install -r requirements.txt
```

### 3. Jalankan FastAPI

```bash
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

---

## C. Mengakses API yang Sudah Dideploy

API telah dideploy menggunakan Railway dan dapat diakses langsung tanpa setup tambahan:

**Base URL:**

```
https://web-production-f21ddd.up.railway.app
```

**Swagger Documentation:**

```
https://web-production-f21ddd.up.railway.app/docs
```

---

## D. Menjalankan TensorBoard

Dari root project:

```bash
tensorboard --logdir logs
```

Buka browser:

```
http://localhost:6006
```

---

# Implementasi Main Quest

## 1. Pengembangan Model Deep Learning

Model dikembangkan menggunakan TensorFlow Keras Functional API untuk melakukan klasifikasi kondisi mata menjadi:

* Mata Terbuka (Alert)
* Mata Tertutup (Drowsy)

Model dilatih menggunakan dataset citra mata yang telah diproses dan dibagi menjadi data training, validation, dan testing.

Notebook pelatihan model tersedia pada file:

```text
notebook model.ipynb
```

---

## 2. Implementasi Komponen Kustom

Proyek ini mengimplementasikan komponen kustom berupa **Custom Callback** pada proses training model.

### Custom Logger Callback

Callback dikembangkan dengan melakukan subclass terhadap:

```python
tf.keras.callbacks.Callback
```

Tujuan callback ini adalah untuk menampilkan ringkasan metrik training pada setiap akhir epoch secara otomatis.

Metrik yang dicatat meliputi:

- Training Loss
- Training Accuracy
- Validation Loss
- Validation Accuracy

Implementasi callback:

```python
class CustomLogger(tf.keras.callbacks.Callback):
    def on_epoch_end(self, epoch, logs=None):
        logs = logs or {}
        print(
            f"Epoch {epoch+1:3d} | "
            f"Loss: {logs.get('loss', 0):.4f} | "
            f"Acc: {logs.get('accuracy', 0)*100:.2f}% | "
            f"Val Loss: {logs.get('val_loss', 0):.4f} | "
            f"Val Acc: {logs.get('val_accuracy', 0)*100:.2f}%"
        )
```

---

## 3. Penyimpanan Model

Model hasil training disimpan dalam format produksi TensorFlow:

```text
eye_model_22mei.keras
```

Format ini memungkinkan model langsung digunakan pada proses inferensi maupun deployment.

---

## 4. Implementasi Inference

Kode inferensi model sederhana diimplementasikan pada:

```text
notebook model.ipynb
```

---

# Implementasi Side Quest

## 1. REST API Mandiri Menggunakan FastAPI

Model telah diintegrasikan ke dalam REST API berbasis FastAPI sehingga dapat diakses oleh aplikasi frontend maupun backend.

### Daftar Endpoint

| Method | Endpoint | Deskripsi |
|--------|----------|-----------|
| GET | `/` | Menampilkan informasi API |
| GET | `/health` | Memeriksa status layanan API |
| POST | `/api/v1/predict` | Melakukan prediksi kondisi mata |
| POST | `/api/v1/predict-with-advice` | Melakukan prediksi dan menghasilkan rekomendasi menggunakan Gemini AI |
| GET | `/api/v1/history` | Menampilkan riwayat prediksi |
| GET | `/api/v1/stats` | Menampilkan statistik penggunaan API |

### Endpoint Utama

#### Prediksi Kondisi Mata

```http
POST /api/v1/predict
```

Input: File gambar (JPG / PNG)

#### Prediksi dengan Rekomendasi AI

```http
POST /api/v1/predict-with-advice
```

Input: File gambar (JPG / PNG)

---

## 2. Implementasi tf.GradientTape

Proyek ini mengimplementasikan **custom training loop** menggunakan TensorFlow `tf.GradientTape` untuk memberikan kontrol penuh terhadap proses training model.

Implementasi dilakukan melalui fungsi:

- `train_step()`
- `val_step()`

Pada setiap iterasi training, proses yang dilakukan meliputi:

1. Data augmentation pada batch input.
2. Forward propagation untuk menghasilkan prediksi.
3. Perhitungan loss.
4. Perhitungan gradien menggunakan `tf.GradientTape`.
5. Update parameter model menggunakan `optimizer.apply_gradients()`.

---

## 3. Integrasi Generative AI

Proyek mengintegrasikan Generative AI sebagai fitur tambahan untuk menghasilkan rekomendasi keselamatan berdasarkan hasil prediksi model.

### Contoh Output

```json
{
  "id": "ff0ea0d2-2a05-442e-bcc2-f6ce63214bea",
  "filename": "eye.png",
  "prediction": "Open",
  "confidence": 0.9997,
  "open_probability": 0.9997,
  "closed_probability": 0.0003,
  "eye_detected": true,
  "created_at": "2026-06-02T14:49:23.549867",
  "ai_advice": "Luar biasa, mata Anda tetap terbuka lebar dan fokus dengan tingkat keyakinan yang sangat tinggi. Pertahankan semangat ini untuk menyelesaikan seluruh aktivitas produktif Anda hari ini. Tetap fokus dan tunjukkan performa terbaik Anda!"
}
```

---

## 4. Integrasi TensorBoard

TensorBoard digunakan untuk memantau proses training model secara menyeluruh.

### Metrik yang Dimonitor

* Accuracy
* Loss
* Mean Absolute Error (MAE)
* Learning Rate

Visualisasi hasil training dapat dilihat pada folder:

```text
TensorBoard Results/
```

---

# Hasil Performa Model

| Metrik   | Hasil  |
| -------- | ------ |
| Accuracy | > 85%  |
| MAE      | < 0.02 |

Visualisasi lengkap tersedia pada folder **TensorBoard Results**.

---

# Pemetaan Checklist AI Engineering

| Checklist                               | Status |
| --------------------------------------- | ------ |
| Deep Learning TensorFlow Functional API | ✅      |
| Komponen Kustom (Custom Callback)       | ✅      |
| Export Model (.keras)                   | ✅      |
| Implementasi Inference Model            | ✅      |
| REST API Mandiri (FastAPI)              | ✅      |
| Custom Training Loop (tf.GradientTape)  | ✅      |
| Integrasi Generative AI                 | ✅      |
| Integrasi TensorBoard                   | ✅      |
| Akurasi Minimal 85%                     | ✅      |
| MAE Maksimal 0,02                       | ✅      |

---

# Kontributor

AI Engineering Team
- Nicke Damayanti Safitri (CACC008D6X2616)
- Rifka Alya Damayanti (CACC008D6X1433)
