# Yuvashakti Skill India Pvt. Ltd. — Kaushalya LMS
## Complete Full-Stack Setup & Installation Guide

This repository contains the institutional-grade **Kaushalya Learning Management System (LMS)** developed for **Yuvashakti Foundation (YSF)**, comprising:
1. **Central Administration Control Center & Backend API** (`backend/`):
   - Express REST API with SheetJS (`xlsx`) Excel ingestion & template generator.
   - Question Bank repository with Fisher-Yates randomization.
   - Trainee registry with 12-digit Aadhaar deduplication & status upsert.
   - Helpdesk ticketing, OJT attendance tracking, and assignment grading.
   - Single-Page Admin SaaS Control Center at `http://localhost:5000/admin.html`.
2. **Mobile Learning Application** (`mobile/`):
   - Cross-platform React Native Expo application (Web, Android, iOS).
   - Bi-directional synchronization with Central LMS API.
   - OJT Attendance & Training Hours progress tracker.
   - Dynamic MCQ Test Module, Learning Resources reader (PDF/PPT/Video), Assignments submission & evaluation, and Technical Query Helpdesk.

---

## 📋 System Requirements
- **Node.js**: v18.0.0 or higher (v20+ recommended). Check with `node -v`.
- **npm**: v9.0.0 or higher. Check with `npm -v`.
- *(Optional)* **Expo Go** app on your physical iOS/Android phone (free from App Store / Google Play) if testing on a real device.

---

## 🚀 Quick Start (Step-by-Step Installation)

### Step 1: Unzip the Project
Extract the zip file to your preferred folder:
```bash
unzip YSF_LMS_Complete_Project.zip -d YSF_LMS
cd YSF_LMS
```

---

### Step 2: Install Dependencies

Run the following commands to install dependencies for both the Backend and Mobile App:

```bash
# 1. Install root dependencies
npm install

# 2. Install backend dependencies (Express, CORS, Multer, XLSX)
cd backend
npm install
cd ..

# 3. Install mobile app dependencies (React Native, Expo, Icons, AsyncStorage)
cd mobile
npm install
cd ..
```

*(Tip: You can run `cd backend && npm install && cd ../mobile && npm install && cd ..` in one line)*

---

### Step 3: Start the Backend Server & Admin Control Center

In a new terminal window, run:
```bash
cd backend
npm start
```

You should see:
```text
============================================================
 Kaushalya LMS Backend Server & Admin Control Center Live
 Server running on port: 5000
 Local URL:   http://localhost:5000
 Admin Panel: http://localhost:5000/admin.html
 API Endpoint: http://localhost:5000/api
============================================================
```

#### Accessing the Admin Panel:
Open your browser and navigate to:
👉 **`http://localhost:5000/admin.html`**

---

### Step 4: Run the Mobile Application

Open a **separate terminal window** and choose your preferred platform:

#### Option A: Run in Web Browser (⚡ Fastest & Easiest — Recommended for Testing)
```bash
cd mobile
npx expo start --web
```
*Or from the root directory:*
```bash
npm run mobile:web
```
- Opens automatically in your browser at **`http://localhost:8081`**.
- Press `F12` (or `Cmd + Option + I` on Mac) and click the **Device Toolbar / Mobile View** button in Chrome/Edge/Safari for an authentic smartphone display!

#### Option B: Run on Your Physical Phone via Expo Go
1. Install **Expo Go** from Google Play Store or Apple App Store.
2. Make sure your computer and phone are connected to the **same Wi-Fi network**.
3. In terminal:
   ```bash
   cd mobile
   npx expo start
   ```
4. Scan the QR code displayed in the terminal:
   - **Android**: Tap "Scan QR code" inside the **Expo Go** app.
   - **iOS**: Scan with your default **Camera** app, then tap the prompt to open in Expo Go.

#### Option C: Run on Android Emulator
```bash
cd mobile
npx expo start --android
```

#### Option D: Run on iOS Simulator (Mac only)
```bash
cd mobile
npx expo start --ios
```

---

## 🔑 Login & Demo Credentials

### Mobile App Login Flow:
1. **Language Screen**: Select **English** or **मराठी (Marathi)**.
2. **Institute Code Screen**:
   - **Institute Code**: `21092`
   - Tap **"Validate Institute Code"**.
3. **Login Screen**:
   - **Username / YSF Code**: `W2307C00001`
   - **Password**: `password123`
   - *(Alternatively, tap **"Continue as Guest"** for instant 1-click access!)*

