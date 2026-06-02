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

Callback ini membantu proses monitoring performa model selama training tanpa perlu melihat log TensorBoard secara langsung.

---

## 3. Penyimpanan Model

Model hasil training disimpan dalam format produksi TensorFlow:

```text
eye_model_22mei.keras
```

Format ini memungkinkan model langsung digunakan pada proses inferensi maupun deployment.

---

## 4. Implementasi Inference

Kode inferensi model diimplementasikan pada:

```text
api_deployment/app.py
```

Tahapan inferensi:

1. Menerima gambar mata dari pengguna
2. Melakukan preprocessing gambar
3. Menjalankan prediksi menggunakan model
4. Menghasilkan probabilitas prediksi
5. Menghasilkan rekomendasi berbasis Generative AI

---

# Implementasi Side Quest

## 1. REST API Mandiri Menggunakan FastAPI

Model telah diintegrasikan ke dalam REST API berbasis FastAPI sehingga dapat diakses oleh aplikasi frontend maupun backend.

### Endpoint Utama

#### Cek Status API

```http
GET /
```

#### Prediksi Kantuk

```http
POST /api/v1/predict-with-advice
```

### Input

* File gambar JPG
* File gambar PNG

### Contoh Output

```json
{
  "prediction": "drowsy",
  "confidence": 0.98,
  "advice": "Disarankan untuk beristirahat sebelum melanjutkan perjalanan."
}
```

### Deployment API

API telah dideploy menggunakan Railway dan dapat diakses melalui:

```text
https://web-production-f21ddd.up.railway.app
```

### Dokumentasi API

Swagger UI:

```text
https://web-production-f21ddd.up.railway.app/docs
```

---

## 2. Implementasi tf.GradientTape

Training model dilakukan menggunakan custom training loop berbasis:

```python
tf.GradientTape
```

Implementasi ini memberikan kontrol penuh terhadap:

* Forward propagation
* Perhitungan loss
* Backpropagation
* Update parameter model

---

## 3. Integrasi Generative AI

Proyek mengintegrasikan Generative AI sebagai fitur tambahan untuk menghasilkan rekomendasi keselamatan berdasarkan hasil prediksi model.

### Contoh Output

```json
{
  "prediction": "drowsy",
  "advice": "Anda terindikasi mengantuk. Disarankan untuk berhenti sejenak dan beristirahat sebelum melanjutkan perjalanan."
}
```

Bukti implementasi dapat dilihat pada folder:

```text
url api testing/
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

Sedangkan log TensorBoard disimpan pada folder:

```text
logs/
```

---

# Hasil Performa Model

Model memenuhi seluruh kriteria minimum yang ditetapkan.

| Metrik   | Hasil  |
| -------- | ------ |
| Accuracy | > 85%  |
| MAE      | < 0.02 |

Visualisasi lengkap tersedia pada folder **TensorBoard Results**.

---

# Cara Menjalankan Notebook Training

## 1. Install Dependency

```bash
pip install tensorflow
pip install numpy
pip install pandas
pip install matplotlib
pip install scikit-learn
pip install tensorboard
```

## 2. Jalankan Jupyter Notebook

```bash
jupyter notebook
```

## 3. Buka Notebook

```text
notebook model.ipynb
```

Kemudian jalankan seluruh sel notebook secara berurutan.

---

# Cara Menjalankan TensorBoard

Dari root project:

```bash
tensorboard --logdir logs
```

Buka browser:

```text
http://localhost:6006
```

---

# Cara Menjalankan REST API Secara Lokal

## 1. Masuk ke Folder Deployment

```bash
cd api_deployment
```

## 2. Install Dependency

```bash
pip install -r requirements.txt
```

## 3. Jalankan FastAPI

```bash
uvicorn app:app --reload
```

API akan berjalan pada:

```text
http://127.0.0.1:8000
```

Swagger Documentation:

```text
http://127.0.0.1:8000/docs
```

---

### RestAPI Deployment

API berhasil dideploy menggunakan Railway dan dapat diakses secara publik melalui:

- Base URL: https://web-production-f21ddd.up.railway.app
- Swagger Documentation: https://web-production-f21ddd.up.railway.app/docs

Contoh hasil pengujian endpoint tersedia pada folder:

```text
url api testing/
```

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
Nicke Damayanti Safitri (CACC008D6X2616)
Rifka Alya Damayanti (CACC008D6X1433)
