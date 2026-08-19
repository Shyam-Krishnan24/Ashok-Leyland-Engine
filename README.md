# Ashok Leyland "H" Series Engine History Card MES
### Sequential Multi-Operator Assembly Line Quality Tracking & Execution System (HLEF 4790F-L2A)

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Backend-Node%20HTTP%20%2F%20Express-000000?style=flat&logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB%20%2F%20Local%20JSON%20Fallback-47A248?style=flat&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Architecture](https://img.shields.io/badge/Architecture-75%20Assembly%20Stations-0b4da2?style=flat)]()
[![Compliance](https://img.shields.io/badge/Standard-BS--VI%204V%20Diesel%20Engines-002244?style=flat)]()

---

## 📌 Executive Overview

The **Ashok Leyland Engine History Card MES** is an enterprise-grade digital Manufacturing Execution System (MES) and Sequential Quality Tracking platform built specifically for the **Ashok Leyland "H" Series Auto Engines** (H6 BS-VI - 4V Engines, 250 HP rating) at the **Hosur Plant - I**.

Digitizing the physical standard operating document **HLEF 4790F-L2A**, this platform coordinates **75 sequential assembly stations** across 10 structured documentation pages, ensuring 100% traceability, mandatory torque-angle logging, Poka-Yoke failure locks, component QR serialization, and strict Quality Firewall sign-offs before engine release.

```
+---------------------------------------------------------------------------------------------------+
|                                 ASHOK LEYLAND ENGINE ASSEMBLY LINE                                |
+------------------+------------------+-------------------+--------------------+--------------------+
|  Crankcase (CB)  |  Short Block(SB) |   Long Block (LB) |  Testing & Leak    | Quality Firewall   |
|   CB01 -> CB08   |   SB01 -> SB13   |    LB01 -> LB36   |  ECOS & Hot Test   | Final Release (52) |
+------------------+------------------+-------------------+--------------------+--------------------+
```

---

## 🌟 Key Features

### 1. 🔐 Shift & Operator Station Role Enforcements
- Multi-shift operator authentication for **Day Shift** (`operatord-1` to `operatord-75`), **Afternoon Shift** (`operatora-1` to `operatora-75`), and **Night Shift** (`operatorn-1` to `operatorn-75`).
- **Sequential Poka-Yoke Locking**: Operators can only submit their assigned station; out-of-sequence submissions are prevented to ensure complete upstream verification.
- Default demo PIN: `1234`.

### 2. 📋 Digital 10-Page Master History Card (`HLEF 4790F-L2A`)
- Exact digital twin of Ashok Leyland's standard engine history document.
- Real-time station status updates (`IN_PROGRESS`, `COMPLETED_PASSED`, `COMPLETED_WITH_FAILURES`, `FIREWALL_RELEASED`).
- Validation rules enforcing mandatory remarks on any failed inspection item.

### 3. 🔍 Aggregate Component QR Serialization Grid
- Serial number and 2D QR Code tracking for critical powertrain aggregates:
  - Fuel Injection Pump (FIP)
  - Common Rail (CR) Fuel Rail & Injectors
  - Turbocharger Assembly
  - Engine Electronic Control Unit (ECU)
  - Starter Motor & Alternator
  - CCV / OCV Filter Assembly

### 4. 🛡️ Quality Gates & Compliance Audits
- **IPV-1 (In-Process Verification 1)**: Free rotation & crankshaft end play checks.
- **Q-GATE 1**: Poly-V belt routing & tension check.
- **ECOS Cold Leak Test**: Automated pressure decay validation for coolant and lubrication circuits.
- **Hot Testing Inspection**: Dynamometer run-up, abnormal noise detection, and oil/water leak checks.
- **52-Point Final Quality Inspection**: Comprehensive visual, torque, and clearance audit.
- **Quality Firewall Sign-Off**: Authorization gate before engine dispatch.

### 5. 💾 Resilient Hybrid Storage Architecture
- Connects automatically to **MongoDB** for high-volume enterprise production.
- Auto-switches to a zero-dependency **Local JSON Flat-File Storage** (`data/engines.json`) if MongoDB is unavailable, ensuring zero shop floor downtime.

---

## 🏗️ Assembly Line Station Mapping (75 Stations / 10 Pages)

| Page | Station Range | Assembly Stage Description |
| :--- | :--- | :--- |
| **Page 1** | `CB01` – `CB08`, `SB01` – `SB02` | Block preparation, PCN fitment, shell bearings, crankshaft torquing, IPV-1 end play, oil pump assembly, timing back plate, camshaft. |
| **Page 2** | `SB03` – `SB08` | Idler gear, flywheel housing torquing, PTFE oil seal, FIP sub-assembly, flywheel mounting (180–360 Nm), timing gear case, con-rod stuffing. |
| **Page 3** | `SB08A` – `SB13`, `LB01` – `LB03A` | Con-rod caps matching, nut runner torquing, piston torque-to-turn, sump sealant application, 34-bolt sump torquing, cylinder head sub-assembly. |
| **Page 4** | `LB04` – `LB10A` | Cylinder head bolt nut runner tightening, rocker lever torquing, tappet valve clearance, common rail & injectors, turbocharger, EGR cooler. |
| **Page 5** | `LB11` – `LB18` | Alternator, AC compressor, auto tensioner, Q-GATE 1 belt routing, coolant outlet pipe, wiring harness routing, damper nut torquing, fan fitment. |
| **Page 6** | `LB19` – `LB23A` | CCV filter assembly, high pressure fuel pipes 1–6, fuel return lines, intake manifold, intake throttle valve (ITV). |
| **Page 7** | `LB24` – `LB31` | Common rail pressure / boost / cam / crank sensors, ECU fitment, glow plugs, engine ground cable, HC dozer injector, fastener torque verification. |
| **Page 8** | `LB32` – `LB36` | Coolant hose clamps, ECOS system cold leak testing, engine oil filling (grade & volume), End of Line Q-GATE 4 audit, lifting decision. |
| **Page 9** | `PAGE9-QR` | Aggregate 2D QR code scanning, component serial matching, and engine traceability grid. |
| **Page 10** | `TESTING` – `FIREWALL` | Hot testing leak & noise inspection, engine dressing verification, 52-point quality check, Quality Firewall sign-off & release. |

---

## 💻 Tech Stack

- **Frontend**: HTML5, Vanilla CSS3 (Custom Ashok Leyland Industrial Design System), ES6+ JavaScript, Lucide Icons.
- **Backend API**: Node.js HTTP / Express REST API.
- **Database**: MongoDB (via Mongoose) with automated local JSON fallback (`data/engines.json`).
- **Build / Dev Tools**: Vite, TypeScript typings, PostCSS / TailwindCSS tooling.

---

## 🚀 Quick Start Guide

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18.x or higher)
- [npm](https://www.npmjs.com/) (version 9.x or higher)
- *(Optional)* [MongoDB](https://www.mongodb.com/) (Local or MongoDB Atlas)

### 1. Clone the Repository
```bash
git clone https://github.com/Shyam-Krishnan24/Ashok-Leyland-Engine.git
cd Ashok-Leyland-Engine
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Configuration (Optional)
Copy the example environment file and update if using external MongoDB:
```bash
cp .env.example .env
```
Default configuration values:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/ashok_leyland_engines
```
> **Note**: If MongoDB is not running, the application will automatically fall back to local file storage at `./data/engines.json`.

### 4. Start the Application

#### Production / Unified MES Server:
```bash
node server.js
```
The MES Portal will be live at: **`http://localhost:3000`**

#### Frontend Development Server:
```bash
npm run dev
```

---

## 🔑 Operator Authentication Details

| Shift | Username Pattern | Available Stations | Password / PIN |
| :--- | :--- | :--- | :--- |
| **Day Shift** | `operatord-1` to `operatord-75` | Station 1 (`CB01`) to Station 75 (`FIREWALL-PASS`) | `1234` |
| **Afternoon Shift** | `operatora-1` to `operatora-75` | Station 1 (`CB01`) to Station 75 (`FIREWALL-PASS`) | `1234` |
| **Night Shift** | `operatorn-1` to `operatorn-75` | Station 1 (`CB01`) to Station 75 (`FIREWALL-PASS`) | `1234` |

---

## 📡 REST API Reference

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/stations` | Retrieve list of all 75 assembly stations and descriptions. |
| `GET` | `/api/engines` | Retrieve list of all tracked engines with status and current station. |
| `POST` | `/api/engines/init` | Create or register a new engine barcode. |
| `GET` | `/api/engines/:barcode` | Get complete history card and inspection details for an engine. |
| `POST` | `/api/engines/:barcode/section/:sectionId` | Submit station inspection test cases, operator token, and pass engine to next station. |

---

## 📁 Repository Structure

```
Ashok-Leyland-Engine/
├── data/                    # Local storage database fallback (engines.json)
├── src/                     # React / Vite application source files
│   ├── App.tsx
│   ├── index.css
│   └── main.tsx
├── .env.example             # Example environment variable file
├── app.js                   # Client-side MES business logic & station workflows
├── index.html               # Multi-view MES interface (Login, Workspace, Master Card)
├── metadata.json            # Application metadata & configuration
├── package.json             # NPM dependencies and scripts
├── server.js                # Zero-dependency Node.js HTTP/Express API & Storage Server
├── styles.css               # Ashok Leyland Industrial Design System Stylesheet
├── tsconfig.json            # TypeScript configuration
└── vite.config.ts           # Vite bundler configuration
```

---

## 📄 License & Compliance

Designed and developed for **Ashok Leyland Engine Division** - Hosur Plant - I.  
Complies with **ISO/TS 16949 / IATF 16949 Automotive Quality Management Standards** and **Bharat Stage VI (BS-VI)** emission compliance tracking.