### Admin Control Center:
- No login required in development mode; open `http://localhost:5000/admin.html` directly.

---

## 🧪 Key Features & Workflows to Test

1. **Question Bank Bulk Excel Ingestion**:
   - Go to Admin Panel → **Tests & Assessments** → click **Question Bank Repository** sub-tab.
   - Click **"Download Template (.xlsx)"** to get a pre-formatted Excel template.
   - Click **"Bulk Ingest Questions"** to upload question spreadsheets; check deduplication report.
2. **Smart MCQ Test Builder**:
   - Click **"+ Create New MCQ Test"**.
   - Test the 3 modes:
     - 🎲 **Smart Randomize**: Select module, count, and difficulty → click "Pick Questions Randomly" or "Re-roll".
     - ☑️ **Pick from Bank**: Search and tick questions from the bank → "Add Selected to Test".
     - ➕ **Custom Entry**: Add a manual question with an optional checkbox to also save to bank.
3. **Mass Trainee Ingestion (Aadhaar Deduplication & Upsert)**:
   - Go to Admin Panel → **User Master**.
   - Download template via **"Download Excel Template (.xlsx)"**.
   - Click **"Bulk Excel Import & Status Upsert"** to upload a trainee spreadsheet; existing Aadhaar numbers are updated, while new trainees are enrolled.
4. **Attendance & OJT Hours Management**:
   - In User Master, click the **"Attendance"** button on any trainee row.
   - Adjust Present/Absent days or Completed Hours; check the live progress bar and save.
   - Check the **Dashboard** on the mobile app to verify live bi-directional sync!
5. **Technical Queries Helpdesk**:
   - In Mobile App → tap **Technical Query (Support)** → submit a question.
   - In Admin Panel → check the **Technical Queries** tab (with live open ticket badge).
   - Click **"Reply & Resolve"** to send an official response; view the response in the mobile app!
6. **Assignment Grading & Feedback**:
   - In Admin Panel → **Assignments & Submissions** → inspect trainee submissions.
   - Click **"Grade & Review"** → assign marks and remarks.
   - In Mobile App → open **Assignments** → check the evaluated submission card!

---

## 🛠️ Project Structure Overview

```text
YSF_LMS/
├── backend/
│   ├── data/
│   │   └── db.json               # Persistent JSON database (questionBank, trainees, attendance, etc.)
│   ├── public/
│   │   └── admin.html            # Single-Page Admin SaaS Control Center
│   ├── src/
│   │   ├── server.js             # Express API server, SheetJS parsing & template generators
│   │   └── data.js               # Initial state seeds & database manager
│   ├── package.json
│   └── uploads/                  # Uploaded reference papers and student assignments
│
├── mobile/
│   ├── assets/                   # App logos, icons, splash screens
│   ├── src/
│   │   ├── components/           # Header, Footer, DrawerSidebar, DocumentViewerModal, Toast
│   │   ├── i18n/                 # English and Marathi language translations
│   │   ├── screens/              # Dashboard, Profile, LearningResources, TestModule, Assignments, etc.
│   │   ├── services/             # api.ts (REST client & sync) & ScreenTimeTracker.ts (Telemetry)
│   │   └── types/                # TypeScript interface definitions
│   ├── package.json
│   ├── tsconfig.json
│   └── .env                      # Mobile environment configurations (API URLs & Institute Code)
│
├── package.json                  # Root convenience scripts
└── README_SETUP.md               # This setup guide
```

---

## ❓ Troubleshooting

- **Port 5000 is already in use:**
  ```bash
  # On Mac/Linux:
  lsof -i :5000
  kill -9 <PID>
  # On Windows (cmd as admin):
  netstat -ano | findstr :5000
  taskkill /PID <PID> /F
  ```
- **Mobile app shows "Network request failed":**
  - Verify `backend` is running (`http://localhost:5000`).
  - If running on a physical phone via Expo Go, ensure `EXPO_PUBLIC_API_URL_LAN` in `mobile/.env` matches your computer's local IP address (e.g. `http://192.168.x.x:5000/api`).
- **TypeScript Typecheck:**
  ```bash
  cd mobile
  npx tsc --noEmit
  # Verifies 0 errors
  ```

---
*Developed for Yuvashakti Skill India Pvt. Ltd. — Kaushalya LMS Institutional Vocational Apprenticeship & Dual-System Training.*
