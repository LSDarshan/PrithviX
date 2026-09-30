# PrithviX

> **AI-Driven Land Document Digitization and Verification System**

PrithviX is an AI-powered platform for converting Indian land records (like Pahani, RTC, title deeds, Jamabandi, and survey registers) into structured digital records. It features a **Public Citizen Portal** for instant ULPIN search & QR verification, and a secure **Admin Workspace** for document extraction, evidence review, verification, and publication.

---

## 🏛️ Two Separate Interfaces

### 1. 🌐 Public Citizen Portal
- **Home (`/`)**: Search land records by ULPIN or scan QR codes.
- **Search ULPIN (`/search-ulpin`)**: Fast database lookup for published & verified land records (No AI calls).
- **Verify QR (`/verify-qr` or `/verify/:recordId`)**: Scan QR code on a Digital Parcel Card to verify record status.
- **Help (`/help`)**: Citizen guide on ULPIN (Bhu-Aadhaar) and land record verification.

### 2. 🔐 Admin Workspace (`/admin`)
- **Dashboard (`/admin/dashboard`)**: Workspace overview & pending review queues.
- **Documents (`/admin/documents`)**: Upload scanned PDFs, PNGs, JPEGs, or WebP files.
- **Extraction & Detail (`/admin/documents/:id`)**: Fast two-stage AI extraction with evidence grounding.
- **Verification (`/admin/verification`)**: Side-by-side evidence inspection & manual field correction.
- **Land Records & Publication (`/admin/records`)**: Publish records, generate scannable QR codes, and print official verification receipts.

---

## 🚀 How to Start the Application

Run commands from the **`Replit-Design-Project`** workspace directory:

### Step 1: Open the Project Directory
```bash
cd Replit-Design-Project
```

### Step 2: Start Backend API Server (Port 5000)
```bash
npx pnpm --filter @workspace/api-server run dev
```

### Step 3: Start Frontend Web Dashboard (Port 5174)
In a **second terminal window**:
```bash
npx pnpm --filter @workspace/prithvix run dev -- --port 5174
```

---

## 💻 Browser Links

- **Public Citizen Portal**: [http://localhost:5174](http://localhost:5174)
- **Public ULPIN Search**: [http://localhost:5174/search-ulpin](http://localhost:5174/search-ulpin)
- **Admin Workspace Portal**: [http://localhost:5174/admin/dashboard](http://localhost:5174/admin/dashboard)
- **Document Review Page**: [http://localhost:5174/admin/documents/d1010000-0000-4000-8000-000000000002](http://localhost:5174/admin/documents/d1010000-0000-4000-8000-000000000002)
- **Backend API Status**: [http://localhost:5000/api/healthz](http://localhost:5000/api/healthz)

---

## ⚡ Technical Highlights

- **Fast Two-Stage Extraction**: Stage 1 fast-path Vision AI (~5–10s) + Stage 2 targeted crop retries for low confidence fields.
- **PDF & Image Processing**: Safe PDF page rendering via `pdf-img-convert` and Sharp image preprocessing.
- **Strict Field Separation**: Separate RTC #, Document #, Survey #, Hissa #, Current Holder vs Previous Holder, and Land Location vs Owner Address.
- **Multilingual Support**: English, Hindi, Kannada, Marathi, Telugu, Tamil, Malayalam, Bengali, Gujarati, Punjabi.
- **Document Hash Caching**: Hashes document bytes (`documentHash`) to load saved extractions instantly without re-running AI.

---

## 📜 License

MIT License.
