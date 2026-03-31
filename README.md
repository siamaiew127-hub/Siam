# 🚀 Portfolio Website — Full Stack

A complete, production-ready portfolio with admin dashboard.
**Frontend → GitHub Pages | Backend → Render | Database → MongoDB Atlas**

---

## 🗂️ Project Structure

```
portfolio-backend/         ← Node.js + Express + MongoDB API
portfolio-frontend/        ← Static frontend (GitHub Pages)
  ├── index.html           ← Main portfolio page
  ├── admin/
  │   ├── login.html       ← Admin login
  │   └── dashboard.html   ← Admin dashboard
  └── assets/
      ├── css/style.css
      ├── css/admin.css
      ├── js/config.js     ← ⚠️ Update API_BASE here!
      ├── js/main.js
      └── admin/admin.js
```

---

## ⚡ Quick Deployment Guide

### Step 1 — MongoDB Atlas (Free)
1. Go to [https://cloud.mongodb.com](https://cloud.mongodb.com)
2. Create a free cluster
3. Create a database user (username + password)
4. Whitelist IP: `0.0.0.0/0` (allow all for Render)
5. Copy connection string: `mongodb+srv://user:pass@cluster.mongodb.net/portfolio`

### Step 2 — Cloudinary (Free, for images)
1. Go to [https://cloudinary.com](https://cloudinary.com)
2. Sign up and get: Cloud Name, API Key, API Secret

### Step 3 — Deploy Backend to Render
1. Push `portfolio-backend/` to a **separate** GitHub repo
2. Go to [https://render.com](https://render.com) → New → Web Service
3. Connect your backend repo
4. Set these environment variables:
   ```
   NODE_ENV=production
   PORT=10000
   MONGODB_URI=<your MongoDB URI>
   JWT_SECRET=<a long random string>
   ADMIN_USERNAME=admin
   ADMIN_PASSWORD=<your secure password>
   CLOUDINARY_CLOUD_NAME=<from Cloudinary>
   CLOUDINARY_API_KEY=<from Cloudinary>
   CLOUDINARY_API_SECRET=<from Cloudinary>
   FRONTEND_URL=https://yourusername.github.io
   ```
5. Build Command: `npm install`
6. Start Command: `npm start`
7. Deploy — copy your Render URL (e.g. `https://portfolio-api.onrender.com`)

### Step 4 — Configure Frontend
1. Open `portfolio-frontend/assets/js/config.js`
2. Update:
   ```js
   API_BASE: 'https://your-backend.onrender.com'
   SITE_URL: 'https://yourusername.github.io'
   ```

### Step 5 — Deploy Frontend to GitHub Pages
1. Push `portfolio-frontend/` to a GitHub repo (can be `yourusername.github.io`)
2. Go to repo Settings → Pages → Source: main branch, root `/`
3. Your site will be live at `https://yourusername.github.io`

---

## 🔐 Admin Access

- URL: `https://yourusername.github.io/admin/login.html`
- Username: whatever you set in `ADMIN_USERNAME`
- Password: whatever you set in `ADMIN_PASSWORD`

---

## 🛠️ Local Development

### Backend
```bash
cd portfolio-backend
cp .env.example .env
# Fill in .env values
npm install
npm run dev       # runs on http://localhost:5000
```

### Frontend
```bash
# Just open with Live Server (VS Code extension)
# or use:
cd portfolio-frontend
npx serve .       # runs on http://localhost:3000
```

---

## 📋 API Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| GET | /api/profile | — | Get profile |
| PUT | /api/profile | ✅ | Update profile |
| POST | /api/profile/avatar | ✅ | Upload avatar |
| GET | /api/skills | — | Get skills |
| POST | /api/skills | ✅ | Add skill |
| PUT | /api/skills/:id | ✅ | Update skill |
| DELETE | /api/skills/:id | ✅ | Delete skill |
| GET | /api/projects | — | Get projects |
| POST | /api/projects | ✅ | Add project |
| PUT | /api/projects/:id | ✅ | Update project |
| DELETE | /api/projects/:id | ✅ | Delete project |
| GET | /api/services | — | Get services |
| POST | /api/services | ✅ | Add service |
| PUT | /api/services/:id | ✅ | Update service |
| DELETE | /api/services/:id | ✅ | Delete service |
| GET | /api/social | — | Get social links |
| PUT | /api/social | ✅ | Update social links |
| GET | /api/cv | — | Get CV info |
| POST | /api/cv | ✅ | Upload CV |
| DELETE | /api/cv | ✅ | Delete CV |
| POST | /api/contact | — | Send message |
| GET | /api/contact | ✅ | Get all messages |
| DELETE | /api/contact/:id | ✅ | Delete message |
| POST | /api/auth/login | — | Admin login |
| GET | /api/auth/me | ✅ | Get current user |
| PUT | /api/auth/change-password | ✅ | Change password |

---

## 🎨 Design Features

- **Color Scheme**: White bg, deep black text, orange (#FF6B2B) accent
- **Font**: Poppins (Century Gothic fallback)
- **Dark/Light Mode** toggle
- **Fully Responsive** (mobile-first)
- **Smooth Animations**: scroll reveal, count-up stats, skill bar animations
- **Premium UI**: floating cards, blob backgrounds, grid overlay, glassmorphism nav
- **Project Modal**: lightbox with details
- **Contact Form**: live validation + success/error states
- **Admin Dashboard**: full CRUD for all content sections

---

## 🔒 Security Features

- JWT authentication (7-day expiry)
- bcrypt password hashing (12 rounds)
- Rate limiting (100 req/15min, 10 logins/15min)
- Helmet.js HTTP security headers
- CORS whitelist
- XSS escaping on frontend
- Admin-only routes protected

---

Built with ❤️ — Node.js + Express + MongoDB + Vanilla JS
