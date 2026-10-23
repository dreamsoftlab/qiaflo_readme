# 🐾 Qiaflo — AI-Powered Pet Guardian Network

> A distributed AI-powered community platform designed to protect, track, and care for pets using a Bluetooth Low Energy (BLE) sensor network, multimodal AI Guardian health assistants, real-time activity tracking (Pet Walk), live maps, and full 5-language localization.

[![Flutter](https://img.shields.io/badge/Mobile-Flutter-02569B?logo=flutter)](https://flutter.dev)
[![Fastify](https://img.shields.io/badge/Backend-Fastify-000000?logo=fastify)](https://fastify.dev)
[![Next.js](https://img.shields.io/badge/Dashboard-Next.js-000000?logo=next.js)](https://nextjs.org)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?logo=postgresql)](https://postgresql.org)
[![Redis](https://img.shields.io/badge/Queue-Redis%20%26%20BullMQ-DC382D?logo=redis)](https://redis.io)
[![Meta AI](https://img.shields.io/badge/AI-Meta%20AI-0081FB?logo=meta)](https://ai.meta.com)
[![OpenStreetMap](https://img.shields.io/badge/Maps-OpenStreetMap-7EBC6F?logo=openstreetmap)](https://www.openstreetmap.org)
[![i18n](https://img.shields.io/badge/i18n-5%20Languages%20(EN%20%7C%20ID%20%7C%20ES%20%7C%20PT%20%7C%20ZH)-blue)](#-multi-language-support-i18n)

---

## 📌 Table of Contents

- [About Qiaflo](#-about-qiaflo)
- [Core Features](#-core-features)
- [System Architecture](#-system-architecture)
- [Monorepo Structure](#-monorepo-structure)
- [Tech Stack](#-tech-stack)
- [Multi-Language Support (i18n)](#-multi-language-support-i18n)
- [Quick Start Guide (Local Setup)](#-quick-start-guide-local-setup)
- [Security & Privacy](#-security--privacy)
- [Business Model & In-App Economy](#-business-model--in-app-economy)
- [License & Copyright](#-license--copyright)

---

## 🌟 About Qiaflo

**Qiaflo** is an intelligent ecosystem combining Artificial Intelligence (AI) and a community-driven sensor network (Bluetooth Low Energy / BLE). The platform is engineered to:

1. **Prevent Pet Loss:** Utilizing power-efficient BLE signal tracking and decentralized community-assisted search radius coverage.
2. **Integrated AI Health Assistant:** Assisting pet owners with symptom checks via multimodal visual analysis (photos/videos) and interactive natural voice conversations.
3. **Engage Pet Communities:** Empowering owners through daily walk tracking (Pet Walk), gamified educational trivia quizzes, and social community feeds.

---

## 🚀 Core Features

| Feature | Description |
|---|---|
| **BLE Beacon Pairing & Battery Monitor** | Connects smart BLE tags to monitor pet signal strength and battery levels periodically. |
| **Real-Time Interactive Maps** | Displays last known coordinates and activity route history using OpenStreetMap. |
| **Proximity Radar Mode** | Visual radar powered by RSSI signal strength to guide close-range physical searches. |
| **Emergency Lost Mode** | Broadcasts immediate alerts within a localized geographic radius and mobilizes background community scanners. |
| **Sighting Reports** | Community members can submit verified lost pet sighting reports with GPS coordinates, photos, and contact info. |
| **AI Guardian (Consultation & Visual Analysis)** | Multimodal assistant powered by Meta AI for pet care Q&A and physical symptom analysis via photos/videos. |
| **AI Voice Assistant (Voice Conversation)** | Natural, low-latency, two-way interactive voice consultation session with the pet care AI assistant. |
| **Pet Walk Tracker** | Records walking routes, pedometer steps, distance, duration, bonding points, and 7-day consistency streaks. |
| **Daily Pet Quiz** | Interactive daily trivia tailored to specific pet breeds to test knowledge and earn virtual reward coins. |
| **Community Feed & Pats** | Social feed to share walking milestones, found pet announcements, and send friendly "Pat" interactions. |
| **Digital Medical Hub** | Structured digital archives for vaccination history, daily medications, allergies, vet visits, and weight charts. |

---

## 🏗 System Architecture

The Qiaflo platform is architected around a modern, modular monorepo model:

```
┌────────────────────────────────────────────────────────┐
│                 Mobile Client (Flutter)                │
│    • State Management: Riverpod                        │
│    • Networking: HTTP Client & WebSockets              │
│    • Sensors: Passive BLE Scanner, GPS & Pedometer     │
│    • UI: Dynamic Material 3 (Adaptive Dark / Light)    │
└───────────────────────────┬────────────────────────────┘
                            │ HTTPS / TLS
                            ▼
┌────────────────────────────────────────────────────────┐
│               Backend Gateway (Fastify)                │
│    • Authentication: Secure JWT & Google OAuth Verify  │
│    • Data Validation: Runtime Zod Schema Validation    │
│    • Background Queue: Redis & BullMQ Worker Pipeline  │
│    • Multi-Agent AI Engine: Meta AI                    │
└─────────────┬────────────────────────────┬─────────────┘
              │                            │
              ▼                            ▼
┌───────────────────────────┐ ┌──────────────────────────┐
│     Database & Cache      │ │  Admin Web & Simulator   │
│  • PostgreSQL (Prisma ORM)│ │      (Next.js App)       │
│  • Redis (Queue & Cache)  │ │  • Platform Monitoring   │
│  • S3 Object Storage      │ │  • Live Map Simulator    │
└───────────────────────────┘ └──────────────────────────┘
```

---

## 📂 Monorepo Structure

```text
qiaflo/
├── mobile/             # Cross-platform mobile app (Flutter / Dart)
│   ├── lib/
│   │   ├── core/       # Theme, networking, centralized configuration
│   │   ├── features/   # Feature modules (auth, pet, tracking, ai, walk, quiz)
│   │   └── l10n/       # Multi-language localization dictionaries (ARB)
│   └── pubspec.yaml    # Mobile dependencies and asset specifications
│
├── backend/            # REST API & WebSocket server (Fastify / TypeScript)
│   ├── src/
│   │   ├── controllers/# Request handlers and routing logic
│   │   ├── routes/     # API endpoint declarations
│   │   ├── services/   # Business logic (AI, email, notification, storage)
│   │   └── server.ts   # Server application entry point
│   ├── prisma/         # Database schema & migrations
│   └── locales/        # Notification localization dictionaries (JSON)
│
└── dashboard/          # Admin control panel & web simulator (Next.js / React)
    ├── src/
    │   ├── app/        # Dashboard route pages
    │   └── components/ # Web interface components
    └── package.json
```

---

## 💻 Tech Stack

### 📱 Mobile Application
- **Language & Framework:** Dart `^3.12` / Flutter Stable
- **State Management:** Flutter Riverpod
- **Maps & Location:** OpenStreetMap (`flutter_map`) + Geolocator
- **Sensors & Hardware:** `flutter_reactive_ble`, `pedometer`, `camera`
- **Artificial Intelligence:** Meta AI, Gemini Live WebSockets & Google Generative AI
- **UI Design System:** Material 3 Adaptive (Full support for Dark and Light themes)

### ⚙️ Backend API
- **Runtime:** Node.js v20+ / TypeScript ESM
- **Web Framework:** Fastify (High performance, low overhead)
- **Database & ORM:** PostgreSQL + Prisma ORM
- **Asynchronous Task Queue:** BullMQ + Redis
- **Schema Validation:** Zod Runtime Validator
- **API Documentation:** OpenAPI / Swagger UI

### 🖥️ Web Dashboard
- **Framework:** Next.js 16 (App Router) + React 19
- **Styling:** TailwindCSS
- **Map Visualizations:** Leaflet & React Leaflet
- **Icons:** Lucide Icons

---

## 🌐 Multi-Language Support (i18n)

Qiaflo features comprehensive 1:1 synchronized localization across both mobile client interfaces and server notification engines:

| Code | Language | Target Region |
|:---:|---|---|
| `en` | English | Global (Default) |
| `id` | Indonesian (Bahasa Indonesia) | Indonesia |
| `es` | Spanish (Español) | Spain & Latin America |
| `pt` | Portuguese (Português) | Brazil & Portugal |
| `zh` | Chinese (中文 简体) | Greater China & Asia Pacific |

---

## 🛠 Quick Start Guide (Local Setup)

### Prerequisites:
- [Flutter SDK](https://flutter.dev) (Latest Stable channel)
- [Node.js](https://nodejs.org) (v20 LTS or newer)
- [Docker](https://www.docker.com/) (Optional, for running local PostgreSQL & Redis)

### 1. Clone the Repository
```bash
git clone https://github.com/dreamsoftlab/qiaflo.git
cd qiaflo
```

### 2. Run Backend (Fastify)
```bash
cd backend
cp .env.example .env
# Configure your local database and credentials in .env

npm install
npx prisma generate
npx prisma db push
npm run dev
```
*API runs at: `http://localhost:3000` (Swagger Documentation: `http://localhost:3000/docs`)*

### 3. Run Web Dashboard (Next.js)
```bash
cd ../dashboard
npm install
npm run dev
```
*Dashboard runs at: `http://localhost:3001`*

### 4. Run Mobile App (Flutter)
```bash
cd ../mobile
flutter pub get
flutter run
```

---

## 🔒 Security & Privacy

- **User Location Protection:** The community BLE search network is fully anonymized. Passive scanning coordinates only update the estimated location of lost pets without revealing scanner identity or movement history.
- **Encrypted Transmission:** All communications between client applications, backend servers, and cloud services are encrypted via HTTPS and WSS (TLS 1.3).
- **Credential Isolation:** All third-party secrets, keys, and credentials reside exclusively within secure server environments and are never bundled into distributed mobile binaries.

---

## 💎 Business Model & In-App Economy

- **Free Community Tier:** Essential pet safety profiles, community BLE searching, and basic features are permanently free for all users.
- **Premium Subscription:** Extended pet capacity, prioritized emergency broadcast alerts, and monthly AI Guardian consultation benefits.
- **Virtual Q-Coins:** An in-app virtual token economy earned via walking consistency, educational quiz completion, or official store purchases.

---

## 📄 License & Copyright

Copyright © 2026 **DreamsoftLab**. All rights reserved.  
The Qiaflo platform and its intellectual property are developed and maintained by the DreamsoftLab engineering team.
