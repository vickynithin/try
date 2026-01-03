# Quick Deployment Checklist

## Before Deploying

- [ ] Test locally (both servers running)
- [ ] Create GitHub account
- [ ] Create Vercel account (free)
- [ ] Create Render account (free tier)
- [ ] Create MongoDB Atlas account (free tier)

## Step-by-Step

### 1️⃣ GitHub Setup
```bash
cd c:\try
git init
git add .
git commit -m "MERN todo app"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mern-todo.git
git push -u origin main
```

### 2️⃣ MongoDB Atlas
- Create cluster at mongodb.com/cloud/atlas
- Get connection string with credentials
- Save: `mongodb+srv://user:pass@cluster0.mongodb.net/mern-todo?retryWrites=true&w=majority`

### 3️⃣ Deploy Backend to Render
- New Web Service from GitHub repo
- Root: `backend/`
- Build: `npm install`
- Start: `npm start`
- Env vars:
  - `MONGODB_URI`: (from MongoDB Atlas)
  - `JWT_SECRET`: (your secret)
  - `PORT`: `5000`
- ✅ Copy backend URL: `https://your-backend.onrender.com`

### 4️⃣ Deploy Frontend to Vercel
- New project from GitHub repo
- Root: `frontend/`
- Build: `npm run build`
- Output: `dist`
- Env var: `VITE_API_URL`: `https://your-backend.onrender.com`
- ✅ Your app is live!

## Links
- 🌐 Frontend: `https://your-project.vercel.app`
- 🔌 Backend API: `https://your-backend.onrender.com`
- 📊 MongoDB: Your cluster in MongoDB Atlas
