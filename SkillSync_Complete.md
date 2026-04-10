# ⚡ SkillSync — Complete Source Code
> All 41 files combined. Copy each section into its correct path.
---
## 📁 Table of Contents
- [`.gitignore`](#gitignore)
- [`README.md`](#readmemd)
- [`client/.env`](#clientenv)
- [`client/index.html`](#clientindexhtml)
- [`client/package.json`](#clientpackagejson)
- [`client/postcss.config.js`](#clientpostcssconfigjs)
- [`client/src/App.jsx`](#clientsrcappjsx)
- [`client/src/components/Navbar.jsx`](#clientsrccomponentsnavbarjsx)
- [`client/src/components/ScoreRing.jsx`](#clientsrccomponentsscoreringjsx)
- [`client/src/components/SkillTag.jsx`](#clientsrccomponentsskilltagjsx)
- [`client/src/components/Spinner.jsx`](#clientsrccomponentsspinnerjsx)
- [`client/src/context/AuthContext.jsx`](#clientsrccontextauthcontextjsx)
- [`client/src/index.css`](#clientsrcindexcss)
- [`client/src/main.jsx`](#clientsrcmainjsx)
- [`client/src/pages/Dashboard.jsx`](#clientsrcpagesdashboardjsx)
- [`client/src/pages/Landing.jsx`](#clientsrcpageslandingjsx)
- [`client/src/pages/Login.jsx`](#clientsrcpagesloginjsx)
- [`client/src/pages/Matches.jsx`](#clientsrcpagesmatchesjsx)
- [`client/src/pages/Profile.jsx`](#clientsrcpagesprofilejsx)
- [`client/src/pages/Projects.jsx`](#clientsrcpagesprojectsjsx)
- [`client/src/pages/Register.jsx`](#clientsrcpagesregisterjsx)
- [`client/src/utils/api.js`](#clientsrcutilsapijs)
- [`client/tailwind.config.js`](#clienttailwindconfigjs)
- [`client/vite.config.js`](#clientviteconfigjs)
- [`package.json`](#packagejson)
- [`server/.env`](#serverenv)
- [`server/config/db.js`](#serverconfigdbjs)
- [`server/controllers/authController.js`](#servercontrollersauthcontrollerjs)
- [`server/controllers/matchController.js`](#servercontrollersmatchcontrollerjs)
- [`server/controllers/projectController.js`](#servercontrollersprojectcontrollerjs)
- [`server/controllers/userController.js`](#servercontrollersusercontrollerjs)
- [`server/index.js`](#serverindexjs)
- [`server/middleware/authMiddleware.js`](#servermiddlewareauthmiddlewarejs)
- [`server/models/Match.js`](#servermodelsmatchjs)
- [`server/models/Project.js`](#servermodelsprojectjs)
- [`server/models/User.js`](#servermodelsuserjs)
- [`server/package.json`](#serverpackagejson)
- [`server/routes/authRoutes.js`](#serverroutesauthroutesjs)
- [`server/routes/matchRoutes.js`](#serverroutesmatchroutesjs)
- [`server/routes/projectRoutes.js`](#serverroutesprojectroutesjs)
- [`server/routes/userRoutes.js`](#serverroutesuserroutesjs)

---

## `.gitignore`

```
# Dependencies
node_modules/
client/node_modules/
server/node_modules/

# Environment variables
.env
.env.local
.env.production
server/.env
client/.env

# Build output
client/dist/
client/build/

# Logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
logs/

# OS
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo

# Misc
.cache/
coverage/
```

---

## `README.md`

```markdown
# ⚡ SkillSync — AI Team Formation System

> Match with compatible teammates instantly. Built for hackathons, academic projects, and technical competitions.

![SkillSync](https://img.shields.io/badge/SkillSync-v1.0.0-0e83f5?style=for-the-badge)
![Node](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb)

---

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Running the App](#running-the-app)
- [API Endpoints](#api-endpoints)
- [Matching Algorithm](#matching-algorithm)
- [Deployment](#deployment)
- [GitHub Push Commands](#github-push-commands)

---

## ✨ Features

- 🔐 **JWT Authentication** — Register, login, logout with bcrypt password hashing
- 👤 **User Profiles** — Skills array, experience level, bio, GitHub, LinkedIn
- 🤖 **AI Matching** — Skill tokenization + Jaccard similarity scoring
- 📊 **Compatibility Scores** — 0–100% score for every potential teammate
- 💡 **Project Suggestions** — 16 curated projects matched to your skillset
- 🎨 **Modern UI** — Dark theme, responsive, animated with Tailwind CSS
- 🔔 **Toast Notifications** — Real-time feedback on every action
- ⚡ **Loading States** — Spinners and skeleton states throughout

---

## 🛠 Tech Stack

| Layer      | Technology                        |
|------------|-----------------------------------|
| Frontend   | React 18, Vite, Tailwind CSS      |
| Backend    | Node.js, Express.js               |
| Database   | MongoDB (Mongoose ODM)            |
| Auth       | JWT + bcryptjs                    |
| HTTP       | Axios (with interceptors)         |
| Icons      | Lucide React                      |
| Toasts     | React Hot Toast                   |
| Routing    | React Router v6                   |

---

## 📁 Project Structure

```
skillsync/
├── client/                     # React frontend (Vite)
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── SkillTag.jsx
│   │   │   ├── ScoreRing.jsx
│   │   │   └── Spinner.jsx
│   │   ├── context/
│   │   │   └── AuthContext.jsx
│   │   ├── pages/
│   │   │   ├── Landing.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── Matches.jsx
│   │   │   ├── Projects.jsx
│   │   │   └── Profile.jsx
│   │   ├── utils/
│   │   │   └── api.js
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── index.html
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── package.json
│
├── server/                     # Node.js backend
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── userController.js
│   │   ├── matchController.js
│   │   └── projectController.js
│   ├── middleware/
│   │   └── authMiddleware.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Match.js
│   │   └── Project.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── userRoutes.js
│   │   ├── matchRoutes.js
│   │   └── projectRoutes.js
│   ├── index.js
│   └── package.json
│
├── package.json                # Root — concurrent dev scripts
├── .gitignore
└── README.md
```

---

## ✅ Prerequisites

Make sure you have these installed:

- **Node.js** v18 or higher → [nodejs.org](https://nodejs.org)
- **npm** v9+ (comes with Node)
- **MongoDB Atlas** account (free) → [mongodb.com/atlas](https://www.mongodb.com/atlas)
- **Git** → [git-scm.com](https://git-scm.com)

---

## 🚀 Installation

### Step 1 — Clone or download the project

```bash
git clone https://github.com/YOUR_USERNAME/skillsync.git
cd skillsync
```

### Step 2 — Install ALL dependencies at once

```bash
npm run install:all
```

This installs dependencies for the root, server, and client in one command.

Or install manually:

```bash
# Root
npm install

# Server
cd server && npm install

# Client
cd ../client && npm install
```

---

## 🔑 Environment Variables

### Server — `server/.env`

Create `server/.env` and fill in your values:

```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/skillsync?retryWrites=true&w=majority
JWT_SECRET=your_super_secret_key_here_make_it_long
JWT_EXPIRE=7d
NODE_ENV=development
CLIENT_URL=http://localhost:5173
```

**How to get your MongoDB URI:**
1. Go to [mongodb.com/atlas](https://www.mongodb.com/atlas) and create a free account
2. Create a new cluster (free M0 tier)
3. Click **Connect** → **Connect your application**
4. Copy the connection string and replace `<username>` and `<password>`
5. Add `0.0.0.0/0` to IP Whitelist (Network Access)

### Client — `client/.env`

```env
VITE_API_URL=/api
```

---

## ▶️ Running the App

### Development (both servers at once)

From the **root** directory:

```bash
npm run dev
```

This starts:
- **Backend** → `http://localhost:5000`
- **Frontend** → `http://localhost:5173`

### Run separately

```bash
# Server only
npm run server

# Client only
npm run client
```

### Production build

```bash
npm run build
```

---

## 📡 API Endpoints

### Authentication
| Method | Endpoint              | Access  | Description          |
|--------|----------------------|---------|----------------------|
| POST   | `/api/auth/register` | Public  | Register new user    |
| POST   | `/api/auth/login`    | Public  | Login user           |
| GET    | `/api/auth/me`       | Private | Get current user     |

### Users
| Method | Endpoint              | Access  | Description          |
|--------|----------------------|---------|----------------------|
| GET    | `/api/users/profile` | Private | Get own profile      |
| PUT    | `/api/users/update`  | Private | Update profile       |
| GET    | `/api/users`         | Private | Get all users        |

### Matching
| Method | Endpoint          | Access  | Description               |
|--------|------------------|---------|---------------------------|
| GET    | `/api/match`      | Private | Get all matches + scores  |
| GET    | `/api/match/:id`  | Private | Get match with specific user |

### Projects
| Method | Endpoint        | Access  | Description                  |
|--------|----------------|---------|------------------------------|
| GET    | `/api/projects` | Private | Get personalized suggestions |

---

## 🧠 Matching Algorithm

```
compatibilityScore = (commonSkills / totalUniqueSkills) × 100
```

**Steps:**
1. Normalize skills (lowercase, trim)
2. Tokenize both users' skill arrays into Sets
3. Find intersection (common skills)
4. Find union (total unique skills)
5. Calculate Jaccard similarity as percentage
6. Apply small experience-level bonus (±10%)
7. Sort results descending by score
8. Cache top 10 matches to MongoDB

**Example:**
```
User A: ['react', 'node.js', 'python', 'mongodb']
User B: ['react', 'node.js', 'docker', 'kubernetes']

Common: ['react', 'node.js'] → 2
Union:  ['react', 'node.js', 'python', 'mongodb', 'docker', 'kubernetes'] → 6

Score = (2 / 6) × 100 = 33%
```

---

## 🌐 Deployment

### Frontend → Vercel

```bash
cd client
npm run build

# Deploy with Vercel CLI
npx vercel --prod
```

Or connect your GitHub repo on [vercel.com](https://vercel.com).

Set build settings:
- **Framework**: Vite
- **Build command**: `npm run build`
- **Output directory**: `dist`
- **Environment variable**: `VITE_API_URL=https://your-backend.render.com/api`

### Backend → Render

1. Go to [render.com](https://render.com) → New Web Service
2. Connect your GitHub repo
3. Settings:
   - **Root directory**: `server`
   - **Build command**: `npm install`
   - **Start command**: `npm start`
4. Add environment variables from `server/.env`

### Database → MongoDB Atlas

Already cloud-hosted. Just whitelist `0.0.0.0/0` for Render's dynamic IPs.

---

## 📤 GitHub Push Commands

```bash
# 1. Initialize git repo (from project root)
git init

# 2. Add all files
git add .

# 3. First commit
git commit -m "feat: initial SkillSync full-stack app"

# 4. Create repo on GitHub, then add remote
git remote add origin https://github.com/YOUR_USERNAME/skillsync.git

# 5. Push to main branch
git branch -M main
git push -u origin main
```

**Future commits:**
```bash
git add .
git commit -m "feat: your feature description"
git push
```

---

## 📊 Database Collections

### Users
```json
{
  "_id": "ObjectId",
  "name": "Ada Lovelace",
  "email": "ada@example.com",
  "password": "<hashed>",
  "skills": ["python", "machine learning", "react"],
  "experienceLevel": "advanced",
  "bio": "Building AI tools",
  "github": "alovelace",
  "linkedin": "ada-lovelace",
  "isAvailable": true,
  "createdAt": "2024-01-01T00:00:00Z"
}
```

### Matches
```json
{
  "_id": "ObjectId",
  "userId": "ObjectId",
  "matchedUserId": "ObjectId",
  "compatibilityScore": 75,
  "commonSkills": ["python", "react"],
  "createdAt": "2024-01-01T00:00:00Z"
}
```

### Projects (virtual — in controller)
```json
{
  "title": "AI-Powered Portfolio Generator",
  "description": "...",
  "requiredSkills": ["react", "node.js", "openai"],
  "difficulty": "intermediate",
  "techStack": ["React", "Node.js", "OpenAI API"],
  "estimatedDuration": "3-4 weeks",
  "category": "Web Development",
  "matchScore": 85
}
```

---

## 🤝 Contributing

Pull requests welcome. For major changes, open an issue first.

---

## 📄 License

MIT © SkillSync 2024
```

---

## `client/.env`

```
VITE_API_URL=/api
```

---

## `client/index.html`

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="SkillSync – AI-powered team formation for hackathons and projects" />
    <title>SkillSync – AI Team Formation</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,400&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet" />
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

---

## `client/package.json`

```json
{
  "name": "skillsync-client",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "axios": "^1.6.2",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.20.1",
    "react-hot-toast": "^2.4.1",
    "lucide-react": "^0.294.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.43",
    "@types/react-dom": "^18.2.17",
    "@vitejs/plugin-react": "^4.2.1",
    "autoprefixer": "^10.4.16",
    "postcss": "^8.4.32",
    "tailwindcss": "^3.3.6",
    "vite": "^5.0.8"
  }
}
```

---

## `client/postcss.config.js`

```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

---

## `client/src/App.jsx`

```jsx
import { BrowserRouter, Routes, Route, Navigate } from 'react-router-dom'
import { AuthProvider, useAuth } from './context/AuthContext'
import Navbar from './components/Navbar'
import Landing from './pages/Landing'
import Login from './pages/Login'
import Register from './pages/Register'
import Dashboard from './pages/Dashboard'
import Profile from './pages/Profile'
import Matches from './pages/Matches'
import Projects from './pages/Projects'

const PrivateRoute = ({ children }) => {
  const { user, loading } = useAuth()
  if (loading) return (
    <div className="min-h-screen flex items-center justify-center">
      <div className="w-10 h-10 rounded-full border-2 border-brand-500 border-t-transparent animate-spin" />
    </div>
  )
  return user ? children : <Navigate to="/login" replace />
}

const PublicRoute = ({ children }) => {
  const { user, loading } = useAuth()
  if (loading) return null
  return user ? <Navigate to="/dashboard" replace /> : children
}

const Layout = ({ children }) => (
  <div className="min-h-screen flex flex-col">
    <Navbar />
    <main className="flex-1">{children}</main>
  </div>
)

export default function App() {
  return (
    <AuthProvider>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Layout><Landing /></Layout>} />
          <Route path="/login"    element={<PublicRoute><Layout><Login /></Layout></PublicRoute>} />
          <Route path="/register" element={<PublicRoute><Layout><Register /></Layout></PublicRoute>} />
          <Route path="/dashboard" element={<PrivateRoute><Layout><Dashboard /></Layout></PrivateRoute>} />
          <Route path="/profile"   element={<PrivateRoute><Layout><Profile /></Layout></PrivateRoute>} />
          <Route path="/matches"   element={<PrivateRoute><Layout><Matches /></Layout></PrivateRoute>} />
          <Route path="/projects"  element={<PrivateRoute><Layout><Projects /></Layout></PrivateRoute>} />
          <Route path="*" element={<Navigate to="/" replace />} />
        </Routes>
      </BrowserRouter>
    </AuthProvider>
  )
}
```

---

## `client/src/components/Navbar.jsx`

```jsx
import { useState } from 'react'
import { Link, useLocation, useNavigate } from 'react-router-dom'
import { useAuth } from '../context/AuthContext'
import { Zap, LayoutDashboard, Users, FolderGit2, User, LogOut, Menu, X } from 'lucide-react'

const navLinks = [
  { to: '/dashboard', label: 'Dashboard', icon: LayoutDashboard },
  { to: '/matches',   label: 'Teammates', icon: Users },
  { to: '/projects',  label: 'Projects',  icon: FolderGit2 },
  { to: '/profile',   label: 'Profile',   icon: User },
]

export default function Navbar() {
  const { user, logout } = useAuth()
  const { pathname } = useLocation()
  const navigate = useNavigate()
  const [open, setOpen] = useState(false)

  const handleLogout = () => {
    logout()
    navigate('/')
    setOpen(false)
  }

  const initials = user?.name
    ? user.name.split(' ').map(n => n[0]).join('').toUpperCase().slice(0, 2)
    : '?'

  return (
    <header className="sticky top-0 z-50 border-b border-white/5 glass">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 h-16 flex items-center justify-between">
        {/* Logo */}
        <Link to={user ? '/dashboard' : '/'} className="flex items-center gap-2.5 group">
          <div className="w-8 h-8 rounded-lg bg-brand-600 flex items-center justify-center shadow-lg shadow-brand-900/50 group-hover:bg-brand-500 transition-colors">
            <Zap className="w-4 h-4 text-white" strokeWidth={2.5} />
          </div>
          <span className="font-display font-bold text-white text-lg tracking-tight">
            Skill<span className="text-brand-400">Sync</span>
          </span>
        </Link>

        {/* Desktop nav */}
        {user ? (
          <nav className="hidden md:flex items-center gap-1">
            {navLinks.map(({ to, label, icon: Icon }) => (
              <Link
                key={to}
                to={to}
                className={`flex items-center gap-1.5 px-3 py-2 rounded-lg text-sm font-body transition-all duration-150 ${
                  pathname === to
                    ? 'bg-brand-600/20 text-brand-400'
                    : 'text-slate-400 hover:text-white hover:bg-white/5'
                }`}
              >
                <Icon className="w-4 h-4" />
                {label}
              </Link>
            ))}
          </nav>
        ) : (
          <nav className="hidden md:flex items-center gap-3">
            <Link to="/login"    className="btn-ghost">Sign In</Link>
            <Link to="/register" className="btn-primary">Get Started</Link>
          </nav>
        )}

        {/* Desktop user + logout */}
        {user && (
          <div className="hidden md:flex items-center gap-3">
            <div className="flex items-center gap-2.5 px-3 py-1.5 rounded-xl bg-surface-700/50 border border-white/5">
              <div className="w-7 h-7 rounded-lg bg-brand-600 flex items-center justify-center text-xs font-display font-bold text-white">
                {initials}
              </div>
              <span className="text-sm font-body text-slate-300 max-w-[120px] truncate">{user.name}</span>
            </div>
            <button onClick={handleLogout} className="btn-ghost text-slate-500 hover:text-red-400">
              <LogOut className="w-4 h-4" />
            </button>
          </div>
        )}

        {/* Mobile hamburger */}
        <button
          className="md:hidden btn-ghost p-2"
          onClick={() => setOpen(!open)}
          aria-label="Toggle menu"
        >
          {open ? <X className="w-5 h-5" /> : <Menu className="w-5 h-5" />}
        </button>
      </div>

      {/* Mobile drawer */}
      {open && (
        <div className="md:hidden border-t border-white/5 bg-surface-900/95 backdrop-blur-xl px-4 py-4 flex flex-col gap-1 animate-fade-in">
          {user ? (
            <>
              <div className="flex items-center gap-3 px-3 py-3 mb-2 rounded-xl bg-surface-700/50 border border-white/5">
                <div className="w-8 h-8 rounded-lg bg-brand-600 flex items-center justify-center text-sm font-display font-bold text-white">
                  {initials}
                </div>
                <div>
                  <p className="text-sm font-body font-medium text-white">{user.name}</p>
                  <p className="text-xs text-slate-500">{user.email}</p>
                </div>
              </div>
              {navLinks.map(({ to, label, icon: Icon }) => (
                <Link
                  key={to}
                  to={to}
                  onClick={() => setOpen(false)}
                  className={`flex items-center gap-3 px-4 py-3 rounded-xl text-sm font-body transition-all ${
                    pathname === to
                      ? 'bg-brand-600/20 text-brand-400'
                      : 'text-slate-400 hover:text-white hover:bg-white/5'
                  }`}
                >
                  <Icon className="w-4 h-4" />{label}
                </Link>
              ))}
              <button
                onClick={handleLogout}
                className="flex items-center gap-3 px-4 py-3 rounded-xl text-sm font-body text-red-400 hover:bg-red-500/10 mt-1 transition-all"
              >
                <LogOut className="w-4 h-4" /> Logout
              </button>
            </>
          ) : (
            <>
              <Link to="/login"    onClick={() => setOpen(false)} className="btn-ghost justify-center py-3">Sign In</Link>
              <Link to="/register" onClick={() => setOpen(false)} className="btn-primary justify-center py-3">Get Started</Link>
            </>
          )}
        </div>
      )}
    </header>
  )
}
```

---

## `client/src/components/ScoreRing.jsx`

```jsx
export default function ScoreRing({ score, size = 80, stroke = 6 }) {
  const r = (size - stroke) / 2
  const circ = 2 * Math.PI * r
  const offset = circ - (score / 100) * circ

  const color =
    score >= 70 ? '#2aa3ff' :
    score >= 40 ? '#a78bfa' :
    '#64748b'

  return (
    <div className="relative inline-flex items-center justify-center" style={{ width: size, height: size }}>
      <svg width={size} height={size} className="-rotate-90">
        {/* Track */}
        <circle
          cx={size / 2} cy={size / 2} r={r}
          fill="none" stroke="rgba(255,255,255,0.06)" strokeWidth={stroke}
        />
        {/* Progress */}
        <circle
          cx={size / 2} cy={size / 2} r={r}
          fill="none"
          stroke={color}
          strokeWidth={stroke}
          strokeLinecap="round"
          strokeDasharray={circ}
          strokeDashoffset={offset}
          style={{ transition: 'stroke-dashoffset 1s cubic-bezier(.4,0,.2,1)' }}
        />
      </svg>
      <div className="absolute inset-0 flex items-center justify-center flex-col">
        <span className="font-display font-bold text-white" style={{ fontSize: size * 0.22 }}>
          {score}%
        </span>
      </div>
    </div>
  )
}
```

---

## `client/src/components/SkillTag.jsx`

```jsx
const colorMap = [
  'bg-brand-500/15 text-brand-300 border-brand-500/20',
  'bg-accent-500/15 text-accent-400 border-accent-500/20',
  'bg-emerald-500/15 text-emerald-400 border-emerald-500/20',
  'bg-amber-500/15 text-amber-400 border-amber-500/20',
  'bg-rose-500/15 text-rose-400 border-rose-500/20',
  'bg-cyan-500/15 text-cyan-400 border-cyan-500/20',
]

const hash = (str) => str.split('').reduce((a, c) => a + c.charCodeAt(0), 0)

export default function SkillTag({ skill, highlight = false, size = 'sm' }) {
  const color = highlight
    ? 'bg-brand-500/25 text-brand-200 border-brand-400/40 ring-1 ring-brand-500/30'
    : colorMap[hash(skill) % colorMap.length]

  return (
    <span className={`badge border ${color} ${size === 'xs' ? 'text-xs px-2 py-0.5' : 'text-xs'}`}>
      {skill}
    </span>
  )
}
```

---

## `client/src/components/Spinner.jsx`

```jsx
export default function Spinner({ size = 'md', className = '' }) {
  const sizes = { sm: 'w-4 h-4', md: 'w-8 h-8', lg: 'w-12 h-12' }
  return (
    <div className={`${sizes[size]} rounded-full border-2 border-brand-500 border-t-transparent animate-spin ${className}`} />
  )
}

export function PageSpinner() {
  return (
    <div className="flex flex-col items-center justify-center min-h-[40vh] gap-4">
      <Spinner size="lg" />
      <p className="text-slate-500 text-sm font-body">Loading…</p>
    </div>
  )
}
```

---

## `client/src/context/AuthContext.jsx`

```jsx
import { createContext, useContext, useState, useEffect, useCallback } from 'react'
import API from '../utils/api'
import toast from 'react-hot-toast'

const AuthContext = createContext(null)

export const AuthProvider = ({ children }) => {
  const [user, setUser]       = useState(null)
  const [loading, setLoading] = useState(true)

  // Restore session on mount
  useEffect(() => {
    const token = localStorage.getItem('skillsync_token')
    const saved = localStorage.getItem('skillsync_user')
    if (token && saved) {
      try { setUser(JSON.parse(saved)) } catch { /* ignore */ }
    }
    setLoading(false)
  }, [])

  const persist = (token, userData) => {
    localStorage.setItem('skillsync_token', token)
    localStorage.setItem('skillsync_user', JSON.stringify(userData))
    setUser(userData)
  }

  const register = async (formData) => {
    const { data } = await API.post('/auth/register', formData)
    persist(data.token, data.user)
    toast.success('Welcome to SkillSync! 🚀')
    return data
  }

  const login = async (formData) => {
    const { data } = await API.post('/auth/login', formData)
    persist(data.token, data.user)
    toast.success(`Welcome back, ${data.user.name}!`)
    return data
  }

  const logout = useCallback(() => {
    localStorage.removeItem('skillsync_token')
    localStorage.removeItem('skillsync_user')
    setUser(null)
    toast.success('Logged out successfully.')
  }, [])

  const refreshUser = async () => {
    try {
      const { data } = await API.get('/auth/me')
      localStorage.setItem('skillsync_user', JSON.stringify(data.user))
      setUser(data.user)
      return data.user
    } catch { /* ignore */ }
  }

  return (
    <AuthContext.Provider value={{ user, loading, register, login, logout, refreshUser, setUser }}>
      {children}
    </AuthContext.Provider>
  )
}

export const useAuth = () => {
  const ctx = useContext(AuthContext)
  if (!ctx) throw new Error('useAuth must be used inside AuthProvider')
  return ctx
}
```

---

## `client/src/index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  *, *::before, *::after { box-sizing: border-box; }

  html {
    scroll-behavior: smooth;
  }

  body {
    @apply bg-surface-900 text-slate-100 font-body antialiased;
    background-image:
      radial-gradient(ellipse 80% 50% at 50% -20%, rgba(14,131,245,0.12), transparent),
      url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%230e83f5' fill-opacity='0.03'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }

  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { @apply bg-surface-800; }
  ::-webkit-scrollbar-thumb { @apply bg-surface-500 rounded-full; }
  ::-webkit-scrollbar-thumb:hover { @apply bg-brand-700; }

  ::selection { @apply bg-brand-600/40 text-white; }
}

@layer components {
  .glass {
    @apply bg-surface-800/60 backdrop-blur-xl border border-white/5;
  }

  .glass-hover {
    @apply hover:bg-surface-700/60 hover:border-white/10 transition-all duration-200;
  }

  .btn-primary {
    @apply inline-flex items-center gap-2 px-5 py-2.5 rounded-xl bg-brand-600 hover:bg-brand-500 text-white font-display font-semibold text-sm transition-all duration-200 shadow-lg shadow-brand-900/30 hover:shadow-brand-600/25 hover:-translate-y-0.5 active:translate-y-0 disabled:opacity-50 disabled:cursor-not-allowed disabled:hover:translate-y-0;
  }

  .btn-secondary {
    @apply inline-flex items-center gap-2 px-5 py-2.5 rounded-xl bg-surface-600 hover:bg-surface-500 text-slate-200 font-display font-semibold text-sm border border-white/10 hover:border-white/20 transition-all duration-200 hover:-translate-y-0.5 active:translate-y-0 disabled:opacity-50 disabled:cursor-not-allowed;
  }

  .btn-ghost {
    @apply inline-flex items-center gap-2 px-4 py-2 rounded-lg text-slate-400 hover:text-white hover:bg-white/5 font-body text-sm transition-all duration-150;
  }

  .input-field {
    @apply w-full px-4 py-3 rounded-xl bg-surface-700 border border-white/10 text-slate-100 placeholder:text-slate-500 focus:outline-none focus:ring-2 focus:ring-brand-500/50 focus:border-brand-500/50 transition-all duration-200 font-body text-sm;
  }

  .label {
    @apply block text-xs font-display font-semibold text-slate-400 uppercase tracking-widest mb-2;
  }

  .card {
    @apply glass rounded-2xl p-6 glass-hover;
  }

  .section-title {
    @apply font-display font-bold text-white;
  }

  .badge {
    @apply inline-flex items-center px-2.5 py-1 rounded-lg text-xs font-mono font-medium;
  }

  .score-ring {
    stroke-linecap: round;
    transform-origin: center;
    transform: rotate(-90deg);
    transition: stroke-dashoffset 1s ease;
  }

  .shimmer {
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.04), transparent);
    background-size: 200% 100%;
    animation: shimmer 1.5s infinite;
  }
}

@keyframes shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}

.float { animation: float 4s ease-in-out infinite; }

/* Stagger animations for lists */
.stagger-item { opacity: 0; animation: slideUp 0.4s ease forwards; }
.stagger-item:nth-child(1) { animation-delay: 0.05s; }
.stagger-item:nth-child(2) { animation-delay: 0.1s; }
.stagger-item:nth-child(3) { animation-delay: 0.15s; }
.stagger-item:nth-child(4) { animation-delay: 0.2s; }
.stagger-item:nth-child(5) { animation-delay: 0.25s; }
.stagger-item:nth-child(6) { animation-delay: 0.3s; }
.stagger-item:nth-child(7) { animation-delay: 0.35s; }
.stagger-item:nth-child(8) { animation-delay: 0.4s; }

@keyframes slideUp {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

---

## `client/src/main.jsx`

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import { Toaster } from 'react-hot-toast'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
    <Toaster
      position="top-right"
      toastOptions={{
        duration: 3500,
        style: {
          background: '#1a2235',
          color: '#f1f5f9',
          border: '1px solid rgba(255,255,255,0.08)',
          borderRadius: '12px',
          fontFamily: 'DM Sans, sans-serif',
          fontSize: '14px',
          padding: '12px 16px',
          boxShadow: '0 20px 40px rgba(0,0,0,0.4)',
        },
        success: { iconTheme: { primary: '#2aa3ff', secondary: '#0d1220' } },
        error:   { iconTheme: { primary: '#f87171', secondary: '#0d1220' } },
      }}
    />
  </React.StrictMode>,
)
```

---

## `client/src/pages/Dashboard.jsx`

```jsx
import { useState, useEffect } from 'react'
import { Link } from 'react-router-dom'
import { useAuth } from '../context/AuthContext'
import API from '../utils/api'
import SkillTag from '../components/SkillTag'
import ScoreRing from '../components/ScoreRing'
import { PageSpinner } from '../components/Spinner'
import {
  Users, FolderGit2, Zap, ArrowRight, TrendingUp,
  Github, Linkedin, ChevronRight, AlertCircle
} from 'lucide-react'

const expColor = {
  beginner: 'bg-emerald-500/15 text-emerald-400 border-emerald-500/25',
  intermediate: 'bg-brand-500/15 text-brand-400 border-brand-500/25',
  advanced: 'bg-accent-500/15 text-accent-400 border-accent-500/25',
  expert: 'bg-amber-500/15 text-amber-400 border-amber-500/25',
}

export default function Dashboard() {
  const { user } = useAuth()
  const [matches, setMatches]   = useState([])
  const [projects, setProjects] = useState([])
  const [loading, setLoading]   = useState(true)

  useEffect(() => {
    const fetchAll = async () => {
      try {
        const [mRes, pRes] = await Promise.all([
          API.get('/match'),
          API.get('/projects'),
        ])
        setMatches(mRes.data.matches?.slice(0, 3) || [])
        setProjects(pRes.data.projects?.slice(0, 3) || [])
      } catch { /* silently handle */ }
      finally { setLoading(false) }
    }
    fetchAll()
  }, [])

  if (loading) return <PageSpinner />

  const initials = user?.name?.split(' ').map(n => n[0]).join('').toUpperCase().slice(0, 2) || '?'
  const hasSkills = user?.skills?.length > 0

  return (
    <div className="max-w-7xl mx-auto px-4 sm:px-6 py-10">
      {/* Welcome banner */}
      <div className="mb-8 animate-fade-in">
        <h1 className="font-display font-bold text-3xl text-white">
          Hey, {user?.name?.split(' ')[0]} 👋
        </h1>
        <p className="text-slate-400 mt-1 text-sm">Here's your SkillSync overview</p>
      </div>

      {/* Skills warning */}
      {!hasSkills && (
        <div className="mb-6 flex items-start gap-3 p-4 rounded-xl bg-amber-500/10 border border-amber-500/20 text-amber-300 text-sm animate-slide-up">
          <AlertCircle className="w-4 h-4 mt-0.5 shrink-0" />
          <span>
            Your profile has no skills yet.{' '}
            <Link to="/profile" className="underline underline-offset-2 hover:text-amber-200 transition-colors">
              Update your profile
            </Link>{' '}
            to start getting teammate matches.
          </span>
        </div>
      )}

      <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
        {/* Profile card */}
        <div className="lg:col-span-1 flex flex-col gap-6">
          <div className="card animate-slide-up">
            <div className="flex items-start justify-between mb-5">
              <div className="flex items-center gap-3">
                <div className="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-500 to-accent-500 flex items-center justify-center text-xl font-display font-bold text-white shadow-lg">
                  {initials}
                </div>
                <div>
                  <h2 className="font-display font-semibold text-white text-lg leading-tight">{user?.name}</h2>
                  <p className="text-slate-500 text-xs">{user?.email}</p>
                </div>
              </div>
              <span className={`badge border text-xs capitalize ${expColor[user?.experienceLevel] || expColor.beginner}`}>
                {user?.experienceLevel}
              </span>
            </div>

            {user?.bio && (
              <p className="text-slate-400 text-sm leading-relaxed mb-4">{user.bio}</p>
            )}

            {/* Skills */}
            <div className="mb-5">
              <p className="text-xs font-display font-semibold text-slate-500 uppercase tracking-wider mb-2.5">
                Skills ({user?.skills?.length || 0})
              </p>
              {hasSkills ? (
                <div className="flex flex-wrap gap-1.5">
                  {user.skills.map(s => <SkillTag key={s} skill={s} />)}
                </div>
              ) : (
                <p className="text-slate-600 text-xs italic">No skills added yet</p>
              )}
            </div>

            {/* Links */}
            <div className="flex gap-2 flex-wrap">
              {user?.github && (
                <a href={user.github.startsWith('http') ? user.github : `https://github.com/${user.github}`}
                  target="_blank" rel="noopener noreferrer"
                  className="btn-ghost text-xs px-3 py-1.5 gap-1.5">
                  <Github className="w-3.5 h-3.5" /> GitHub
                </a>
              )}
              {user?.linkedin && (
                <a href={user.linkedin.startsWith('http') ? user.linkedin : `https://linkedin.com/in/${user.linkedin}`}
                  target="_blank" rel="noopener noreferrer"
                  className="btn-ghost text-xs px-3 py-1.5 gap-1.5">
                  <Linkedin className="w-3.5 h-3.5" /> LinkedIn
                </a>
              )}
            </div>

            <Link to="/profile" className="btn-secondary w-full justify-center mt-4 text-sm">
              Update Profile
            </Link>
          </div>

          {/* Stats mini-cards */}
          <div className="grid grid-cols-2 gap-3">
            {[
              { label: 'Skill Count', value: user?.skills?.length || 0, icon: Zap, color: 'text-brand-400' },
              { label: 'Top Matches', value: matches.length, icon: Users, color: 'text-accent-400' },
              { label: 'Projects',    value: projects.length, icon: FolderGit2, color: 'text-emerald-400' },
              { label: 'Top Score',   value: matches[0] ? `${matches[0].compatibilityScore}%` : '—', icon: TrendingUp, color: 'text-amber-400' },
            ].map(({ label, value, icon: Icon, color }) => (
              <div key={label} className="card py-4 px-4 text-center stagger-item">
                <Icon className={`w-5 h-5 mx-auto mb-1.5 ${color}`} />
                <div className="font-display font-bold text-xl text-white">{value}</div>
                <div className="text-xs text-slate-500 mt-0.5">{label}</div>
              </div>
            ))}
          </div>
        </div>

        {/* Right column */}
        <div className="lg:col-span-2 flex flex-col gap-6">
          {/* Top Matches */}
          <div className="card animate-slide-up" style={{ animationDelay: '0.1s' }}>
            <div className="flex items-center justify-between mb-5">
              <div className="flex items-center gap-2">
                <Users className="w-5 h-5 text-brand-400" />
                <h2 className="font-display font-semibold text-white">Suggested Teammates</h2>
              </div>
              <Link to="/matches" className="btn-ghost text-xs gap-1">
                Find Teammates <ChevronRight className="w-3.5 h-3.5" />
              </Link>
            </div>

            {matches.length === 0 ? (
              <div className="text-center py-8 text-slate-600">
                <Users className="w-10 h-10 mx-auto mb-2 opacity-30" />
                <p className="text-sm">Add skills to see matched teammates</p>
              </div>
            ) : (
              <div className="flex flex-col gap-3">
                {matches.map((m, i) => (
                  <div key={m.user._id} className="flex items-center gap-4 p-3 rounded-xl bg-surface-700/40 hover:bg-surface-700/70 transition-colors stagger-item">
                    <div className="w-10 h-10 rounded-xl bg-gradient-to-br from-brand-600 to-accent-600 flex items-center justify-center text-sm font-display font-bold text-white shrink-0">
                      {m.user.name.split(' ').map(n => n[0]).join('').toUpperCase().slice(0, 2)}
                    </div>
                    <div className="flex-1 min-w-0">
                      <div className="flex items-center gap-2">
                        <p className="font-display font-semibold text-white text-sm truncate">{m.user.name}</p>
                        <span className={`badge border text-xs capitalize ${expColor[m.user.experienceLevel] || expColor.beginner}`}>
                          {m.user.experienceLevel}
                        </span>
                      </div>
                      <div className="flex flex-wrap gap-1 mt-1">
                        {m.commonSkills.slice(0, 3).map(s => (
                          <SkillTag key={s} skill={s} highlight size="xs" />
                        ))}
                        {m.commonSkills.length > 3 && (
                          <span className="text-xs text-slate-600">+{m.commonSkills.length - 3}</span>
                        )}
                      </div>
                    </div>
                    <ScoreRing score={m.compatibilityScore} size={52} stroke={5} />
                  </div>
                ))}
              </div>
            )}
          </div>

          {/* Project Ideas */}
          <div className="card animate-slide-up" style={{ animationDelay: '0.15s' }}>
            <div className="flex items-center justify-between mb-5">
              <div className="flex items-center gap-2">
                <FolderGit2 className="w-5 h-5 text-emerald-400" />
                <h2 className="font-display font-semibold text-white">Project Ideas</h2>
              </div>
              <Link to="/projects" className="btn-ghost text-xs gap-1">
                Get Project Ideas <ChevronRight className="w-3.5 h-3.5" />
              </Link>
            </div>

            {projects.length === 0 ? (
              <div className="text-center py-8 text-slate-600">
                <FolderGit2 className="w-10 h-10 mx-auto mb-2 opacity-30" />
                <p className="text-sm">No project suggestions yet</p>
              </div>
            ) : (
              <div className="grid grid-cols-1 sm:grid-cols-3 gap-3">
                {projects.map((p, i) => (
                  <div key={p.title} className="p-3.5 rounded-xl bg-surface-700/40 border border-white/5 hover:border-white/10 transition-colors stagger-item flex flex-col gap-2">
                    <div className="flex items-start justify-between gap-2">
                      <h3 className="font-display font-semibold text-white text-sm leading-snug">{p.title}</h3>
                      <span className={`badge border shrink-0 ${
                        p.difficulty === 'beginner' ? 'bg-emerald-500/15 text-emerald-400 border-emerald-500/20' :
                        p.difficulty === 'intermediate' ? 'bg-brand-500/15 text-brand-400 border-brand-500/20' :
                        'bg-red-500/15 text-red-400 border-red-500/20'
                      }`}>{p.difficulty}</span>
                    </div>
                    <div className="flex flex-wrap gap-1">
                      {p.techStack.slice(0, 3).map(t => (
                        <span key={t} className="text-xs font-mono text-slate-500">{t}</span>
                      ))}
                    </div>
                    {p.matchScore > 0 && (
                      <div className="flex items-center gap-1 mt-auto">
                        <div className="h-1 flex-1 rounded-full bg-surface-600">
                          <div className="h-full rounded-full bg-brand-500" style={{ width: `${p.matchScore}%` }} />
                        </div>
                        <span className="text-xs text-brand-400 font-mono">{p.matchScore}%</span>
                      </div>
                    )}
                  </div>
                ))}
              </div>
            )}
          </div>
        </div>
      </div>
    </div>
  )
}
```

---

## `client/src/pages/Landing.jsx`

```jsx
import { Link } from 'react-router-dom'
import { Zap, Users, FolderGit2, Brain, ArrowRight, CheckCircle2, Star } from 'lucide-react'

const features = [
  { icon: Brain,      title: 'AI Skill Matching',       desc: 'Our algorithm tokenizes and scores skill overlap to find your perfect teammates instantly.' },
  { icon: Users,      title: 'Compatibility Scores',    desc: 'Every match comes with a 0–100% compatibility score so you know exactly how well you align.' },
  { icon: FolderGit2, title: 'Project Suggestions',     desc: 'Get curated project ideas tailored to your team\'s combined tech stack and experience.' },
  { icon: Zap,        title: 'Instant Team Formation',  desc: 'Cut team formation time from 30 minutes to under 2 minutes at any hackathon.' },
]

const stats = [
  { value: '92%', label: 'Skill balance improvement' },
  { value: '2min', label: 'Avg. team formation time' },
  { value: '4.7★', label: 'User satisfaction' },
]

export default function Landing() {
  return (
    <div className="overflow-hidden">
      {/* Hero */}
      <section className="relative min-h-[90vh] flex items-center">
        {/* BG orbs */}
        <div className="absolute inset-0 overflow-hidden pointer-events-none">
          <div className="absolute top-1/4 left-1/3 w-[600px] h-[600px] bg-brand-600/10 rounded-full blur-[120px]" />
          <div className="absolute bottom-1/4 right-1/4 w-[400px] h-[400px] bg-accent-600/8 rounded-full blur-[100px]" />
        </div>

        <div className="relative max-w-7xl mx-auto px-4 sm:px-6 py-24 text-center">
          <div className="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-brand-600/10 border border-brand-500/20 text-brand-400 text-sm font-body mb-8 animate-fade-in">
            <Zap className="w-3.5 h-3.5" />
            AI-Powered Team Formation for Hackathons
          </div>

          <h1 className="font-display font-extrabold text-5xl sm:text-6xl md:text-7xl text-white leading-[1.08] tracking-tight mb-6 animate-slide-up">
            Find Your Perfect<br />
            <span className="text-transparent bg-clip-text bg-gradient-to-r from-brand-400 via-brand-300 to-accent-400">
              Dream Team
            </span>
          </h1>

          <p className="max-w-2xl mx-auto text-lg text-slate-400 font-body leading-relaxed mb-10 animate-slide-up" style={{ animationDelay: '0.1s' }}>
            SkillSync analyzes your skills and instantly matches you with compatible teammates.
            Stop wasting time on random grouping — build balanced teams that win.
          </p>

          <div className="flex flex-col sm:flex-row items-center justify-center gap-4 animate-slide-up" style={{ animationDelay: '0.2s' }}>
            <Link to="/register" className="btn-primary text-base px-7 py-3.5">
              Start Matching Free <ArrowRight className="w-4 h-4" />
            </Link>
            <Link to="/login" className="btn-secondary text-base px-7 py-3.5">
              Sign In
            </Link>
          </div>

          {/* Stats */}
          <div className="mt-20 grid grid-cols-3 gap-6 max-w-xl mx-auto">
            {stats.map(({ value, label }) => (
              <div key={label} className="text-center">
                <div className="font-display font-bold text-3xl text-white">{value}</div>
                <div className="text-xs text-slate-500 mt-1 font-body">{label}</div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Features */}
      <section className="py-24 border-t border-white/5">
        <div className="max-w-7xl mx-auto px-4 sm:px-6">
          <div className="text-center mb-16">
            <h2 className="font-display font-bold text-4xl text-white mb-4">
              Everything you need to build a winning team
            </h2>
            <p className="text-slate-400 max-w-xl mx-auto">
              Powered by intelligent algorithms that understand your technical skillset.
            </p>
          </div>

          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            {features.map(({ icon: Icon, title, desc }, i) => (
              <div key={title} className="card group stagger-item" style={{ animationDelay: `${i * 0.08}s` }}>
                <div className="w-10 h-10 rounded-xl bg-brand-600/15 flex items-center justify-center mb-4 group-hover:bg-brand-600/25 transition-colors">
                  <Icon className="w-5 h-5 text-brand-400" />
                </div>
                <h3 className="font-display font-semibold text-white mb-2">{title}</h3>
                <p className="text-sm text-slate-400 leading-relaxed">{desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* How it works */}
      <section className="py-24 border-t border-white/5">
        <div className="max-w-4xl mx-auto px-4 sm:px-6 text-center">
          <h2 className="font-display font-bold text-4xl text-white mb-4">How SkillSync Works</h2>
          <p className="text-slate-400 mb-16">From signup to dream team in minutes.</p>

          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            {[
              { step: '01', title: 'Create Profile', desc: 'Register and add your skills, experience level, and what you\'re looking to build.' },
              { step: '02', title: 'Get Matched',    desc: 'Our AI compares skill vectors across all users and ranks your best compatible teammates.' },
              { step: '03', title: 'Build Together', desc: 'View project suggestions based on your team\'s combined stack and start building.' },
            ].map(({ step, title, desc }) => (
              <div key={step} className="relative">
                <div className="font-mono text-6xl font-bold text-brand-600/15 mb-4 select-none">{step}</div>
                <h3 className="font-display font-semibold text-white text-lg mb-2">{title}</h3>
                <p className="text-sm text-slate-400 leading-relaxed">{desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* CTA */}
      <section className="py-24 border-t border-white/5">
        <div className="max-w-2xl mx-auto px-4 text-center">
          <div className="card border border-brand-500/20 bg-brand-600/5">
            <div className="flex justify-center mb-6">
              {[...Array(5)].map((_, i) => (
                <Star key={i} className="w-5 h-5 text-amber-400 fill-amber-400" />
              ))}
            </div>
            <h2 className="font-display font-bold text-3xl text-white mb-4">
              Ready to find your team?
            </h2>
            <p className="text-slate-400 mb-8">
              Join hundreds of students forming smarter teams at hackathons worldwide.
            </p>
            <Link to="/register" className="btn-primary text-base px-8 py-3.5">
              Create Free Account <ArrowRight className="w-4 h-4" />
            </Link>
          </div>
        </div>
      </section>
    </div>
  )
}
```

---

## `client/src/pages/Login.jsx`

```jsx
import { useState } from 'react'
import { Link, useNavigate } from 'react-router-dom'
import { useAuth } from '../context/AuthContext'
import { Zap, Mail, Lock, Eye, EyeOff, ArrowRight } from 'lucide-react'
import toast from 'react-hot-toast'

export default function Login() {
  const { login } = useAuth()
  const navigate = useNavigate()

  const [form, setForm]       = useState({ email: '', password: '' })
  const [show, setShow]       = useState(false)
  const [loading, setLoading] = useState(false)

  const handle = (e) => setForm(f => ({ ...f, [e.target.name]: e.target.value }))

  const submit = async (e) => {
    e.preventDefault()
    if (!form.email || !form.password) return toast.error('Please fill in all fields.')
    setLoading(true)
    try {
      await login(form)
      navigate('/dashboard')
    } catch (err) {
      toast.error(err.response?.data?.message || 'Login failed. Try again.')
    } finally {
      setLoading(false)
    }
  }

  return (
    <div className="min-h-[calc(100vh-4rem)] flex items-center justify-center px-4 py-16">
      {/* BG */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        <div className="absolute top-1/3 left-1/2 -translate-x-1/2 w-[500px] h-[500px] bg-brand-600/8 rounded-full blur-[100px]" />
      </div>

      <div className="relative w-full max-w-md animate-slide-up">
        {/* Header */}
        <div className="text-center mb-8">
          <div className="inline-flex w-12 h-12 items-center justify-center rounded-xl bg-brand-600 shadow-lg shadow-brand-900/50 mb-4">
            <Zap className="w-6 h-6 text-white" strokeWidth={2.5} />
          </div>
          <h1 className="font-display font-bold text-3xl text-white">Welcome back</h1>
          <p className="text-slate-400 mt-1 text-sm">Sign in to your SkillSync account</p>
        </div>

        {/* Card */}
        <div className="card">
          <form onSubmit={submit} className="flex flex-col gap-5">
            {/* Email */}
            <div>
              <label className="label">Email</label>
              <div className="relative">
                <Mail className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input
                  name="email" type="email" value={form.email} onChange={handle}
                  placeholder="you@example.com" autoComplete="email"
                  className="input-field pl-10"
                />
              </div>
            </div>

            {/* Password */}
            <div>
              <label className="label">Password</label>
              <div className="relative">
                <Lock className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input
                  name="password" type={show ? 'text' : 'password'} value={form.password} onChange={handle}
                  placeholder="••••••••" autoComplete="current-password"
                  className="input-field pl-10 pr-10"
                />
                <button type="button" onClick={() => setShow(!show)}
                  className="absolute right-3.5 top-1/2 -translate-y-1/2 text-slate-500 hover:text-slate-300 transition-colors">
                  {show ? <EyeOff className="w-4 h-4" /> : <Eye className="w-4 h-4" />}
                </button>
              </div>
            </div>

            <button type="submit" disabled={loading} className="btn-primary justify-center py-3 mt-1">
              {loading ? (
                <>
                  <span className="w-4 h-4 rounded-full border-2 border-white border-t-transparent animate-spin" />
                  Signing in…
                </>
              ) : (
                <>Sign In <ArrowRight className="w-4 h-4" /></>
              )}
            </button>
          </form>
        </div>

        <p className="text-center text-sm text-slate-500 mt-6">
          Don't have an account?{' '}
          <Link to="/register" className="text-brand-400 hover:text-brand-300 font-medium transition-colors">
            Create one free
          </Link>
        </p>
      </div>
    </div>
  )
}
```

---

## `client/src/pages/Matches.jsx`

```jsx
import { useState, useEffect } from 'react'
import API from '../utils/api'
import SkillTag from '../components/SkillTag'
import ScoreRing from '../components/ScoreRing'
import { PageSpinner } from '../components/Spinner'
import { Users, Search, RefreshCw, Github, Linkedin, ChevronDown, ChevronUp } from 'lucide-react'
import toast from 'react-hot-toast'

const expColor = {
  beginner: 'bg-emerald-500/15 text-emerald-400 border-emerald-500/25',
  intermediate: 'bg-brand-500/15 text-brand-400 border-brand-500/25',
  advanced: 'bg-accent-500/15 text-accent-400 border-accent-500/25',
  expert: 'bg-amber-500/15 text-amber-400 border-amber-500/25',
}

function MatchCard({ match }) {
  const [expanded, setExpanded] = useState(false)
  const { user, compatibilityScore, commonSkills } = match
  const initials = user.name.split(' ').map(n => n[0]).join('').toUpperCase().slice(0, 2)

  return (
    <div className="card stagger-item flex flex-col gap-4">
      <div className="flex items-start gap-4">
        <div className="w-12 h-12 rounded-xl bg-gradient-to-br from-brand-500 to-accent-500 flex items-center justify-center text-base font-display font-bold text-white shrink-0 shadow-lg">
          {initials}
        </div>
        <div className="flex-1 min-w-0">
          <div className="flex flex-wrap items-center gap-2 mb-0.5">
            <h3 className="font-display font-semibold text-white">{user.name}</h3>
            <span className={`badge border text-xs capitalize ${expColor[user.experienceLevel] || expColor.beginner}`}>
              {user.experienceLevel}
            </span>
          </div>
          <p className="text-slate-500 text-xs">{user.email}</p>
          {user.bio && <p className="text-slate-400 text-sm mt-1.5 line-clamp-2">{user.bio}</p>}
        </div>
        <ScoreRing score={compatibilityScore} size={64} stroke={5} />
      </div>

      {/* Common skills */}
      {commonSkills.length > 0 && (
        <div>
          <p className="text-xs font-display font-semibold text-slate-500 uppercase tracking-wider mb-2">
            Common Skills ({commonSkills.length})
          </p>
          <div className="flex flex-wrap gap-1.5">
            {commonSkills.map(s => <SkillTag key={s} skill={s} highlight />)}
          </div>
        </div>
      )}

      {/* All skills (expandable) */}
      {user.skills.length > 0 && (
        <div>
          <button
            onClick={() => setExpanded(!expanded)}
            className="flex items-center gap-1.5 text-xs text-slate-500 hover:text-slate-300 transition-colors mb-2"
          >
            All skills ({user.skills.length})
            {expanded ? <ChevronUp className="w-3 h-3" /> : <ChevronDown className="w-3 h-3" />}
          </button>
          {expanded && (
            <div className="flex flex-wrap gap-1.5">
              {user.skills.map(s => <SkillTag key={s} skill={s} />)}
            </div>
          )}
        </div>
      )}

      {/* Links */}
      <div className="flex gap-2 pt-1 border-t border-white/5">
        {user.github && (
          <a href={user.github.startsWith('http') ? user.github : `https://github.com/${user.github}`}
            target="_blank" rel="noopener noreferrer"
            className="btn-ghost text-xs px-3 py-1.5 gap-1.5">
            <Github className="w-3.5 h-3.5" /> GitHub
          </a>
        )}
        {user.linkedin && (
          <a href={user.linkedin.startsWith('http') ? user.linkedin : `https://linkedin.com/in/${user.linkedin}`}
            target="_blank" rel="noopener noreferrer"
            className="btn-ghost text-xs px-3 py-1.5 gap-1.5">
            <Linkedin className="w-3.5 h-3.5" /> LinkedIn
          </a>
        )}
      </div>
    </div>
  )
}

export default function Matches() {
  const [matches, setMatches]   = useState([])
  const [loading, setLoading]   = useState(true)
  const [refreshing, setRefreshing] = useState(false)
  const [query, setQuery]       = useState('')
  const [minScore, setMinScore] = useState(0)
  const [userSkills, setUserSkills] = useState([])

  const fetchMatches = async (silent = false) => {
    if (!silent) setLoading(true)
    else setRefreshing(true)
    try {
      const { data } = await API.get('/match')
      setMatches(data.matches || [])
      setUserSkills(data.userSkills || [])
      if (silent) toast.success('Matches refreshed!')
    } catch {
      toast.error('Failed to load matches.')
    } finally {
      setLoading(false)
      setRefreshing(false)
    }
  }

  useEffect(() => { fetchMatches() }, [])

  const filtered = matches.filter(m => {
    const nameMatch = m.user.name.toLowerCase().includes(query.toLowerCase())
    const skillMatch = m.user.skills.some(s => s.toLowerCase().includes(query.toLowerCase()))
    return (nameMatch || skillMatch) && m.compatibilityScore >= minScore
  })

  if (loading) return <PageSpinner />

  return (
    <div className="max-w-6xl mx-auto px-4 sm:px-6 py-10">
      {/* Header */}
      <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-8 animate-fade-in">
        <div>
          <h1 className="font-display font-bold text-3xl text-white flex items-center gap-2">
            <Users className="w-7 h-7 text-brand-400" /> Find Teammates
          </h1>
          <p className="text-slate-400 text-sm mt-1">
            {matches.length} matches found based on your {userSkills.length} skills
          </p>
        </div>
        <button onClick={() => fetchMatches(true)} disabled={refreshing} className="btn-secondary gap-2">
          <RefreshCw className={`w-4 h-4 ${refreshing ? 'animate-spin' : ''}`} />
          Refresh Matches
        </button>
      </div>

      {/* Filters */}
      <div className="card mb-6 flex flex-col sm:flex-row gap-4 animate-slide-up">
        <div className="relative flex-1">
          <Search className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
          <input
            value={query} onChange={e => setQuery(e.target.value)}
            placeholder="Search by name or skill…"
            className="input-field pl-10"
          />
        </div>
        <div className="flex items-center gap-3 sm:w-64">
          <span className="text-xs text-slate-400 shrink-0 font-body">Min score</span>
          <input type="range" min={0} max={100} step={5}
            value={minScore} onChange={e => setMinScore(+e.target.value)}
            className="flex-1 accent-brand-500" />
          <span className="font-mono text-sm text-brand-400 w-10 text-right">{minScore}%</span>
        </div>
      </div>

      {/* Results */}
      {filtered.length === 0 ? (
        <div className="card text-center py-16">
          <Users className="w-16 h-16 mx-auto mb-4 text-slate-700" />
          <h3 className="font-display font-semibold text-slate-400 text-lg mb-1">No matches found</h3>
          <p className="text-slate-600 text-sm">
            {matches.length === 0
              ? 'Add skills to your profile to start matching with teammates.'
              : 'Try adjusting your search filters.'}
          </p>
        </div>
      ) : (
        <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
          {filtered.map(m => <MatchCard key={m.user._id} match={m} />)}
        </div>
      )}
    </div>
  )
}
```

---

## `client/src/pages/Profile.jsx`

```jsx
import { useState } from 'react'
import { useAuth } from '../context/AuthContext'
import API from '../utils/api'
import SkillTag from '../components/SkillTag'
import { User, Mail, BookOpen, Github, Linkedin, Plus, X, Save, ToggleLeft, ToggleRight } from 'lucide-react'
import toast from 'react-hot-toast'

const levels = ['beginner', 'intermediate', 'advanced', 'expert']

const popularSkills = [
  'JavaScript','TypeScript','Python','Java','C++','Go','Rust',
  'React','Vue','Angular','Next.js','Node.js','Express','Django',
  'MongoDB','PostgreSQL','MySQL','Redis','Docker','Kubernetes',
  'AWS','Firebase','GraphQL','REST API','Machine Learning',
  'TensorFlow','PyTorch','Flutter','React Native','Solidity',
]

export default function Profile() {
  const { user, setUser, refreshUser } = useAuth()

  const [form, setForm] = useState({
    name:            user?.name || '',
    bio:             user?.bio || '',
    github:          user?.github || '',
    linkedin:        user?.linkedin || '',
    experienceLevel: user?.experienceLevel || 'beginner',
    skills:          user?.skills || [],
    isAvailable:     user?.isAvailable ?? true,
  })
  const [skillInput, setSkillInput] = useState('')
  const [saving, setSaving]         = useState(false)

  const handle = e => setForm(f => ({ ...f, [e.target.name]: e.target.value }))

  const addSkill = (skill) => {
    const s = skill.trim()
    if (!s) return
    if (form.skills.map(x => x.toLowerCase()).includes(s.toLowerCase())) {
      toast.error(`"${s}" is already in your skills.`)
      return
    }
    setForm(f => ({ ...f, skills: [...f.skills, s] }))
    setSkillInput('')
  }

  const removeSkill = s => setForm(f => ({ ...f, skills: f.skills.filter(x => x !== s) }))

  const handleSkillKey = e => {
    if (['Enter', ',', 'Tab'].includes(e.key)) {
      e.preventDefault()
      addSkill(skillInput)
    }
  }

  const submit = async e => {
    e.preventDefault()
    if (!form.name.trim()) return toast.error('Name cannot be empty.')
    setSaving(true)
    try {
      const { data } = await API.put('/users/update', form)
      // Update local context
      localStorage.setItem('skillsync_user', JSON.stringify(data.user))
      setUser(data.user)
      toast.success('Profile updated successfully!')
    } catch (err) {
      toast.error(err.response?.data?.message || 'Failed to update profile.')
    } finally {
      setSaving(false)
    }
  }

  const unusedPopular = popularSkills.filter(
    s => !form.skills.map(x => x.toLowerCase()).includes(s.toLowerCase())
  )

  const initials = form.name
    ? form.name.split(' ').map(n => n[0]).join('').toUpperCase().slice(0, 2)
    : '?'

  return (
    <div className="max-w-3xl mx-auto px-4 sm:px-6 py-10">
      {/* Header */}
      <div className="flex items-center gap-4 mb-8 animate-fade-in">
        <div className="w-16 h-16 rounded-2xl bg-gradient-to-br from-brand-500 to-accent-500 flex items-center justify-center text-2xl font-display font-bold text-white shadow-xl">
          {initials}
        </div>
        <div>
          <h1 className="font-display font-bold text-3xl text-white">Edit Profile</h1>
          <p className="text-slate-400 text-sm mt-0.5">Update your skills and information</p>
        </div>
      </div>

      <form onSubmit={submit} className="flex flex-col gap-6 animate-slide-up">
        {/* Basic info card */}
        <div className="card">
          <h2 className="font-display font-semibold text-white text-base mb-5 flex items-center gap-2">
            <User className="w-4 h-4 text-brand-400" /> Basic Information
          </h2>

          <div className="grid grid-cols-1 sm:grid-cols-2 gap-5">
            {/* Name */}
            <div>
              <label className="label">Full Name</label>
              <div className="relative">
                <User className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input name="name" value={form.name} onChange={handle}
                  placeholder="Your full name" className="input-field pl-10" />
              </div>
            </div>

            {/* Email (read-only) */}
            <div>
              <label className="label">Email</label>
              <div className="relative">
                <Mail className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input value={user?.email || ''} readOnly
                  className="input-field pl-10 opacity-50 cursor-not-allowed" />
              </div>
            </div>

            {/* GitHub */}
            <div>
              <label className="label">GitHub</label>
              <div className="relative">
                <Github className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input name="github" value={form.github} onChange={handle}
                  placeholder="username or URL" className="input-field pl-10" />
              </div>
            </div>

            {/* LinkedIn */}
            <div>
              <label className="label">LinkedIn</label>
              <div className="relative">
                <Linkedin className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input name="linkedin" value={form.linkedin} onChange={handle}
                  placeholder="username or URL" className="input-field pl-10" />
              </div>
            </div>
          </div>

          {/* Bio */}
          <div className="mt-5">
            <label className="label">Bio</label>
            <div className="relative">
              <BookOpen className="absolute left-3.5 top-3.5 w-4 h-4 text-slate-500" />
              <textarea name="bio" value={form.bio} onChange={handle} rows={3}
                placeholder="Tell teammates about yourself, what you're looking to build, your interests…"
                className="input-field pl-10 resize-none" maxLength={300} />
            </div>
            <p className="text-right text-xs text-slate-600 mt-1">{form.bio.length}/300</p>
          </div>
        </div>

        {/* Experience + Availability */}
        <div className="card">
          <h2 className="font-display font-semibold text-white text-base mb-5">
            Experience & Availability
          </h2>

          <div className="flex flex-col sm:flex-row gap-6">
            {/* Level */}
            <div className="flex-1">
              <label className="label">Experience Level</label>
              <div className="grid grid-cols-2 sm:grid-cols-4 gap-2">
                {levels.map(lvl => (
                  <button key={lvl} type="button"
                    onClick={() => setForm(f => ({ ...f, experienceLevel: lvl }))}
                    className={`py-2.5 rounded-xl text-xs font-display font-semibold capitalize border transition-all ${
                      form.experienceLevel === lvl
                        ? 'bg-brand-600/20 border-brand-500/50 text-brand-300 shadow-sm shadow-brand-900/20'
                        : 'bg-surface-700/50 border-white/10 text-slate-400 hover:border-white/20'
                    }`}
                  >{lvl}</button>
                ))}
              </div>
            </div>

            {/* Available toggle */}
            <div className="sm:w-48">
              <label className="label">Open to Team Up</label>
              <button
                type="button"
                onClick={() => setForm(f => ({ ...f, isAvailable: !f.isAvailable }))}
                className={`w-full flex items-center justify-between px-4 py-3 rounded-xl border transition-all ${
                  form.isAvailable
                    ? 'bg-emerald-500/10 border-emerald-500/30 text-emerald-400'
                    : 'bg-surface-700/50 border-white/10 text-slate-500'
                }`}
              >
                <span className="text-sm font-body">{form.isAvailable ? 'Available' : 'Unavailable'}</span>
                {form.isAvailable
                  ? <ToggleRight className="w-5 h-5" />
                  : <ToggleLeft  className="w-5 h-5" />
                }
              </button>
            </div>
          </div>
        </div>

        {/* Skills card */}
        <div className="card">
          <h2 className="font-display font-semibold text-white text-base mb-5">
            Skills ({form.skills.length})
          </h2>

          {/* Input row */}
          <div className="flex gap-2 mb-4">
            <input
              value={skillInput}
              onChange={e => setSkillInput(e.target.value)}
              onKeyDown={handleSkillKey}
              placeholder="Type a skill and press Enter or comma…"
              className="input-field flex-1"
            />
            <button type="button" onClick={() => addSkill(skillInput)}
              className="btn-secondary px-3.5 shrink-0">
              <Plus className="w-4 h-4" />
            </button>
          </div>

          {/* Added skills */}
          {form.skills.length > 0 ? (
            <div className="flex flex-wrap gap-2 mb-5">
              {form.skills.map(s => (
                <span key={s}
                  className="inline-flex items-center gap-1.5 px-3 py-1.5 rounded-xl bg-brand-600/15 border border-brand-500/30 text-brand-300 text-xs font-mono group">
                  {s}
                  <button type="button" onClick={() => removeSkill(s)}
                    className="text-brand-500 hover:text-red-400 transition-colors ml-0.5">
                    <X className="w-3 h-3" />
                  </button>
                </span>
              ))}
            </div>
          ) : (
            <p className="text-slate-600 text-sm italic mb-4">No skills added yet</p>
          )}

          {/* Quick-add popular */}
          <div>
            <p className="text-xs font-display font-semibold text-slate-500 uppercase tracking-wider mb-3">
              Quick Add
            </p>
            <div className="flex flex-wrap gap-2">
              {unusedPopular.slice(0, 16).map(s => (
                <button key={s} type="button" onClick={() => addSkill(s)}
                  className="px-3 py-1.5 rounded-lg bg-surface-600/50 border border-white/8 text-slate-400 hover:text-brand-400 hover:border-brand-500/30 text-xs font-mono transition-all hover:-translate-y-0.5">
                  + {s}
                </button>
              ))}
            </div>
          </div>
        </div>

        {/* Save button */}
        <button type="submit" disabled={saving} className="btn-primary justify-center py-3.5 text-base">
          {saving ? (
            <>
              <span className="w-4 h-4 rounded-full border-2 border-white border-t-transparent animate-spin" />
              Saving…
            </>
          ) : (
            <>
              <Save className="w-4 h-4" /> Update Profile
            </>
          )}
        </button>
      </form>
    </div>
  )
}
```

---

## `client/src/pages/Projects.jsx`

```jsx
import { useState, useEffect } from 'react'
import API from '../utils/api'
import { PageSpinner } from '../components/Spinner'
import SkillTag from '../components/SkillTag'
import { FolderGit2, RefreshCw, Search, Clock, BarChart3, Layers } from 'lucide-react'
import toast from 'react-hot-toast'

const difficultyConfig = {
  beginner:     { label: 'Beginner',     cls: 'bg-emerald-500/15 text-emerald-400 border-emerald-500/25' },
  intermediate: { label: 'Intermediate', cls: 'bg-brand-500/15 text-brand-400 border-brand-500/25' },
  advanced:     { label: 'Advanced',     cls: 'bg-red-500/15 text-red-400 border-red-500/25' },
}

function ProjectCard({ project }) {
  const diff = difficultyConfig[project.difficulty] || difficultyConfig.beginner

  return (
    <div className="card flex flex-col gap-4 stagger-item hover:border-brand-500/20 transition-all duration-200">
      {/* Header */}
      <div className="flex items-start justify-between gap-3">
        <div className="w-10 h-10 rounded-xl bg-surface-600/60 flex items-center justify-center shrink-0">
          <FolderGit2 className="w-5 h-5 text-brand-400" />
        </div>
        <span className={`badge border text-xs capitalize ${diff.cls}`}>{diff.label}</span>
      </div>

      {/* Title + desc */}
      <div>
        <h3 className="font-display font-semibold text-white text-base leading-snug mb-1.5">
          {project.title}
        </h3>
        <p className="text-slate-400 text-sm leading-relaxed">{project.description}</p>
      </div>

      {/* Match score bar */}
      {project.matchScore > 0 && (
        <div>
          <div className="flex items-center justify-between mb-1.5">
            <span className="text-xs text-slate-500 font-body">Skill match</span>
            <span className="text-xs font-mono text-brand-400">{project.matchScore}%</span>
          </div>
          <div className="h-1.5 rounded-full bg-surface-600">
            <div
              className="h-full rounded-full bg-gradient-to-r from-brand-600 to-brand-400 transition-all duration-700"
              style={{ width: `${project.matchScore}%` }}
            />
          </div>
        </div>
      )}

      {/* Meta */}
      <div className="flex flex-wrap gap-3 text-xs text-slate-500">
        <span className="flex items-center gap-1.5">
          <Clock className="w-3.5 h-3.5" /> {project.estimatedDuration}
        </span>
        <span className="flex items-center gap-1.5">
          <Layers className="w-3.5 h-3.5" /> {project.category}
        </span>
      </div>

      {/* Tech stack */}
      <div>
        <p className="text-xs font-display font-semibold text-slate-500 uppercase tracking-wider mb-2">
          Tech Stack
        </p>
        <div className="flex flex-wrap gap-1.5">
          {project.techStack.map(t => (
            <span key={t} className="badge bg-surface-600/60 text-slate-400 border border-white/8 font-mono">
              {t}
            </span>
          ))}
        </div>
      </div>

      {/* Required skills */}
      <div className="pt-2 border-t border-white/5">
        <p className="text-xs font-display font-semibold text-slate-500 uppercase tracking-wider mb-2">
          Required Skills
        </p>
        <div className="flex flex-wrap gap-1.5">
          {project.requiredSkills.map(s => <SkillTag key={s} skill={s} />)}
        </div>
      </div>
    </div>
  )
}

export default function Projects() {
  const [projects, setProjects]   = useState([])
  const [loading, setLoading]     = useState(true)
  const [refreshing, setRefreshing] = useState(false)
  const [query, setQuery]         = useState('')
  const [diffFilter, setDiffFilter] = useState('all')
  const [userSkills, setUserSkills] = useState([])

  const fetchProjects = async (silent = false) => {
    if (!silent) setLoading(true)
    else setRefreshing(true)
    try {
      const { data } = await API.get('/projects')
      setProjects(data.projects || [])
      setUserSkills(data.userSkills || [])
      if (silent) toast.success('Projects refreshed!')
    } catch {
      toast.error('Failed to load projects.')
    } finally {
      setLoading(false)
      setRefreshing(false)
    }
  }

  useEffect(() => { fetchProjects() }, [])

  const filtered = projects.filter(p => {
    const matchesQuery =
      p.title.toLowerCase().includes(query.toLowerCase()) ||
      p.techStack.some(t => t.toLowerCase().includes(query.toLowerCase())) ||
      p.category.toLowerCase().includes(query.toLowerCase())
    const matchesDiff = diffFilter === 'all' || p.difficulty === diffFilter
    return matchesQuery && matchesDiff
  })

  if (loading) return <PageSpinner />

  return (
    <div className="max-w-6xl mx-auto px-4 sm:px-6 py-10">
      {/* Header */}
      <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-8 animate-fade-in">
        <div>
          <h1 className="font-display font-bold text-3xl text-white flex items-center gap-2">
            <FolderGit2 className="w-7 h-7 text-emerald-400" /> Project Ideas
          </h1>
          <p className="text-slate-400 text-sm mt-1">
            {userSkills.length > 0
              ? `Personalized for your ${userSkills.length} skills — sorted by match score`
              : 'Add skills to your profile for personalized suggestions'}
          </p>
        </div>
        <button onClick={() => fetchProjects(true)} disabled={refreshing} className="btn-secondary gap-2">
          <RefreshCw className={`w-4 h-4 ${refreshing ? 'animate-spin' : ''}`} />
          Get Project Ideas
        </button>
      </div>

      {/* Filters */}
      <div className="card mb-6 flex flex-col sm:flex-row gap-4 animate-slide-up">
        <div className="relative flex-1">
          <Search className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
          <input
            value={query} onChange={e => setQuery(e.target.value)}
            placeholder="Search by title, tech, or category…"
            className="input-field pl-10"
          />
        </div>
        <div className="flex gap-2">
          {['all', 'beginner', 'intermediate', 'advanced'].map(d => (
            <button
              key={d}
              onClick={() => setDiffFilter(d)}
              className={`px-3.5 py-2 rounded-xl text-xs font-display font-semibold capitalize border transition-all ${
                diffFilter === d
                  ? 'bg-brand-600/20 border-brand-500/40 text-brand-300'
                  : 'bg-surface-700/50 border-white/10 text-slate-400 hover:border-white/20'
              }`}
            >
              {d === 'all' ? 'All' : d}
            </button>
          ))}
        </div>
      </div>

      {/* Your skills banner */}
      {userSkills.length > 0 && (
        <div className="flex flex-wrap items-center gap-2 mb-6 animate-slide-up">
          <span className="text-xs text-slate-500 font-body">Your skills:</span>
          {userSkills.map(s => <SkillTag key={s} skill={s} />)}
        </div>
      )}

      {/* Grid */}
      {filtered.length === 0 ? (
        <div className="card text-center py-16">
          <FolderGit2 className="w-16 h-16 mx-auto mb-4 text-slate-700" />
          <h3 className="font-display font-semibold text-slate-400 text-lg mb-1">No projects found</h3>
          <p className="text-slate-600 text-sm">Try a different search or difficulty filter.</p>
        </div>
      ) : (
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
          {filtered.map(p => <ProjectCard key={p.title} project={p} />)}
        </div>
      )}
    </div>
  )
}
```

---

## `client/src/pages/Register.jsx`

```jsx
import { useState } from 'react'
import { Link, useNavigate } from 'react-router-dom'
import { useAuth } from '../context/AuthContext'
import { Zap, User, Mail, Lock, Eye, EyeOff, Plus, X, ArrowRight } from 'lucide-react'
import toast from 'react-hot-toast'

const levels = ['beginner', 'intermediate', 'advanced', 'expert']

const popularSkills = [
  'JavaScript', 'Python', 'React', 'Node.js', 'TypeScript', 'Java',
  'CSS', 'MongoDB', 'SQL', 'Docker', 'Machine Learning', 'Flutter'
]

export default function Register() {
  const { register } = useAuth()
  const navigate = useNavigate()

  const [form, setForm] = useState({
    name: '', email: '', password: '',
    experienceLevel: 'beginner', skills: []
  })
  const [skillInput, setSkillInput] = useState('')
  const [show, setShow]   = useState(false)
  const [loading, setLoading] = useState(false)

  const handle = (e) => setForm(f => ({ ...f, [e.target.name]: e.target.value }))

  const addSkill = (skill) => {
    const s = skill.trim()
    if (!s) return
    if (form.skills.map(x => x.toLowerCase()).includes(s.toLowerCase())) return
    setForm(f => ({ ...f, skills: [...f.skills, s] }))
    setSkillInput('')
  }

  const removeSkill = (s) => setForm(f => ({ ...f, skills: f.skills.filter(x => x !== s) }))

  const handleSkillKey = (e) => {
    if (['Enter', ',', 'Tab'].includes(e.key)) {
      e.preventDefault()
      addSkill(skillInput)
    }
  }

  const submit = async (e) => {
    e.preventDefault()
    if (!form.name || !form.email || !form.password)
      return toast.error('Please fill in all required fields.')
    if (form.password.length < 6)
      return toast.error('Password must be at least 6 characters.')
    setLoading(true)
    try {
      await register(form)
      navigate('/dashboard')
    } catch (err) {
      toast.error(err.response?.data?.message || 'Registration failed.')
    } finally {
      setLoading(false)
    }
  }

  return (
    <div className="min-h-[calc(100vh-4rem)] flex items-center justify-center px-4 py-16">
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        <div className="absolute top-1/3 left-1/2 -translate-x-1/2 w-[600px] h-[600px] bg-accent-600/6 rounded-full blur-[120px]" />
      </div>

      <div className="relative w-full max-w-lg animate-slide-up">
        <div className="text-center mb-8">
          <div className="inline-flex w-12 h-12 items-center justify-center rounded-xl bg-brand-600 shadow-lg shadow-brand-900/50 mb-4">
            <Zap className="w-6 h-6 text-white" strokeWidth={2.5} />
          </div>
          <h1 className="font-display font-bold text-3xl text-white">Join SkillSync</h1>
          <p className="text-slate-400 mt-1 text-sm">Create your profile and start matching</p>
        </div>

        <div className="card">
          <form onSubmit={submit} className="flex flex-col gap-5">
            {/* Name */}
            <div>
              <label className="label">Full Name</label>
              <div className="relative">
                <User className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input name="name" value={form.name} onChange={handle}
                  placeholder="Ada Lovelace" className="input-field pl-10" />
              </div>
            </div>

            {/* Email */}
            <div>
              <label className="label">Email</label>
              <div className="relative">
                <Mail className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input name="email" type="email" value={form.email} onChange={handle}
                  placeholder="you@example.com" className="input-field pl-10" />
              </div>
            </div>

            {/* Password */}
            <div>
              <label className="label">Password</label>
              <div className="relative">
                <Lock className="absolute left-3.5 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
                <input name="password" type={show ? 'text' : 'password'} value={form.password} onChange={handle}
                  placeholder="Min. 6 characters" className="input-field pl-10 pr-10" />
                <button type="button" onClick={() => setShow(!show)}
                  className="absolute right-3.5 top-1/2 -translate-y-1/2 text-slate-500 hover:text-slate-300 transition-colors">
                  {show ? <EyeOff className="w-4 h-4" /> : <Eye className="w-4 h-4" />}
                </button>
              </div>
            </div>

            {/* Experience */}
            <div>
              <label className="label">Experience Level</label>
              <div className="grid grid-cols-4 gap-2">
                {levels.map(lvl => (
                  <button key={lvl} type="button"
                    onClick={() => setForm(f => ({ ...f, experienceLevel: lvl }))}
                    className={`py-2 rounded-xl text-xs font-display font-semibold capitalize border transition-all ${
                      form.experienceLevel === lvl
                        ? 'bg-brand-600/20 border-brand-500/50 text-brand-300'
                        : 'bg-surface-700/50 border-white/10 text-slate-400 hover:border-white/20'
                    }`}
                  >{lvl}</button>
                ))}
              </div>
            </div>

            {/* Skills */}
            <div>
              <label className="label">Skills</label>
              <div className="flex gap-2 mb-2">
                <input
                  value={skillInput}
                  onChange={e => setSkillInput(e.target.value)}
                  onKeyDown={handleSkillKey}
                  placeholder="Type a skill + Enter"
                  className="input-field flex-1"
                />
                <button type="button" onClick={() => addSkill(skillInput)}
                  className="btn-secondary px-3 shrink-0">
                  <Plus className="w-4 h-4" />
                </button>
              </div>

              {/* Quick-add chips */}
              <div className="flex flex-wrap gap-1.5 mb-3">
                {popularSkills.filter(s => !form.skills.map(x => x.toLowerCase()).includes(s.toLowerCase())).slice(0, 8).map(s => (
                  <button key={s} type="button" onClick={() => addSkill(s)}
                    className="px-2.5 py-1 rounded-lg bg-surface-600/50 border border-white/8 text-slate-400 hover:text-brand-400 hover:border-brand-500/30 text-xs font-mono transition-all">
                    + {s}
                  </button>
                ))}
              </div>

              {/* Added skills */}
              {form.skills.length > 0 && (
                <div className="flex flex-wrap gap-1.5">
                  {form.skills.map(s => (
                    <span key={s} className="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-lg bg-brand-600/15 border border-brand-500/30 text-brand-300 text-xs font-mono">
                      {s}
                      <button type="button" onClick={() => removeSkill(s)}
                        className="hover:text-red-400 transition-colors">
                        <X className="w-3 h-3" />
                      </button>
                    </span>
                  ))}
                </div>
              )}
            </div>

            <button type="submit" disabled={loading} className="btn-primary justify-center py-3 mt-1">
              {loading ? (
                <>
                  <span className="w-4 h-4 rounded-full border-2 border-white border-t-transparent animate-spin" />
                  Creating account…
                </>
              ) : (
                <>Create Account <ArrowRight className="w-4 h-4" /></>
              )}
            </button>
          </form>
        </div>

        <p className="text-center text-sm text-slate-500 mt-6">
          Already have an account?{' '}
          <Link to="/login" className="text-brand-400 hover:text-brand-300 font-medium transition-colors">
            Sign in
          </Link>
        </p>
      </div>
    </div>
  )
}
```

---

## `client/src/utils/api.js`

```javascript
import axios from 'axios'

const API = axios.create({
  baseURL: import.meta.env.VITE_API_URL || '/api',
  headers: { 'Content-Type': 'application/json' },
})

// Attach JWT to every request
API.interceptors.request.use(config => {
  const token = localStorage.getItem('skillsync_token')
  if (token) config.headers.Authorization = `Bearer ${token}`
  return config
})

// Global response error handler
API.interceptors.response.use(
  res => res,
  err => {
    if (err.response?.status === 401) {
      localStorage.removeItem('skillsync_token')
      localStorage.removeItem('skillsync_user')
      window.location.href = '/login'
    }
    return Promise.reject(err)
  }
)

export default API
```

---

## `client/tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,jsx}'],
  theme: {
    extend: {
      fontFamily: {
        display: ['Syne', 'sans-serif'],
        body: ['DM Sans', 'sans-serif'],
        mono: ['JetBrains Mono', 'monospace'],
      },
      colors: {
        brand: {
          50:  '#eef9ff',
          100: '#d8f1ff',
          200: '#b9e7ff',
          300: '#89d9ff',
          400: '#52c2ff',
          500: '#2aa3ff',
          600: '#0e83f5',
          700: '#0a6ae0',
          800: '#0f55b5',
          900: '#12498e',
          950: '#0e2d57',
        },
        accent: {
          400: '#a78bfa',
          500: '#8b5cf6',
          600: '#7c3aed',
        },
        surface: {
          900: '#080c14',
          800: '#0d1220',
          700: '#111827',
          600: '#1a2235',
          500: '#1f2a42',
          400: '#243050',
        }
      },
      backgroundImage: {
        'grid-pattern': "url(\"data:image/svg+xml,%3Csvg width='40' height='40' viewBox='0 0 40 40' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%230e83f5' fill-opacity='0.04'%3E%3Cpath d='M0 40L40 0H20L0 20M40 40V20L20 40'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E\")",
      },
      animation: {
        'fade-in': 'fadeIn 0.5s ease forwards',
        'slide-up': 'slideUp 0.4s ease forwards',
        'pulse-slow': 'pulse 3s ease-in-out infinite',
        'spin-slow': 'spin 8s linear infinite',
      },
      keyframes: {
        fadeIn: { from: { opacity: 0 }, to: { opacity: 1 } },
        slideUp: { from: { opacity: 0, transform: 'translateY(20px)' }, to: { opacity: 1, transform: 'translateY(0)' } },
      }
    },
  },
  plugins: [],
}
```

---

## `client/vite.config.js`

```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  server: {
    port: 5173,
    proxy: {
      '/api': {
        target: 'http://localhost:5000',
        changeOrigin: true,
        secure: false,
      }
    }
  }
})
```

---

## `package.json`

```json
{
  "name": "skillsync",
  "version": "1.0.0",
  "description": "AI Team Formation System",
  "scripts": {
    "dev": "concurrently \"npm run server\" \"npm run client\"",
    "server": "cd server && npm run dev",
    "client": "cd client && npm run dev",
    "build": "cd client && npm run build",
    "install:all": "npm install && cd server && npm install && cd ../client && npm install"
  },
  "devDependencies": {
    "concurrently": "^8.2.2"
  }
}
```

---

## `server/.env`

```
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/skillsync?retryWrites=true&w=majority
JWT_SECRET=skillsync_super_secret_jwt_key_change_in_production
JWT_EXPIRE=7d
NODE_ENV=development
CLIENT_URL=http://localhost:5173
```

---

## `server/config/db.js`

```javascript
const mongoose = require('mongoose');

const connectDB = async () => {
  try {
    const conn = await mongoose.connect(process.env.MONGO_URI, {
      useNewUrlParser: true,
      useUnifiedTopology: true,
    });
    console.log(`✅ MongoDB Connected: ${conn.connection.host}`);
  } catch (error) {
    console.error(`❌ MongoDB Connection Error: ${error.message}`);
    process.exit(1);
  }
};

module.exports = connectDB;
```

---

## `server/controllers/authController.js`

```javascript
const jwt = require('jsonwebtoken');
const User = require('../models/User');

// Generate JWT token
const generateToken = (id) => {
  return jwt.sign({ id }, process.env.JWT_SECRET, {
    expiresIn: process.env.JWT_EXPIRE || '7d'
  });
};

// @desc    Register user
// @route   POST /api/auth/register
// @access  Public
const register = async (req, res) => {
  try {
    const { name, email, password, skills, experienceLevel } = req.body;

    if (!name || !email || !password) {
      return res.status(400).json({
        success: false,
        message: 'Please provide name, email, and password.'
      });
    }

    const existingUser = await User.findOne({ email });
    if (existingUser) {
      return res.status(409).json({
        success: false,
        message: 'An account with this email already exists.'
      });
    }

    const user = await User.create({
      name,
      email,
      password,
      skills: skills || [],
      experienceLevel: experienceLevel || 'beginner'
    });

    const token = generateToken(user._id);

    res.status(201).json({
      success: true,
      message: 'Account created successfully!',
      token,
      user: {
        _id: user._id,
        name: user.name,
        email: user.email,
        skills: user.skills,
        experienceLevel: user.experienceLevel,
        bio: user.bio,
        github: user.github,
        linkedin: user.linkedin,
        isAvailable: user.isAvailable,
        createdAt: user.createdAt
      }
    });
  } catch (error) {
    console.error('Register error:', error);
    if (error.name === 'ValidationError') {
      const messages = Object.values(error.errors).map(e => e.message);
      return res.status(400).json({ success: false, message: messages[0] });
    }
    res.status(500).json({ success: false, message: 'Server error during registration.' });
  }
};

// @desc    Login user
// @route   POST /api/auth/login
// @access  Public
const login = async (req, res) => {
  try {
    const { email, password } = req.body;

    if (!email || !password) {
      return res.status(400).json({
        success: false,
        message: 'Please provide email and password.'
      });
    }

    const user = await User.findOne({ email }).select('+password');
    if (!user) {
      return res.status(401).json({
        success: false,
        message: 'Invalid email or password.'
      });
    }

    const isMatch = await user.comparePassword(password);
    if (!isMatch) {
      return res.status(401).json({
        success: false,
        message: 'Invalid email or password.'
      });
    }

    const token = generateToken(user._id);

    res.json({
      success: true,
      message: 'Login successful!',
      token,
      user: {
        _id: user._id,
        name: user.name,
        email: user.email,
        skills: user.skills,
        experienceLevel: user.experienceLevel,
        bio: user.bio,
        github: user.github,
        linkedin: user.linkedin,
        isAvailable: user.isAvailable,
        createdAt: user.createdAt
      }
    });
  } catch (error) {
    console.error('Login error:', error);
    res.status(500).json({ success: false, message: 'Server error during login.' });
  }
};

// @desc    Get current logged-in user
// @route   GET /api/auth/me
// @access  Private
const getMe = async (req, res) => {
  try {
    const user = await User.findById(req.user._id);
    res.json({ success: true, user });
  } catch (error) {
    res.status(500).json({ success: false, message: 'Server error.' });
  }
};

module.exports = { register, login, getMe };
```

---

## `server/controllers/matchController.js`

```javascript
const User = require('../models/User');
const Match = require('../models/Match');

// Core matching algorithm
const calculateCompatibility = (skillsA, skillsB) => {
  const setA = new Set(skillsA.map(s => s.toLowerCase().trim()));
  const setB = new Set(skillsB.map(s => s.toLowerCase().trim()));

  const commonSkills = [...setA].filter(skill => setB.has(skill));
  const totalUniqueSkills = new Set([...setA, ...setB]).size;

  if (totalUniqueSkills === 0) return { score: 0, commonSkills: [] };

  const score = Math.round((commonSkills.length / totalUniqueSkills) * 100);
  return { score, commonSkills };
};

// Experience level bonus scoring
const experienceLevelScore = (levelA, levelB) => {
  const levels = { beginner: 1, intermediate: 2, advanced: 3, expert: 4 };
  const diff = Math.abs((levels[levelA] || 1) - (levels[levelB] || 1));
  if (diff === 0) return 10;
  if (diff === 1) return 7;
  if (diff === 2) return 3;
  return 0;
};

// @desc    Get all matches for current user
// @route   GET /api/match
// @access  Private
const getMatches = async (req, res) => {
  try {
    const currentUser = await User.findById(req.user._id);

    if (!currentUser.skills || currentUser.skills.length === 0) {
      return res.json({
        success: true,
        message: 'Add skills to your profile to find matches.',
        matches: []
      });
    }

    // Get all other available users
    const allUsers = await User.find({
      _id: { $ne: currentUser._id },
      isAvailable: true
    });

    // Calculate compatibility for each user
    const matchResults = allUsers
      .map(user => {
        const { score, commonSkills } = calculateCompatibility(
          currentUser.skills,
          user.skills
        );
        const expBonus = experienceLevelScore(
          currentUser.experienceLevel,
          user.experienceLevel
        );
        const finalScore = Math.min(100, score + Math.round(expBonus * 0.2));

        return {
          user: {
            _id: user._id,
            name: user.name,
            email: user.email,
            skills: user.skills,
            experienceLevel: user.experienceLevel,
            bio: user.bio,
            github: user.github,
            linkedin: user.linkedin
          },
          compatibilityScore: finalScore,
          commonSkills,
          skillCount: user.skills.length
        };
      })
      .filter(m => m.compatibilityScore > 0)
      .sort((a, b) => b.compatibilityScore - a.compatibilityScore)
      .slice(0, 20);

    // Persist top matches to DB (upsert)
    for (const match of matchResults.slice(0, 10)) {
      await Match.findOneAndUpdate(
        { userId: currentUser._id, matchedUserId: match.user._id },
        {
          userId: currentUser._id,
          matchedUserId: match.user._id,
          compatibilityScore: match.compatibilityScore,
          commonSkills: match.commonSkills
        },
        { upsert: true, new: true }
      );
    }

    res.json({
      success: true,
      count: matchResults.length,
      matches: matchResults,
      userSkills: currentUser.skills
    });
  } catch (error) {
    console.error('Match error:', error);
    res.status(500).json({ success: false, message: 'Error computing matches.' });
  }
};

// @desc    Get a specific user's match details
// @route   GET /api/match/:id
// @access  Private
const getMatchById = async (req, res) => {
  try {
    const currentUser = await User.findById(req.user._id);
    const targetUser = await User.findById(req.params.id);

    if (!targetUser) {
      return res.status(404).json({ success: false, message: 'User not found.' });
    }

    const { score, commonSkills } = calculateCompatibility(
      currentUser.skills,
      targetUser.skills
    );

    res.json({
      success: true,
      match: {
        user: targetUser,
        compatibilityScore: score,
        commonSkills
      }
    });
  } catch (error) {
    res.status(500).json({ success: false, message: 'Server error.' });
  }
};

module.exports = { getMatches, getMatchById };
```

---

## `server/controllers/projectController.js`

```javascript
const User = require('../models/User');

// Project database - comprehensive list
const projectDatabase = [
  // Web Development
  {
    title: 'AI-Powered Portfolio Generator',
    description: 'Build a platform that auto-generates stunning portfolios from GitHub profiles using AI.',
    requiredSkills: ['react', 'node.js', 'openai', 'css', 'javascript'],
    difficulty: 'intermediate',
    techStack: ['React', 'Node.js', 'OpenAI API', 'MongoDB', 'Tailwind CSS'],
    estimatedDuration: '3-4 weeks',
    category: 'Web Development'
  },
  {
    title: 'Real-Time Collaborative Code Editor',
    description: 'Multi-user code editor with syntax highlighting, video chat, and execution.',
    requiredSkills: ['react', 'node.js', 'websocket', 'javascript'],
    difficulty: 'advanced',
    techStack: ['React', 'Node.js', 'Socket.io', 'Monaco Editor', 'WebRTC'],
    estimatedDuration: '4-6 weeks',
    category: 'Web Development'
  },
  {
    title: 'E-Commerce Platform with Smart Recommendations',
    description: 'Full-stack store with AI-based product recommendations and payment integration.',
    requiredSkills: ['react', 'node.js', 'mongodb', 'javascript', 'css'],
    difficulty: 'advanced',
    techStack: ['React', 'Node.js', 'MongoDB', 'Stripe', 'Redis'],
    estimatedDuration: '5-7 weeks',
    category: 'E-Commerce'
  },
  // Mobile
  {
    title: 'Health & Fitness Tracker App',
    description: 'Cross-platform mobile app to track workouts, nutrition, and health metrics.',
    requiredSkills: ['react native', 'javascript', 'firebase'],
    difficulty: 'intermediate',
    techStack: ['React Native', 'Firebase', 'Expo', 'Charts.js'],
    estimatedDuration: '3-5 weeks',
    category: 'Mobile'
  },
  // AI/ML
  {
    title: 'Sentiment Analysis Dashboard',
    description: 'Real-time Twitter/social media sentiment analyzer with visualizations.',
    requiredSkills: ['python', 'machine learning', 'react', 'nlp'],
    difficulty: 'advanced',
    techStack: ['Python', 'FastAPI', 'React', 'Scikit-learn', 'D3.js'],
    estimatedDuration: '4-5 weeks',
    category: 'AI/ML'
  },
  {
    title: 'Image Classification Web App',
    description: 'Upload images and classify them using a trained deep learning model.',
    requiredSkills: ['python', 'tensorflow', 'flask', 'react'],
    difficulty: 'intermediate',
    techStack: ['Python', 'TensorFlow', 'Flask', 'React', 'Docker'],
    estimatedDuration: '3-4 weeks',
    category: 'AI/ML'
  },
  {
    title: 'Chatbot Builder Platform',
    description: 'No-code platform to build custom AI chatbots and embed them on websites.',
    requiredSkills: ['python', 'node.js', 'react', 'nlp', 'openai'],
    difficulty: 'advanced',
    techStack: ['Python', 'Node.js', 'React', 'OpenAI', 'PostgreSQL'],
    estimatedDuration: '5-6 weeks',
    category: 'AI/ML'
  },
  // Data
  {
    title: 'Stock Market Analytics Dashboard',
    description: 'Visualize stock data, trends, and get AI-powered predictions.',
    requiredSkills: ['python', 'react', 'data analysis', 'javascript'],
    difficulty: 'intermediate',
    techStack: ['Python', 'React', 'Pandas', 'Plotly', 'FastAPI'],
    estimatedDuration: '3-4 weeks',
    category: 'Data Analytics'
  },
  {
    title: 'COVID-19 Data Visualization Tool',
    description: 'Interactive global dashboard for COVID data with forecasting.',
    requiredSkills: ['python', 'data analysis', 'react', 'visualization'],
    difficulty: 'beginner',
    techStack: ['Python', 'React', 'D3.js', 'Pandas', 'Flask'],
    estimatedDuration: '2-3 weeks',
    category: 'Data Analytics'
  },
  // DevOps
  {
    title: 'CI/CD Pipeline Monitor',
    description: 'Visual dashboard to monitor GitHub Actions, deployments, and system health.',
    requiredSkills: ['docker', 'kubernetes', 'node.js', 'react', 'devops'],
    difficulty: 'advanced',
    techStack: ['Node.js', 'React', 'Docker', 'Kubernetes', 'Prometheus'],
    estimatedDuration: '4-6 weeks',
    category: 'DevOps'
  },
  // Blockchain
  {
    title: 'NFT Marketplace',
    description: 'Mint, buy, and sell NFTs on a custom marketplace with wallet integration.',
    requiredSkills: ['solidity', 'javascript', 'react', 'web3', 'blockchain'],
    difficulty: 'advanced',
    techStack: ['Solidity', 'React', 'Ethers.js', 'IPFS', 'Hardhat'],
    estimatedDuration: '5-8 weeks',
    category: 'Blockchain'
  },
  {
    title: 'Decentralized Voting System',
    description: 'Tamper-proof voting platform built on Ethereum smart contracts.',
    requiredSkills: ['solidity', 'web3', 'react', 'blockchain'],
    difficulty: 'intermediate',
    techStack: ['Solidity', 'React', 'Web3.js', 'Ganache', 'Truffle'],
    estimatedDuration: '3-5 weeks',
    category: 'Blockchain'
  },
  // Beginner friendly
  {
    title: 'Task Management App',
    description: 'A Kanban-style task manager with drag & drop and team collaboration.',
    requiredSkills: ['react', 'css', 'javascript', 'node.js'],
    difficulty: 'beginner',
    techStack: ['React', 'Node.js', 'MongoDB', 'Tailwind CSS'],
    estimatedDuration: '2-3 weeks',
    category: 'Productivity'
  },
  {
    title: 'Recipe Finder & Meal Planner',
    description: 'Search recipes by ingredients and auto-generate weekly meal plans.',
    requiredSkills: ['react', 'javascript', 'api', 'css'],
    difficulty: 'beginner',
    techStack: ['React', 'Spoonacular API', 'CSS', 'LocalStorage'],
    estimatedDuration: '1-2 weeks',
    category: 'Lifestyle'
  },
  {
    title: 'Personal Finance Tracker',
    description: 'Track income, expenses, and investments with beautiful charts.',
    requiredSkills: ['react', 'javascript', 'css', 'charts'],
    difficulty: 'beginner',
    techStack: ['React', 'Chart.js', 'Node.js', 'MongoDB'],
    estimatedDuration: '2-3 weeks',
    category: 'Finance'
  },
  // Java
  {
    title: 'Library Management System',
    description: 'Full-featured system for managing books, members, and rentals.',
    requiredSkills: ['java', 'spring boot', 'mysql', 'react'],
    difficulty: 'intermediate',
    techStack: ['Java', 'Spring Boot', 'MySQL', 'React', 'Hibernate'],
    estimatedDuration: '3-4 weeks',
    category: 'Enterprise'
  }
];

// Smart scoring: how well does a project match combined skills
const scoreProject = (project, userSkills) => {
  const normalizedSkills = userSkills.map(s => s.toLowerCase().trim());
  const requiredSkillsNorm = project.requiredSkills.map(s => s.toLowerCase());

  let matchCount = 0;
  for (const skill of normalizedSkills) {
    for (const req of requiredSkillsNorm) {
      if (req.includes(skill) || skill.includes(req)) {
        matchCount++;
        break;
      }
    }
  }

  const coverage = requiredSkillsNorm.length > 0
    ? (matchCount / requiredSkillsNorm.length) * 100
    : 0;

  return Math.round(coverage);
};

// @desc    Get project suggestions based on user's skills
// @route   GET /api/projects
// @access  Private
const getProjectSuggestions = async (req, res) => {
  try {
    const user = await User.findById(req.user._id);
    const userSkills = user.skills || [];

    if (userSkills.length === 0) {
      // Return all projects sorted by difficulty
      const sorted = [...projectDatabase].sort((a, b) => {
        const order = { beginner: 0, intermediate: 1, advanced: 2 };
        return order[a.difficulty] - order[b.difficulty];
      });
      return res.json({
        success: true,
        message: 'Add skills to get personalized suggestions!',
        projects: sorted.slice(0, 8).map(p => ({ ...p, matchScore: 0 }))
      });
    }

    // Score all projects
    const scored = projectDatabase
      .map(project => ({
        ...project,
        matchScore: scoreProject(project, userSkills)
      }))
      .sort((a, b) => b.matchScore - a.matchScore);

    // Return top 8 matches
    res.json({
      success: true,
      count: scored.length,
      projects: scored.slice(0, 8),
      userSkills
    });
  } catch (error) {
    console.error('Projects error:', error);
    res.status(500).json({ success: false, message: 'Error fetching projects.' });
  }
};

module.exports = { getProjectSuggestions };
```

---

## `server/controllers/userController.js`

```javascript
const User = require('../models/User');

// @desc    Get user profile
// @route   GET /api/users/profile
// @access  Private
const getProfile = async (req, res) => {
  try {
    const user = await User.findById(req.user._id);
    res.json({ success: true, user });
  } catch (error) {
    res.status(500).json({ success: false, message: 'Server error.' });
  }
};

// @desc    Update user profile
// @route   PUT /api/users/update
// @access  Private
const updateProfile = async (req, res) => {
  try {
    const { name, skills, experienceLevel, bio, github, linkedin, isAvailable } = req.body;

    const updateData = {};
    if (name !== undefined) updateData.name = name;
    if (skills !== undefined) updateData.skills = skills.map(s => s.toLowerCase().trim()).filter(Boolean);
    if (experienceLevel !== undefined) updateData.experienceLevel = experienceLevel;
    if (bio !== undefined) updateData.bio = bio;
    if (github !== undefined) updateData.github = github;
    if (linkedin !== undefined) updateData.linkedin = linkedin;
    if (isAvailable !== undefined) updateData.isAvailable = isAvailable;

    const user = await User.findByIdAndUpdate(
      req.user._id,
      { $set: updateData },
      { new: true, runValidators: true }
    );

    res.json({
      success: true,
      message: 'Profile updated successfully!',
      user
    });
  } catch (error) {
    console.error('Update profile error:', error);
    if (error.name === 'ValidationError') {
      const messages = Object.values(error.errors).map(e => e.message);
      return res.status(400).json({ success: false, message: messages[0] });
    }
    res.status(500).json({ success: false, message: 'Server error.' });
  }
};

// @desc    Get all users (for browsing)
// @route   GET /api/users
// @access  Private
const getAllUsers = async (req, res) => {
  try {
    const users = await User.find({ _id: { $ne: req.user._id }, isAvailable: true })
      .select('-password')
      .sort({ createdAt: -1 });
    res.json({ success: true, count: users.length, users });
  } catch (error) {
    res.status(500).json({ success: false, message: 'Server error.' });
  }
};

module.exports = { getProfile, updateProfile, getAllUsers };
```

---

## `server/index.js`

```javascript
const express = require('express');
const cors = require('cors');
const morgan = require('morgan');
const dotenv = require('dotenv');
const connectDB = require('./config/db');

dotenv.config();

// Connect to MongoDB
connectDB();

const app = express();

// Middleware
app.use(cors({
  origin: process.env.CLIENT_URL || 'http://localhost:5173',
  credentials: true
}));
app.use(express.json());
app.use(morgan('dev'));

// Routes
app.use('/api/auth', require('./routes/authRoutes'));
app.use('/api/users', require('./routes/userRoutes'));
app.use('/api/match', require('./routes/matchRoutes'));
app.use('/api/projects', require('./routes/projectRoutes'));

// Health check
app.get('/api/health', (req, res) => {
  res.json({ status: 'OK', message: 'SkillSync API running' });
});

// Global error handler
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.statusCode || 500).json({
    success: false,
    message: err.message || 'Internal Server Error'
  });
});

// 404 handler
app.use((req, res) => {
  res.status(404).json({ success: false, message: 'Route not found' });
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
  console.log(`\n🚀 SkillSync Server running on port ${PORT}`);
  console.log(`📡 Environment: ${process.env.NODE_ENV}`);
});
```

---

## `server/middleware/authMiddleware.js`

```javascript
const jwt = require('jsonwebtoken');
const User = require('../models/User');

const protect = async (req, res, next) => {
  try {
    let token;

    if (req.headers.authorization && req.headers.authorization.startsWith('Bearer')) {
      token = req.headers.authorization.split(' ')[1];
    }

    if (!token) {
      return res.status(401).json({
        success: false,
        message: 'Access denied. No token provided.'
      });
    }

    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    const user = await User.findById(decoded.id);

    if (!user) {
      return res.status(401).json({
        success: false,
        message: 'User no longer exists.'
      });
    }

    req.user = user;
    next();
  } catch (error) {
    return res.status(401).json({
      success: false,
      message: 'Invalid or expired token.'
    });
  }
};

module.exports = { protect };
```

---

## `server/models/Match.js`

```javascript
const mongoose = require('mongoose');

const matchSchema = new mongoose.Schema({
  userId: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true
  },
  matchedUserId: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true
  },
  compatibilityScore: {
    type: Number,
    required: true,
    min: 0,
    max: 100
  },
  commonSkills: {
    type: [String],
    default: []
  }
}, {
  timestamps: true
});

// Compound index to avoid duplicate matches
matchSchema.index({ userId: 1, matchedUserId: 1 }, { unique: true });

module.exports = mongoose.model('Match', matchSchema);
```

---

## `server/models/Project.js`

```javascript
const mongoose = require('mongoose');

const projectSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true,
    trim: true
  },
  description: {
    type: String,
    required: true
  },
  requiredSkills: {
    type: [String],
    default: []
  },
  difficulty: {
    type: String,
    enum: ['beginner', 'intermediate', 'advanced'],
    required: true
  },
  techStack: {
    type: [String],
    default: []
  },
  estimatedDuration: {
    type: String,
    default: '2-4 weeks'
  },
  category: {
    type: String,
    default: 'General'
  }
}, {
  timestamps: true
});

module.exports = mongoose.model('Project', projectSchema);
```

---

## `server/models/User.js`

```javascript
const mongoose = require('mongoose');
const bcrypt = require('bcryptjs');

const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, 'Name is required'],
    trim: true,
    minlength: [2, 'Name must be at least 2 characters'],
    maxlength: [50, 'Name cannot exceed 50 characters']
  },
  email: {
    type: String,
    required: [true, 'Email is required'],
    unique: true,
    lowercase: true,
    trim: true,
    match: [/^\S+@\S+\.\S+$/, 'Please provide a valid email']
  },
  password: {
    type: String,
    required: [true, 'Password is required'],
    minlength: [6, 'Password must be at least 6 characters'],
    select: false
  },
  skills: {
    type: [String],
    default: [],
    set: (skills) => skills.map(s => s.toLowerCase().trim())
  },
  experienceLevel: {
    type: String,
    enum: ['beginner', 'intermediate', 'advanced', 'expert'],
    default: 'beginner'
  },
  bio: {
    type: String,
    maxlength: [300, 'Bio cannot exceed 300 characters'],
    default: ''
  },
  github: {
    type: String,
    default: ''
  },
  linkedin: {
    type: String,
    default: ''
  },
  avatar: {
    type: String,
    default: ''
  },
  isAvailable: {
    type: Boolean,
    default: true
  }
}, {
  timestamps: true
});

// Hash password before saving
userSchema.pre('save', async function (next) {
  if (!this.isModified('password')) return next();
  const salt = await bcrypt.genSalt(12);
  this.password = await bcrypt.hash(this.password, salt);
  next();
});

// Compare password method
userSchema.methods.comparePassword = async function (candidatePassword) {
  return await bcrypt.compare(candidatePassword, this.password);
};

// Return user without password
userSchema.methods.toJSON = function () {
  const obj = this.toObject();
  delete obj.password;
  return obj;
};

module.exports = mongoose.model('User', userSchema);
```

---

## `server/package.json`

```json
{
  "name": "skillsync-server",
  "version": "1.0.0",
  "description": "SkillSync Backend API",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  },
  "dependencies": {
    "bcryptjs": "^2.4.3",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "express": "^4.18.2",
    "jsonwebtoken": "^9.0.2",
    "mongoose": "^8.0.3",
    "morgan": "^1.10.0"
  },
  "devDependencies": {
    "nodemon": "^3.0.2"
  }
}
```

---

## `server/routes/authRoutes.js`

```javascript
const express = require('express');
const router = express.Router();
const { register, login, getMe } = require('../controllers/authController');
const { protect } = require('../middleware/authMiddleware');

router.post('/register', register);
router.post('/login', login);
router.get('/me', protect, getMe);

module.exports = router;
```

---

## `server/routes/matchRoutes.js`

```javascript
const express = require('express');
const router = express.Router();
const { getMatches, getMatchById } = require('../controllers/matchController');
const { protect } = require('../middleware/authMiddleware');

router.get('/', protect, getMatches);
router.get('/:id', protect, getMatchById);

module.exports = router;
```

---

## `server/routes/projectRoutes.js`

```javascript
const express = require('express');
const router = express.Router();
const { getProjectSuggestions } = require('../controllers/projectController');
const { protect } = require('../middleware/authMiddleware');

router.get('/', protect, getProjectSuggestions);

module.exports = router;
```

---

## `server/routes/userRoutes.js`

```javascript
const express = require('express');
const router = express.Router();
const { getProfile, updateProfile, getAllUsers } = require('../controllers/userController');
const { protect } = require('../middleware/authMiddleware');

router.get('/profile', protect, getProfile);
router.put('/update', protect, updateProfile);
router.get('/', protect, getAllUsers);

module.exports = router;
```

---

