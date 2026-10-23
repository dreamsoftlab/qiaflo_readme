# 🐾 Qiaflo — AI-Powered Pet Guardian Network

> Platform komunitas terdistribusi berbasis AI untuk melindungi, melacak, dan merawat hewan peliharaan menggunakan jaringan sensor Bluetooth Low Energy (BLE), asisten kesehatan AI Guardian multimodal, pelacak jalan-jalan (Pet Walk), peta real-time, serta dukungan 5 bahasa.

[![Flutter](https://img.shields.io/badge/Mobile-Flutter-02569B?logo=flutter)](https://flutter.dev)
[![Fastify](https://img.shields.io/badge/Backend-Fastify-000000?logo=fastify)](https://fastify.dev)
[![Next.js](https://img.shields.io/badge/Dashboard-Next.js-000000?logo=next.js)](https://nextjs.org)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?logo=postgresql)](https://postgresql.org)
[![Redis](https://img.shields.io/badge/Queue-Redis%20%26%20BullMQ-DC382D?logo=redis)](https://redis.io)
[![Meta AI](https://img.shields.io/badge/AI-Meta%20AI-0081FB?logo=meta)](https://ai.meta.com)
[![OpenStreetMap](https://img.shields.io/badge/Maps-OpenStreetMap-7EBC6F?logo=openstreetmap)](https://www.openstreetmap.org)
[![i18n](https://img.shields.io/badge/i18n-5%20Bahasa%20(ID%20%7C%20EN%20%7C%20ES%20%7C%20PT%20%7C%20ZH)-blue)](#-dukungan-multi-bahasa-i18n)

---

## 📌 Daftar Isi

- [Tentang Qiaflo](#-tentang-qiaflo)
- [Fitur Utama](#-fitur-utama)
- [Arsitektur Sistem](#-arsitektur-sistem)
- [Struktur Monorepo](#-struktur-monorepo)
- [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
- [Dukungan Multi-Bahasa (i18n)](#-dukungan-multi-bahasa-i18n)
- [Panduan Memulai Cepat (Local Setup)](#-panduan-memulai-cepat-local-setup)
- [Keamanan & Privasi](#-keamanan--privasi)
- [Model Bisnis & Ekonomi In-App](#-model-bisnis--ekonomi-in-app)
- [Lisensi & Hak Cipta](#-lisensi--hak-cipta)

---

## 🌟 Tentang Qiaflo

**Qiaflo** adalah ekosistem pintar yang menggabungkan kecerdasan buatan (AI) dan jaringan sensor komunitas (Bluetooth Low Energy / BLE). Platform ini dirancang untuk:

1. **Mencegah Kehilangan Hewan:** Menggunakan pelacakan sinyal BLE hemat daya dan jangkauan pencarian gotong-royong antar-pengguna aplikasi di sekitar.
2. **Asisten Kesehatan AI Terpadu:** Membantu pemilik hewan berkonsultasi mengenai gejala fisik melalui analisis visual (foto/video) dan percakapan suara interaktif.
3. **Membangun Komunitas Pecinta Hewan:** Melalui pelacak jalan-jalan (Pet Walk), gamifikasi kuis harian edukatif, serta ruang berbagi momen (Community Feed).

---

## 🚀 Fitur Utama

| Fitur | Deskripsi |
|---|---|
| **BLE Beacon Pairing & Battery Monitor** | Menghubungkan tag BLE cerdas untuk memantau status sinyal dan daya baterai hewan peliharaan secara berkala. |
| **Peta Interaktif Real-Time** | Menampilkan titik lokasi terakhir dan jejak rute aktivitas hewan peliharaan menggunakan OpenStreetMap. |
| **Radar Mode Jarak Dekat** | Visual radar berbasis kekuatan sinyal RSSI untuk membantu melacak keberadaan hewan di area terdekat. |
| **Mode Darurat (Lost Mode)** | Mengirimkan sinyal darurat dalam radius tertentu dan mengerahkan pemindai pasif komunitas sekitar. |
| **Laporan Penampakan (Sighting Reports)** | Pengguna komunitas dapat mengirim laporan penampakan hewan hilang disertai foto, koordinat GPS, dan info kontak. |
| **AI Guardian (Konsultasi & Analisis Visual)** | Asisten multimodal bertenaga AI Meta untuk tanya jawab kesehatan serta pemeriksaan gejala fisik via foto/video. |
| **AI Voice Assistant (Percakapan Suara)** | Sesi konsultasi dua arah berbasis suara secara alami dan langsung dengan AI asisten pet care. |
| **Pet Walk Tracker** | Mencatat rute jalan-jalan, hitungan langkah pedometer, jarak, durasi, poin bonding, dan rekor konsistensi mingguan. |
| **Daily Pet Quiz** | Kuis edukasi harian interaktif seputar ras hewan peliharaan untuk mengasah wawasan dan mengumpulkan reward koin. |
| **Community Feed & Pats** | Feed sosial untuk berbagi pencapaian jalan-jalan, penemuan hewan, serta saling mengirimkan interaksi "Pat" (elusan). |
| **Rekam Medis Digital (Medical Hub)** | Arsip terstruktur riwayat vaksinasi, pengobatan harian, riwayat alergi, klinik dokter, dan grafik berat badan. |

---

## 🏗 Arsitektur Sistem

Platform Qiaflo dibangun menggunakan arsitektur monorepo modular berstandar modern:

```
┌────────────────────────────────────────────────────────┐
│                 Aplikasi Mobile (Flutter)              │
│    • State Management: Riverpod                        │
│    • Jaringan: HTTP Client & WebSockets                │
│    • Sensor: BLE Scanner pasif, GPS & Pedometer        │
│    • Antarmuka: Material 3 Adaptif (Dark / Light)      │
└───────────────────────────┬────────────────────────────┘
                            │ HTTPS / TLS
                            ▼
┌────────────────────────────────────────────────────────┐
│             Gerbang API Backend (Fastify)              │
│    • Autentikasi: JWT Aman & Google OAuth Verification │
│    • Validasi Data: Zod Schema Validation              │
│    • Antrean Latar Belakang: Redis & BullMQ            │
│    • Multi-Agent AI Engine: Meta AI                    │
└─────────────┬────────────────────────────┬─────────────┘
              │                            │
              ▼                            ▼
┌───────────────────────────┐ ┌──────────────────────────┐
│      Database & Cache     │ │   Dashboard Web & Admin  │
│  • PostgreSQL (Prisma ORM)│ │      (Next.js App)       │
│  • Redis (Antrean & Cache)│ │  • Monitoring Platform   │
│  • Penyimpanan Objek S3   │ │  • Web Simulator Peta    │
└───────────────────────────┘ └──────────────────────────┘
```

---

## 📂 Struktur Monorepo

```text
qiaflo/
├── mobile/             # Aplikasi mobile multiplatform (Flutter / Dart)
│   ├── lib/
│   │   ├── core/       # Tema, jaringan, konfigurasi terpusat
│   │   ├── features/   # Modul fitur (auth, pet, tracking, ai, walk, quiz)
│   │   └── l10n/       # Kamus lokalisasi multi-bahasa (ARB)
│   └── pubspec.yaml    # Dependensi aplikasi mobile
│
├── backend/            # REST API & WebSocket server (Fastify / TypeScript)
│   ├── src/
│   │   ├── controllers/# Logika pengendali request
│   │   ├── routes/     # Definisi endpoint API
│   │   ├── services/   # Layanan bisnis (AI, email, notifikasi, storage)
│   │   └── server.ts   # Entry point server
│   ├── prisma/         # Skema database & migrasi data
│   └── locales/        # Kamus lokalisasi server notifikasi (JSON)
│
└── dashboard/          # Panel kontrol admin & web simulator (Next.js / React)
    ├── src/
    │   ├── app/        # Halaman rute dashboard
    │   └── components/ # Komponen UI antarmuka web
    └── package.json
```

---

## 💻 Teknologi yang Digunakan

### 📱 Aplikasi Mobile
- **Bahasa & Framework:** Dart `^3.12` / Flutter Stable
- **State Management:** Flutter Riverpod
- **Peta & Lokasi:** OpenStreetMap (`flutter_map`) + Geolocator
- **Sensor:** `flutter_reactive_ble`, `pedometer`, `camera`
- **Kecerdasan Buatan:** Meta AI, Gemini Live WebSockets & Google Generative AI
- **Gaya Antarmuka:** Material 3 Dinamis (Dukungan penuh Mode Gelap dan Terang)

### ⚙️ Backend API
- **Runtime:** Node.js v20+ / TypeScript ESM
- **Framework Web:** Fastify (kinerja tinggi, latensi rendah)
- **Database & ORM:** PostgreSQL + Prisma ORM
- **Antrean Tugas Asinkron:** BullMQ + Redis
- **Validasi Skema:** Zod Validator
- **Dokumentasi API:** OpenAPI / Swagger UI

### 🖥️ Dashboard Web
- **Framework:** Next.js 16 (App Router) + React 19
- **Styling:** TailwindCSS
- **Visualisasi Peta:** Leaflet & React Leaflet
- **Ikonografi:** Lucide Icons

---

## 🌐 Dukungan Multi-Bahasa (i18n)

Qiaflo menyediakan lokalisasi penuh yang disinkronkan secara konsisten pada antarmuka aplikasi dan notifikasi sistem:

| Kode | Bahasa | Wilayah Target |
|:---:|---|---|
| `id` | Bahasa Indonesia | Indonesia |
| `en` | English | Global (Default) |
| `es` | Español | Spanyol & Amerika Latin |
| `pt` | Português | Brasil & Portugal |
| `zh` | 中文 (简体) | Tiongkok & Asia Pasifik |

---

## 🛠 Panduan Memulai Cepat (Local Setup)

### Prasyarat:
- [Flutter SDK](https://flutter.dev) versi stabil terbaru
- [Node.js](https://nodejs.org) versi 20 LTS atau lebih baru
- [Docker](https://www.docker.com/) (opsional untuk menjalankan database lokal)

### 1. Kloning Repositori
```bash
git clone https://github.com/dreamsoftlab/qiaflo.git
cd qiaflo
```

### 2. Menjalankan Backend (Fastify)
```bash
cd backend
cp .env.example .env
# Sesuaikan parameter konfigurasi database Anda di .env

npm install
npx prisma generate
npx prisma db push
npm run dev
```
*API berjalan pada: `http://localhost:3000` (Dokumentasi Swagger: `http://localhost:3000/docs`)*

### 3. Menjalankan Dashboard Web (Next.js)
```bash
cd ../dashboard
npm install
npm run dev
```
*Dashboard berjalan pada: `http://localhost:3001`*

### 4. Menjalankan Aplikasi Mobile (Flutter)
```bash
cd ../mobile
flutter pub get
flutter run
```

---

## 🔒 Keamanan & Privasi

- **Perlindungan Lokasi Pengguna:** Sistem pelacakan gotong-royong BLE bersifat anonim. Koordinat pemindai pasif hanya digunakan untuk memperbarui posisi perkiraan hewan hilang tanpa mengekspos identitas pemilik perangkat pemindai.
- **Enkripsi Komunikasi:** Seluruh transfer data antara aplikasi mobile, backend, dan layanan cloud terenkripsi menggunakan protokol HTTPS / WSS (TLS 1.3).
- **Keamanan Kredensial:** Seluruh token rahasia pihak ketiga diisolasi di lingkungan server backend dan tidak ditanamkan langsung di dalam kode biner aplikasi mobile.

---

## 💎 Model Bisnis & Ekonomi In-App

- **Akses Komunitas Gratis:** Fitur perlindungan dasar hewan, pembuatan profil, dan pencarian komunitas tersedia bagi seluruh pengguna.
- **Layanan Premium:** Akses jumlah profil hewan tambahan, prioritas siaran notifikasi darurat, dan fasilitas konsultasi AI Guardian.
- **Virtual Q-Coins:** Ekosistem koin dalam aplikasi yang dapat diperoleh melalui keaktifan jalan-jalan, penyelesaian kuis edukasi, atau opsi pembelian resmi.

---

## 📄 Lisensi & Hak Cipta

Seluruh hak cipta dilindungi undang-undang © 2026 **DreamsoftLab**.  
Proyek dan merek dagang Qiaflo dikelola oleh tim pengembang DreamsoftLab.
