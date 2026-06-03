## KEMUDI – Sistem Pemantauan Kantuk Pengemudi - Full-Stack Daveloper

## Deskripsi Project
KEMUDI (Sistem Pemantauan Kantuk Pengemudi) adalah aplikasi berbasis Artificial Intelligence yang dirancang untuk mendeteksi tingkat kewaspadaan pengemudi secara real-time menggunakan webcam.
Sistem memanfaatkan teknologi Computer Vision dan Deep Learning untuk menganalisis kondisi mata pengemudi. Ketika terdeteksi indikasi kantuk, sistem dapat memberikan informasi kepada pengguna serta menyimpan histori deteksi untuk keperluan monitoring dan analisis.
Project ini dikembangkan sebagai Capstone Project dengan fokus pada:
- Keselamatan berkendara
- Monitoring kondisi pengemudi secara real-time
- Pencatatan histori deteksi kantuk
- Analisis aktivitas perjalanan
- Dashboard monitoring berbasis web

## Features
# Authentication
- User Registration
- User Login
- JWT Authentication
- Logout System

# AI Drowsiness Detection
- Real-time webcam monitoring
- Eye detection using MediaPipe Face Mesh
- Eye state classification using TensorFlow/Keras
- Drowsiness prediction
- Confidence score calculation

# Driver Monitoring
- Start Trip
- End Trip
- Trip duration tracking
- Driver activity summary

# Dashboard
- Detection history
- Daily monitoring statistics
- Chart visualization
- Activity summary
- Profile management

# User Profile
- Upload profile picture
- View profile information
- User activity tracking

# System Architecture
- Frontend React + Vite (REST API)
- FastAPI Backend Service (PostgreSQL, TensorFlow AI, Database, Drowsiness)
- MediaPipe FaceMesh
- Eye Detection
- Prediction Result
- Dashboard

# Tech Stack
# Frontend
React
Vite
React Router DOM
Axios
JavaScript
CSS

# Backend
FastAPI
Uvicorn
SQLAlchemy
Python-Jose (JWT)
Passlib
Bcrypt
Database
PostgreSQL

# AI 
TensorFlow
Keras
OpenCV
MediaPipe
NumPy
Pillow

# Deployment
Docker
Docker Compose
VPS Deployment

# 📂 Project Structure
KEMUDI │ ├── backend/ │ ├── ai.py │ ├── database.py │ ├── jwt.py │ ├── main.py │ ├── models.py │ ├── schemas.py │ ├── requirements.txt │ ├── Dockerfile │ └── .env.example │ ├── frontend/ │ └── drowsiness-app/ │ ├── src/ │ │ ├── components/ │ │ ├── pages/ │ │ ├── assets/ │ │ └── utils/ │ │ │ ├── public/ │ ├── package.json │ └── Dockerfile │ ├── dataset/ │ ├── docs/ │ └── docker-compose.yml

# ⚙️ Installation
Clone Repository
git clone https://github.com/yourusername/kemudi.git

cd kemudi
Backend Setup
cd backend

python -m venv venv
source venv/bin/activate

Windows:
venv\Scripts\activate

Install dependencies:
pip install -r requirements.txt

Frontend Setup
cd frontend/drowsiness-app
npm install

Database Setup
Pastikan PostgreSQL sudah terinstall.

Buat database:
CREATE DATABASE kemudi_db;
Environment Variables
Buat file .env
MODEL=models/drowsiness_model.keras
SECRET_KEY=your_secret_key
ALGORITHM=HS256
DATABASE_URL=postgresql://username:password@localhost:5432/kemudi_db
TF_CPP_MIN_LOG_LEVEL=3
FRONTEND_URL=http://localhost:5173
BACKEND_URL=http://localhost:8000

# Running Application
Run Backend
cd backend
uvicorn main:app --reload

Backend URL:
http://localhost:8000

Swagger Documentation:
http://localhost:8000/docs

Run Frontend
cd frontend/drowsiness-app
npm run dev

Frontend URL:
http://localhost:5173

Run AI Service
AI Service berjalan langsung di dalam FastAPI melalui:
ai.py
Model TensorFlow akan dimuat saat backend startup.

# AI Model
Model Overview

Framework:
TensorFlow
Keras

Input:
Grayscale Image
96 x 96 pixels

Output:
AWAKE
DROWSY

## Detection Pipeline
1. Webcam Capture
Frontend mengambil frame dari webcam.

2. API Request
Frame dikirim ke endpoint:
POST /predict


3. Face Detection
MediaPipe Face Mesh mendeteksi wajah.


4. Eye Landmark Extraction
Landmark mata kiri dan kanan diambil.

5. Eye Cropping
Area mata dipotong menggunakan bounding box.

6. Preprocessing
Convert to Grayscale
Resize to 96x96
Normalize (0-1)

8. TensorFlow Prediction
Model menghasilkan confidence score.

8. Result
{
  "status": "AWAKE",
  "confidence": 98.23
}

# API Documentation
Method	Endpoint	Description
GET	/	API Health Check
POST	/register	Register User
POST	/login	Login User
POST	/logout	Logout User
POST	/start-trip	Start Driving Session
POST	/end-trip/{trip_id}	End Driving Session
POST	/upload-profile	Upload Profile Photo
GET	/profile	Get User Profile
GET	/profile/activity-summary	Get User Activity Summary
POST	/predict	AI Drowsiness Detection
PUT	/update-summary	Update Daily Summary
GET	/chart-data/{user_id}	Dashboard Chart Data
GET	/dashboard-history	Detection History

# 📊 Dashboard Features

Dashboard menyediakan:
Real-Time Monitoring
Status Pengemudi
Confidence Score
Detection Result
Analytics
Daily Summary
Total Drowsy Events
Driving Duration
Activity Statistics
Visualization
Detection Chart
Historical Data
Monitoring Report
User Management
Profile Information
Profile Picture
Authentication Status

# Deployment
Docker Deployment

Build:
docker-compose build

Run:
docker-compose up -d
VPS Deployment Flow
GitHub Repository
        │
        ▼
     VPS Server
        │
        ▼
 Docker Compose
        │
        ├── Frontend Container
        ├── Backend Container
        └── PostgreSQL Container

Deployment Process:
Pull latest source code
Build Docker images
Start containers
Configure Nginx Reverse Proxy
Configure Domain & SSL
