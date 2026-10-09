# Colligram: College Social Network & Student Marketplace

> A production-oriented web application connecting university students through campus social feeds, mutual-connection discovery matching, senior-junior mentorship, direct messaging, and a student resale marketplace.

---

## 🌟 Core Features

1. **Campus Feed (Instagram-Style)**:
   - High-trust, university-domain-gated social feed.
   - Multi-image photo posts with optimistic likes, nested threaded comments, and channel tags (`Campus Life`, `Academics`, `Events`, `Clubs`, `Lost & Found`).
2. **Student Discovery (Tinder-Style)**:
   - Dynamic card stack with touch & drag physics (Pass `✕`, Super-Connect `⭐`, Connect `🤝`).
   - Mutual connection algorithm computing shared friends (`🤝 3 mutual connections: Sarah, David`).
   - Celebratory match overlay with instant direct chat handoff.
3. **Senior-Junior Mentorship**:
   - Directory of juniors, seniors, and alumni available for student guidance.
   - Filter by degree/major with "Topics I can help with" pills.
   - Formal mentorship request dialog with intro notes.
4. **Campus Marketplace**:
   - Zero-fee, hyper-local classifieds for textbooks, tech, dorm furniture, and lab gear.
   - Filter by condition, category, price, and safe campus pickup locations.
   - Direct "Chat with Seller" handshake.
5. **Direct Student Messaging**:
   - Split-screen real-time conversation stream with unread counters.
   - Permissions guardrail preventing unsolicited spam (requires mutual match, accepted connection, or active marketplace inquiry).
6. **Safety & Moderation**:
   - Confidential reporting workflow with automated quarantine (content receiving ≥ 3 reports is auto-hidden).
   - User blocking that immediately removes posts, listings, and messages from both parties.

---

## 🛠️ Technology Stack

- **Frontend**: React 18, Vite, Tailwind CSS, Lucide React, Framer Motion, Axios.
- **Backend**: Python 3.14 / Django 5.1, Django REST Framework, SimpleJWT.
- **Database**: Neon Serverless PostgreSQL (with local SQLite auto-fallback for offline dev).
- **Media CDN**: Cloudinary direct-to-CDN signed upload architecture (with local fallback).
- **Hosting / DevOps**: Render (`render.yaml` infrastructure-as-code), GitHub Actions.

---

## 🚀 Quickstart Guide

### 1. Backend Setup (Django + DRF)

```bash
cd backend

# 1. Activate virtual environment (Windows PowerShell)
.\venv\Scripts\Activate.ps1

# 2. Run database migrations (creates all Neon / SQLite tables)
python manage.py migrate

# 3. Seed demo universities, student accounts, posts and marketplace items
python manage.py seed_collegedata

# 4. Start the Django API server (runs on http://127.0.0.1:8000)
python manage.py runserver 8000
```

### 2. Frontend Setup (React + Vite)

```bash
cd frontend

# Start the Vite development server
npm run dev
```

Visit **`http://localhost:5173`** in your browser!

---

## 🔑 Pre-Seeded Demo Student Accounts

The database comes pre-seeded with universities (Stanford, MIT, Harvard, UC Berkeley, and Colligram Demo Campus) and active student profiles:

| Account | Email | Password | Role / Major |
|---|---|---|---|
| **Alex Chen** | `alex@college.edu` | `ColligramDemo2026!` | Senior CS Major • Mentor |
| **Maya Patel** | `maya@college.edu` | `ColligramDemo2026!` | Junior Pre-Med • Mentor |
| **Jordan Lee** | `jordan@college.edu` | `ColligramDemo2026!` | Sophomore Economics |
| **Sarah Williams** | `sarah@college.edu` | `ColligramDemo2026!` | Senior Design Lead • Mentor |
| **Lucas Rossi** | `lucas@college.edu` | `ColligramDemo2026!` | Freshman MechE |

---

## 🧪 Automated Testing

Run the backend automated test suite:

```bash
cd backend
.\venv\Scripts\pytest.exe tests/test_colligram_core.py
```

Tests verify:
- ✅ Strict campus email domain validation (e.g. rejecting generic emails when `.edu` is expected)
- ✅ JWT access/refresh token generation
- ✅ Campus boundary isolation (students only see posts and listings from their university)
- ✅ Mutual connection set-intersection computation
- ✅ Tinder-style reciprocal swipe matching and automatic chat thread generation

---

## ☁️ Production Deployment on Render

This project contains a turnkey `render.yaml` deployment blueprint:

1. Push this repository to **GitHub**.
2. Connect your repository to **Render** via **Blueprints**.
3. Supply your **Neon PostgreSQL** `DATABASE_URL` and **Cloudinary** credentials in Render's environment dashboard.
4. Render will automatically build the Django Web Service and the Vite React Static Site with zero extra configuration!
