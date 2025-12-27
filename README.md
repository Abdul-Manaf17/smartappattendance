# 📸 Sistem Absensi Camera - Face Recognition Attendance System

Sistem absensi siswa berbasis pengenalan wajah otomatis menggunakan ESP32-CAM dan Laravel.

## 🎯 Fitur Utama

### 1. **Face Recognition System**
   - Pendaftaran wajah siswa dengan encoding
   - Pengenalan wajah otomatis via ESP32-CAM
   - Pencatatan absensi otomatis
   - Test recognition untuk validasi

### 2. **Role-Based Access Control**
   - **Admin**: Kelola user, kelas, dan face recognition
   - **Siswa**: Dashboard, absensi manual, riwayat absensi
   - **Guru**: Dashboard, lihat absensi siswa
   - **Wali Kelas**: Dashboard, lihat absensi kelas
   - **Orang Tua**: Dashboard, monitoring absensi anak (login dengan NIS + Nama)

### 3. **Dashboard**
   - Statistik real-time
   - Grafik absensi dengan Chart.js
   - Data kehadiran harian
   - Laporan per kelas

> Catatan: Versi awal aplikasi ini terintegrasi dengan **ESP32-CAM**.  
> Versi terbaru sudah beralih ke penggunaan **webcam langsung dari browser**, sehingga modul ESP32-CAM tidak lagi dibutuhkan.

### 5. **Python Dashboard**
   - Dashboard real-time dengan Streamlit
   - Visualisasi data dengan Plotly
   - Statistik kehadiran
   - List absensi hari ini

## 🛠️ Teknologi yang Digunakan

### Backend
- **Laravel 12.37.0** - PHP Framework
- **PHP 8.2.29** - Programming Language
- **SQLite** - Database
- **Python 3** - Face Recognition Engine
- **OpenCV** - Image Processing
- **Haar Cascades** - Face Detection

### Frontend
- **Tailwind CSS** - Utility-first CSS Framework
- **JavaScript** - Client-side scripting
- **Chart.js** - Data Visualization
- **Font Awesome** - Icons
- **Vite** - Build Tool

### Hardware
- **Webcam** (kamera laptop / USB camera)

### Python Dashboard
- **Streamlit** - Web Framework
- **Pandas** - Data Processing
- **Plotly** - Interactive Charts

## 📋 Prerequisites

### Software
- PHP 8.2+
- Composer
- Node.js & npm
- Python 3.8+
- Arduino IDE
- XAMPP (optional, untuk MySQL)

### Python Packages
```
streamlit
pandas
plotly
opencv-python
numpy
face-recognition
```

### Arduino Libraries
- ESP32 Board Support
- WiFi
- HTTPClient
- ArduinoJson
- Camera (ESP32-CAM)

## 🚀 Instalasi

### 1. Clone Repository
```bash
git clone <repository-url>
cd absensi-camera
```

### 2. Install Dependencies

#### PHP Dependencies
```bash
composer install
```

#### Node.js Dependencies
```bash
npm install
```

### 3. Environment Setup
```bash
cp .env.example .env
php artisan key:generate
```

### 4. Database Setup
```bash
php artisan migrate
php artisan db:seed  # Optional
```

### 5. Storage Link
```bash
php artisan storage:link
```

### 6. Build Assets
```bash
npm run build
# atau untuk development
npm run dev
```

### 7. Run Laravel Server
```bash
php artisan serve
```

### 8. Setup Python Dashboard (Optional)
```bash
cd dashboard_python
pip install -r requirements.txt
streamlit run app.py
```

> **Catatan:**  
> Bagian dokumentasi lama terkait **setup ESP32-CAM**, file `esp32_config.h`, dan upload kode ke modul ESP32  
> sudah tidak digunakan lagi karena sistem sekarang berjalan penuh menggunakan **webcam di browser**.

## 📖 Dokumentasi

### Panduan Utama
- `README_ESP32_SETUP.md` - Setup ESP32-CAM
- `CARA_LIHAT_DATABASE.md` - Mengakses database SQLite
- `PANDUAN_LANGKAH_LANGKAH_JELAS.md` - Langkah-langkah setup lengkap

### File Panduan Lainnya
- `PANDUAN_HARDWARE_SOFTWARE_ESP32.md` - Hardware & Software requirements
- `DAFTAR_MODUL_ARDUINO.md` - Daftar modul Arduino
- `CARA_PERBAIKI_ERROR_ARDUINO.md` - Troubleshooting Arduino
- `INFO_IP_ADDRESS.md` - Informasi IP Address

## 🔐 Default Login

**Admin:**
- Email: admin@test.com
- Password: P@ssword17

**Catatan:** Password default mengikuti ketentuan keamanan (minimal 8 karakter, huruf besar, huruf kecil, angka, dan karakter khusus).

*(Direkomendasikan untuk mengubah password setelah instalasi pertama!)*

## 📂 Struktur Project

```
absensi-camera/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Admin/        # Admin controllers
│   │   │   ├── Siswa/        # Student controllers
│   │   │   ├── Guru/         # Teacher controllers
│   │   │   ├── OrangTua/     # Parent controllers
│   │   │   └── Api/          # API controllers
│   │   └── Middleware/
│   ├── Models/
│   └── Services/
│       └── FaceRecognitionService.php
├── resources/
│   ├── views/                # Blade templates
│   ├── css/
│   └── js/
├── routes/
│   ├── web.php               # Web routes
│   └── api.php               # API routes
├── scripts/
│   ├── face_recognition.py   # Face recognition script
│   └── face_encoding_simple.py
├── dashboard_python/         # Streamlit dashboard
├── database/
│   └── database.sqlite       # SQLite database
└── public/
    └── storage/              # Public storage
```

## 🎨 UI/UX

- Modern design dengan Tailwind CSS
- Responsive untuk mobile & desktop
- Facebook-style logout dropdown
- Smooth animations dan transitions
- Chart.js untuk visualisasi data

## 🔌 API Endpoints

### Face Recognition & Dashboard Endpoints
- `POST /api/face-recognition` - Submit face recognition (dari webcam / perangkat lain)
- `GET /api/dashboard/stats` - Get statistics
- `GET /api/dashboard/chart-data` - Get chart data
- `GET /api/dashboard/notifications` - Get notifications

## 🐛 Troubleshooting

### Face Recognition tidak bekerja
1. Pastikan Python scripts ada di `scripts/`
2. Install Python dependencies: `pip install opencv-python face-recognition numpy`
3. Check path Python di `.env`
4. Check logs: `storage/logs/laravel.log`

### Database tidak muncul
- Project menggunakan SQLite (file-based)
- Lihat `CARA_LIHAT_DATABASE.md` untuk cara melihat database
- File database: `database/database.sqlite`

## 📝 License

MIT License - Silakan gunakan sesuai kebutuhan Anda.

## 👥 Kontribusi

Kontribusi sangat diterima! Silakan buat pull request atau buka issue untuk diskusi.

## 📞 Support

Untuk pertanyaan atau masalah, silakan buka issue di repository ini.

---

**Dibuat dengan ❤️ untuk sistem absensi yang lebih efisien**

