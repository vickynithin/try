# Deployment Guide

## Frontend (React + Vite) → Vercel

### Step 1: Prepare your frontend for Vercel

The frontend is ready! Just make sure the `VITE_API_URL` environment variable is set in Vercel.

### Step 2: Push to GitHub

```bash
# From c:\try folder:
git init
git add .
git commit -m "Initial commit: MERN todo app"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mern-todo.git
git push -u origin main
```

### Step 3: Deploy Frontend to Vercel

1. Go to [Vercel.com](https://vercel.com)
2. Click "New Project"
3. Import your GitHub repo (`mern-todo`)
4. Framework: Select **Other** (since we have multiple apps)
5. **Root Directory**: Set to `frontend`
6. **Build Command**: `npm run build`
7. **Output Directory**: `dist`
8. **Environment Variables**: Add:
   - `VITE_API_URL` = `https://your-backend-url.onrender.com` (we'll set up backend next)
9. Click **Deploy**

✅ **Frontend will be live at**: `https://your-project.vercel.app`

---

## Backend (Express + MongoDB) → Render.com

### Step 1: Set up MongoDB Atlas (Cloud Database)

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create free account and cluster
3. Click "Connect" → "Drivers" → Copy connection string
4. Replace `<username>:<password>` with actual credentials
5. Example: `mongodb+srv://user:pass@cluster0.mongodb.net/mern-todo?retryWrites=true&w=majority`

### Step 2: Deploy Backend to Render.com

1. Go to [Render.com](https://render.com)
2. Click "New +" → "Web Service"
3. Connect your GitHub repo
4. Select `backend` folder as root
5. **Runtime**: Node
6. **Build Command**: `npm install`
7. **Start Command**: `npm start`
8. **Environment Variables**:
   - `PORT`: `5000`
   - `MONGODB_URI`: Paste your MongoDB Atlas connection string
   - `JWT_SECRET`: Use a strong secret (e.g., `your-super-secret-key-change-this`)
9. Click **Create Web Service**

✅ **Backend will be live at**: `https://your-backend.onrender.com`

### Step 3: Update Frontend Environment

Go back to Vercel:
1. Project Settings → Environment Variables
2. Update `VITE_API_URL` = `https://your-backend.onrender.com`
3. Redeploy

---

## Testing Deployed App

1. Open `https://your-project.vercel.app`
2. Register a new account
3. Create, update, delete todos
4. Refresh page → data persists in MongoDB Atlas ✅

---

## Troubleshooting

**Frontend can't connect to backend?**
- Check `VITE_API_URL` is set correctly in Vercel
- Check Render backend is running (may take 1-2 min to start)
- Check CORS is enabled in backend

**Backend errors on Render?**
- Check `MONGODB_URI` is correct
- Check `JWT_SECRET` is set
- View logs in Render dashboard

**MongoDB connection fails?**
- Whitelist your Render IP in MongoDB Atlas → Network Access
- Or allow all IPs (0.0.0.0/0) for testing
