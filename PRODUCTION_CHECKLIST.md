# Production Checklist

## Security

- [ ] Change JWT_SECRET in backend .env (use strong random string)
- [ ] Enable MongoDB whitelist in Atlas (or use IP restrictions)
- [ ] Use HTTPS everywhere (Vercel/Render handle this)
- [ ] Add CORS_ORIGIN env var for production

## Backend (.env for Render)

```
PORT=5000
MONGODB_URI=mongodb+srv://user:password@cluster0.mongodb.net/mern-todo?retryWrites=true&w=majority
JWT_SECRET=your-super-secret-key-change-this-in-production
```

## Frontend (Vercel Environment)

```
VITE_API_URL=https://your-backend.onrender.com
```

## Post-Deployment

1. Test registration/login flow
2. Create a test todo
3. Refresh page (data should persist)
4. Test logout and re-login
5. Monitor Render/Vercel logs for errors

## Future Improvements

- Add email verification
- Add password reset
- Add todo categories/tags
- Add sharing/collaboration
- Add mobile app (React Native)
