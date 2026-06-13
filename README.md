<div align="center">

<img src="https://img.shields.io/badge/HeartSync-Medical%20Telemetry-red?style=for-the-badge&logo=heart&logoColor=white" alt="HeartSync"/>

# HeartSync

**AI-Powered Cardiac Telemetry & Real-Time ECG Monitoring Platform**

*A production-ready, full-stack medical dashboard built for clinicians and patients — combining live biometric streaming, Gemini AI cardiac analysis, and automated emergency escalation.*

<br/>

[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-6-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Express](https://img.shields.io/badge/Express-Backend-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com/)
[![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%26%20Auth-FFCA28?style=flat-square&logo=firebase&logoColor=black)](https://firebase.google.com/)
[![Gemini](https://img.shields.io/badge/Gemini-AI%20Analysis-4285F4?style=flat-square&logo=google&logoColor=white)](https://aistudio.google.com/)
[![Twilio](https://img.shields.io/badge/Twilio-Emergency%20Dispatch-F22F46?style=flat-square&logo=twilio&logoColor=white)](https://twilio.com/)
[![Tailwind](https://img.shields.io/badge/Tailwind-v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-MIT-22C55E?style=flat-square)](LICENSE)

<br/>

[Features](#-features) · [Tech Stack](#-tech-stack) · [Getting Started](#-getting-started) · [Environment Variables](#-environment-variables) · [Deployment](#-deployment) · [Roadmap](#-roadmap)

</div>

---

## Overview

HeartSync is a highly responsive, secure medical telemetry platform designed for real-world clinical environments. It streams and analyzes live cardiac biometric data — including ECG waveforms, SpO2 saturation, and continuous heart rate — and uses Google Gemini's multimodal AI with Thinking Mode to deliver intelligent, real-time clinical insights.

When vitals breach dangerous thresholds, HeartSync automatically escalates via Twilio SMS and voice calls to emergency responders. All biometric data, consultation records, and AI analysis histories are securely persisted in Cloud Firestore, with role-based access managed through Firebase Authentication.

---

## ✨ Features

- 🫀 &nbsp;**Live ECG Visualization** — Real-time electrocardiogram, SpO2, and heart rate graphs with interactive Recharts rendering
- 🧠 &nbsp;**Gemini AI Cardiac Analysis** — Server-side telemetry analysis using Gemini Thinking Mode for deep clinical reasoning
- 🔁 &nbsp;**Resilience Failover** — Automatic model downgrade from `gemini-2.5-pro-preview` to standard models under resource limits, preserving 100% uptime
- 🚨 &nbsp;**Automated Emergency Dispatch** — Twilio SMS and voice escalation triggered when vitals enter hazardous cardiac sequences
- 🔐 &nbsp;**Institutional Authentication** — Firebase Auth for medical professionals (SSO) and individual patient profiles
- 🗺️ &nbsp;**Live Ambulance Tracking** — React-Leaflet maps showing real-time ambulance positions, clinic locations, and nearby emergency services
- 📄 &nbsp;**Clinical Report Export** — On-demand jsPDF generation of medical-grade audit trails and biometric charts
- 🗃️ &nbsp;**Secure Data Persistence** — Full biometric history, AI analysis records, and consultation logs in Cloud Firestore

---

## 🏗️ Tech Stack

### Core Architecture

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | React 19 | Functional components, custom hooks, modern state management |
| Backend | Express | Secure full-stack API server with Vite middleware proxy |
| Language | TypeScript (strict) | Type-safety, contract compliance, predictable tooling |
| Client Build | Vite 6 | Lightning-fast HMR and client-side bundling |
| Server Build | esbuild + tsx | Compiles backend to `dist/server.cjs` for production |

### Persistence & Authentication

| Service | Purpose |
|---|---|
| Firebase Authentication | Institutional SSO credentials and patient identity management |
| Cloud Firestore | Real-time biometric data, health analysis histories, emergency triggers, consultation records |

### AI & Medical Intelligence

| Service | Purpose |
|---|---|
| Google Gemini API (`@google/genai`) | Intelligent server-side cardiac telemetry analysis |
| Thinking Mode | Advanced reasoning over complex clinical symptom patterns |
| Resilience Failover Route | Graceful model downgrade under API resource boundaries |

### UI, Visualization & Mapping

| Library | Purpose |
|---|---|
| Tailwind CSS v4 | Utility-first responsive layout and micro-adjustments |
| Motion (`motion/react`) | Panel animations, navigation slides, state transition curves |
| Recharts | Live ECG, SpO2, and heart rate interactive graphs |
| React-Leaflet / Leaflet | Ambulance tracking, clinic locator, emergency dispatch mapping |

### Institutional Services

| Service | Purpose |
|---|---|
| Twilio SDK (server-side) | Automated emergency SMS and voice call escalation |
| jsPDF | Clinical audit trail generation and medical-grade chart exports |

---

## 📁 Project Structure

```
heartsync/
├── client/                         # React 19 frontend
│   ├── src/
│   │   ├── components/             # ECG panels, vitals cards, maps, modals
│   │   ├── hooks/                  # Custom React hooks (useTelemetry, useAuth, etc.)
│   │   ├── pages/                  # Dashboard, Patient View, Consultation, Reports
│   │   ├── services/               # Firebase client, API calls
│   │   └── main.tsx                # App entry point
│   └── index.html
├── server/                         # Express backend
│   ├── routes/                     # /analysis, /dispatch, /export, /auth
│   ├── services/                   # Gemini, Twilio, Firebase Admin integrations
│   └── index.ts                    # Server entry point
├── dist/
│   └── server.cjs                  # Production-bundled server output
├── .env                            # Secret keys — never commit this
├── .env.example                    # Safe template for onboarding
├── .gitignore
├── vite.config.ts
├── tsconfig.json
├── tailwind.config.ts
├── package.json
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18 or higher
- **Google AI Studio** account — [get a Gemini API key](https://aistudio.google.com/app/apikey)
- **Firebase** project with Firestore and Authentication enabled — [Firebase Console](https://console.firebase.google.com)
- **Twilio** account with an active phone number — [twilio.com](https://twilio.com)

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/yourusername/heartsync.git
cd heartsync
```

**2. Install dependencies**

```bash
npm install
```

**3. Configure environment variables**

```bash
cp .env.example .env
```

Open `.env` and fill in your keys (see [Environment Variables](#-environment-variables) below).

**4. Start the development server**

```bash
npm run dev
```

The app runs at `http://localhost:5173` with the Express API proxied through Vite.

---

## 🔐 Environment Variables

Create a `.env` file in the root directory:

```env
# ── Google Gemini ──────────────────────────────
GEMINI_API_KEY=your_gemini_api_key_here

# ── Firebase ───────────────────────────────────
FIREBASE_API_KEY=your_firebase_api_key
FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_STORAGE_BUCKET=your_project.appspot.com
FIREBASE_MESSAGING_SENDER_ID=your_sender_id
FIREBASE_APP_ID=your_app_id

# ── Firebase Admin (server-side) ───────────────
FIREBASE_ADMIN_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
FIREBASE_ADMIN_CLIENT_EMAIL=firebase-adminsdk@your_project.iam.gserviceaccount.com

# ── Twilio ─────────────────────────────────────
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=+1xxxxxxxxxx
EMERGENCY_DISPATCH_NUMBER=+1xxxxxxxxxx

# ── Server ─────────────────────────────────────
PORT=3000
NODE_ENV=development
```

> ⚠️ **Never commit your `.env` file.** It is already covered by `.gitignore`.

---

## 📜 Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start Vite dev server with Express middleware |
| `npm run build` | Build client (Vite) + bundle server (esbuild → `dist/server.cjs`) |
| `npm run start` | Run the production server |
| `npm run typecheck` | TypeScript type checking across the full project |
| `npm run lint` | ESLint across client and server |

---

## ☁️ Deployment

### Render *(recommended — full-stack)*

1. Push your repo to GitHub
2. Go to [render.com](https://render.com) → **New Web Service** → connect your repo
3. Set **Build Command:** `npm run build`
4. Set **Start Command:** `node dist/server.cjs`
5. Add all environment variables under **Environment**
6. Click **Deploy**

### Vercel *(frontend) + Firebase Functions (backend)*

1. Deploy the `client/` build to [Vercel](https://vercel.com) via GitHub import
2. Migrate Express routes to Firebase Cloud Functions
3. Add environment variables in the Vercel dashboard under **Settings → Environment Variables**

---

## 🧠 How the AI Analysis Works

```
Live Biometrics (ECG / SpO2 / HR)
        ↓
  Express Backend receives telemetry stream
        ↓
  Gemini API — Thinking Mode engaged
  (deep clinical reasoning on waveform + vitals)
        ↓
  ┌─────────────────────────────────────┐
  │  Resource limit hit?                │
  │  YES → Failover to standard model   │
  │  NO  → Continue on pro-preview      │
  └─────────────────────────────────────┘
        ↓
  Analysis streams back to dashboard
        ↓
  Vitals breach threshold?
  YES → Twilio triggers emergency SMS + voice call
  NO  → Result saved to Firestore history
```

---

## 🗺️ Roadmap

- [ ] FHIR-compliant data export for EHR integration
- [ ] Wearable device support (ECG patches, Apple Watch, Fitbit)
- [ ] Multi-patient ward monitoring view
- [ ] Role-based access control (cardiologist, nurse, admin, patient)
- [ ] Offline mode with background sync on reconnect
- [ ] Mobile app (React Native)
- [ ] Multilingual support for global clinical deployment

---

## ⚕️ Medical Disclaimer

> HeartSync is an AI-assisted clinical support tool intended for informational and decision-support purposes. It is **not** a certified medical device and must **not** be used as the sole basis for medical diagnosis, treatment decisions, or emergency response. All AI-generated analysis should be reviewed and validated by a qualified healthcare professional. In any medical emergency, always contact your local emergency services immediately.

---



---

<div align="center">

Made with ❤️ by the HeartSync team · Powered by [Google Gemini](https://deepmind.google/technologies/gemini/) · [Firebase](https://firebase.google.com/) · [Twilio](https://twilio.com/)

</div>
