# 🌾 FarmLink Local

**FarmLink Local** is a direct farmer-to-buyer agricultural marketplace built on the MERN stack. It empowers local farmers to list bulk and harvest lots of crops such as **paddy, cotton, red chillies, maize, turmeric, groundnut**, and more—enabling food processors, millers, exporters, and wholesale buyers to discover and purchase crops directly without exploitative middlemen.

---

## 🛠️ Technology Stack

### Frontend (`/client`)
- **Library/Framework**: [React 18](https://react.dev/) + [Vite](https://vitejs.dev/)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Routing**: [React Router v6](https://reactrouter.com/)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **Icons**: [Lucide React](https://lucide.dev/)
- **Dev Server Port**: `http://localhost:5173` (with `/api` proxy to backend)

### Backend (`/server`)
- **Runtime**: [Node.js](https://nodejs.org/) (v20+ recommended)
- **Framework**: [Express.js](https://expressjs.com/)
- **Language**: [TypeScript](https://www.typescriptlang.org/) with `tsx` fast runner
- **CORS**: Configured with credentials & allowed origin support
- **Error Handling**: Centralized error middleware with structured JSON responses
- **Server Port**: `http://localhost:5000`

### Database
- **Database**: [MongoDB](https://www.mongodb.com/)
- **ODM**: [Mongoose v8](https://mongoosejs.com/)
- Resilient connection management with status reporting via `/api/health`.

---

## 📁 Project Structure

```
FarmLink-Local/
├── client/                     # Vite + React + TypeScript + Tailwind Frontend
│   ├── public/                 # Static assets
│   ├── src/
│   │   ├── components/         # Navbar, Hero, CropShowcase, ValueProps, HealthBadge, Footer
│   │   ├── pages/              # LandingPage, NotFoundPage
│   │   ├── services/           # api.ts (health check & backend communication)
│   │   ├── types/              # TypeScript interfaces
│   │   ├── App.tsx             # React Router routing definitions
│   │   ├── index.css           # Tailwind base styles and font declarations
│   │   └── main.tsx            # React DOM mounting
│   ├── index.html              # HTML5 entry with Google Fonts
│   ├── package.json            # Client scripts & dependencies
│   ├── tailwind.config.js      # Agricultural color palette tokens
│   ├── tsconfig.json           # TypeScript configuration for React
│   └── vite.config.ts          # Vite proxy & bundler settings
│
├── server/                     # Express + TypeScript + Mongoose Backend
│   ├── src/
│   │   ├── config/             # env.ts (environment parsing), db.ts (MongoDB connection)
│   │   ├── controllers/        # health.controller.ts
│   │   ├── middleware/         # errorHandler.ts, notFound.ts
│   │   ├── routes/             # health.routes.ts
│   │   ├── app.ts              # Express application configuration & CORS
│   │   └── server.ts           # Server bootstrap and graceful shutdown
│   ├── .env.example            # Backend environment template
│   ├── package.json            # Server scripts & dependencies
│   └── tsconfig.json           # Backend TypeScript configuration
│
├── .env.example                # Root environment reference
├── .gitignore                  # Git ignore definitions
├── package.json                # Root orchestration scripts
└── README.md                   # Project documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites
- **Node.js**: v20 or higher (`node -v`)
- **npm**: v10 or higher (`npm -v`)
- **MongoDB**: Local MongoDB instance running on port 27017 or a MongoDB Atlas URI *(Optional for Phase 1; server runs resiliently with fallback status if MongoDB is offline)*.

---

### 2. Environment Setup

Create your `.env` files from the provided templates:

#### Root & Server
```bash
# In server directory
cp server/.env.example server/.env
```

Default variables in `server/.env`:
```env
PORT=5000
NODE_ENV=development
CLIENT_URL=http://localhost:5173
MONGODB_URI=mongodb://localhost:27017/farmlink_local
```

#### Client
```bash
# In client directory
cp client/.env.example client/.env
```

Default variables in `client/.env`:
```env
VITE_API_URL=http://localhost:5000
```

---

### 3. Install Dependencies

You can install dependencies for root, server, and client:

```bash
# From the root directory:
npm.cmd install
npm.cmd --prefix server install
npm.cmd --prefix client install
```

*(Note: On Windows PowerShell, use `npm.cmd` if PowerShell execution policy restricts script execution).*

---

### 4. Running the Application

You can run the server and client concurrently or in separate terminal tabs:

#### Option A: Run Both Concurrently (Recommended)
From the root directory:
```bash
npm.cmd run dev
```

#### Option B: Run Individually in Separate Terminals

**Terminal 1 (Backend Server):**
```bash
cd server
npm.cmd run dev
```
Backend will start at: `http://localhost:5000`

**Terminal 2 (Frontend Client):**
```bash
cd client
npm.cmd run dev
```
Frontend will be accessible at: `http://localhost:5173`

---

## 🩺 Health Check Verification

The backend exposes a health check endpoint at:
`GET http://localhost:5000/api/health`

### Sample Response:
```json
{
  "status": "ok",
  "service": "FarmLink Local API",
  "version": "1.0.0",
  "environment": "development",
  "uptime": 42,
  "timestamp": "2026-09-23T12:00:00.000Z",
  "database": {
    "status": "connected",
    "connected": true
  }
}
```

The frontend landing page also features:
- A live **status badge** in the navigation bar.
- An interactive **Backend Health Verification console** with a live ping button and JSON payload viewer.

---

## 🌾 Crops Supported in Marketplace Showcase
- **Paddy / Rice** (*Basmati & non-basmati varieties*)
- **Raw Cotton** (*Shankar-6, DCH-32 long & medium staple*)
- **Red Chillies** (*Teja, Byadgi, Sanam high pungency*)
- **Maize / Corn** (*Feed & starch factory grade*)
- **Turmeric Fingers** (*Salem & Nizamabad high-curcumin*)
- **Groundnut / Peanut** (*Bold & Java oilseeds*)

---

## 🛡️ Next Development Steps
- **Phase 2**: Authentication & User Roles (Farmers, Buyers, Admin/Inspectors)
- **Phase 3**: Crop Listing CRUD with Quality & Moisture Metrics
- **Phase 4**: Discovery, Search, and Filtering by Distance / State / Grade
- **Phase 5**: Orders, Escrow / Payment Flow, and AI mandi price predictions
