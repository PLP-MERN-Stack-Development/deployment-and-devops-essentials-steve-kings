# 🚀 Kings Blog - Deployment Guide

## 📍 Live Application URLs

- **Frontend (Vercel)**: https://kings-blog.vercel.app/
- **Backend API (Render)**: https://blog-backend-7mnk.onrender.com/
- **API Health Check**: https://blog-backend-7mnk.onrender.com/api/health

---

## 🎯 Deployment Overview

This MERN stack application is deployed using:
- **Frontend**: Vercel (React/Vite application)
- **Backend**: Render (Express.js API)
- **Database**: MongoDB Atlas (Cloud-hosted)

---

## 🔧 Backend Deployment (Render)

### Configuration

**Service URL**: https://blog-backend-7mnk.onrender.com/

### Environment Variables Set on Render:
```
NODE_ENV=production
PORT=5000
MONGODB_URI=<your-mongodb-atlas-connection-string>
JWT_SECRET=<your-secure-jwt-secret>
JWT_EXPIRE=30d
```

### Build & Start Commands:
- **Build Command**: `npm install`
- **Start Command**: `npm start`
- **Root Directory**: `server`

### CORS Configuration:
The backend is configured to accept requests from:
- https://kings-blog.vercel.app
- http://localhost:3000 (for local development)

---

## 🎨 Frontend Deployment (Vercel)

### Configuration

**Service URL**: https://kings-blog.vercel.app/

### Environment Variables Set on Vercel:
```
VITE_API_URL=https://blog-backend-7mnk.onrender.com/api
```

### Build Settings:
- **Framework Preset**: Vite
- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Install Command**: `npm install`
- **Root Directory**: `client`

---

## 🗄️ Database (MongoDB Atlas)

### Configuration:
- **Cluster**: MongoDB Atlas (Cloud)
- **Database Name**: `mern-blog`
- **Connection**: Configured via `MONGODB_URI` environment variable

### Collections:
- `users` - User accounts and authentication
- `posts` - Blog posts with content
- `categories` - Post categories

---

## 🔐 Environment Variables Setup

### Backend (.env in server/)
```env
NODE_ENV=production
PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/mern-blog?retryWrites=true&w=majority
JWT_SECRET=your-super-secret-jwt-key-make-it-long-and-random
JWT_EXPIRE=30d
```

### Frontend (.env in client/)
```env
VITE_API_URL=https://blog-backend-7mnk.onrender.com/api
```

---

## ✅ Deployment Checklist

### Pre-Deployment
- [x] MongoDB Atlas cluster created and configured
- [x] Environment variables prepared
- [x] CORS configured for production URLs
- [x] Health check endpoint implemented
- [x] Code pushed to GitHub

### Backend (Render)
- [x] Render account created
- [x] New Web Service created
- [x] Connected to GitHub repository
- [x] Environment variables configured
- [x] Build and start commands set
- [x] Service deployed successfully
- [x] Health check endpoint verified

### Frontend (Vercel)
- [x] Vercel account created
- [x] Project imported from GitHub
- [x] Environment variables configured
- [x] Build settings configured
- [x] Deployment successful
- [x] Custom domain configured (optional)

---

## 🧪 Testing the Deployment

### 1. Backend Health Check
```bash
curl https://blog-backend-7mnk.onrender.com/api/health
```

Expected response:
```json
{
  "uptime": 12345,
  "message": "OK",
  "timestamp": 1234567890,
  "environment": "production",
  "database": "connected"
}
```

### 2. Frontend Access
Visit: https://kings-blog.vercel.app/

### 3. API Endpoints Test
```bash
# Get all posts
curl https://blog-backend-7mnk.onrender.com/api/posts

# Get categories
curl https://blog-backend-7mnk.onrender.com/api/categories
```

---

## 🔄 Continuous Deployment

### Automatic Deployments Configured:

**Vercel (Frontend)**:
- Automatically deploys on push to `main` branch
- Preview deployments for pull requests
- Build logs available in Vercel dashboard

**Render (Backend)**:
- Automatically deploys on push to `main` branch
- Manual deploy option available
- Logs available in Render dashboard

---

## 📊 Monitoring & Maintenance

### Health Monitoring
- **Endpoint**: `/api/health`
- **Purpose**: Check server uptime, database connection, and system status
- **Frequency**: Can be monitored with uptime services (UptimeRobot, Pingdom)

### Logs Access
- **Render**: View logs in Render dashboard under "Logs" tab
- **Vercel**: View build and function logs in Vercel dashboard
- **MongoDB Atlas**: Monitor database performance in Atlas dashboard

### Performance Monitoring
- Monitor API response times
- Track database query performance
- Monitor frontend load times

---

## 🐛 Troubleshooting

### Common Issues

**1. CORS Errors**
- Verify frontend URL is added to CORS whitelist in `server/server.js`
- Check that API URL in frontend matches backend URL

**2. Database Connection Issues**
- Verify MongoDB Atlas IP whitelist (allow all: 0.0.0.0/0 for cloud deployments)
- Check MONGODB_URI environment variable is correct
- Ensure database user has proper permissions

**3. API Not Responding**
- Check Render service status
- Verify environment variables are set
- Check logs for errors

**4. Frontend Build Failures**
- Verify all dependencies are in package.json
- Check build logs in Vercel dashboard
- Ensure VITE_API_URL is set correctly

---

## 🔄 Updating the Application

### To Deploy Updates:

1. **Make changes locally**
2. **Test locally**:
   ```bash
   # Terminal 1 - Backend
   cd server
   npm run dev
   
   # Terminal 2 - Frontend
   cd client
   npm run dev
   ```
3. **Commit and push**:
   ```bash
   git add .
   git commit -m "Your update message"
   git push origin main
   ```
4. **Automatic deployment** will trigger on both Render and Vercel

---

## 📈 Scaling Considerations

### Current Setup (Free Tier):
- Render: Free tier with sleep after inactivity
- Vercel: Generous free tier for hobby projects
- MongoDB Atlas: Free M0 cluster (512MB storage)

### For Production Scale:
- Upgrade Render to paid plan for always-on service
- Consider Vercel Pro for better performance
- Upgrade MongoDB Atlas cluster for more storage/performance
- Implement caching (Redis)
- Add CDN for static assets
- Implement rate limiting

---

## 🔒 Security Best Practices

- [x] Environment variables stored securely
- [x] JWT tokens for authentication
- [x] Password hashing with bcrypt
- [x] CORS configured properly
- [x] HTTPS enabled on both frontend and backend
- [ ] Rate limiting (recommended for production)
- [ ] Input sanitization (recommended enhancement)
- [ ] Security headers (helmet.js recommended)

---

## 📝 Additional Resources

- [Render Documentation](https://render.com/docs)
- [Vercel Documentation](https://vercel.com/docs)
- [MongoDB Atlas Documentation](https://docs.atlas.mongodb.com/)
- [Express.js Best Practices](https://expressjs.com/en/advanced/best-practice-security.html)
- [React Deployment Guide](https://create-react-app.dev/docs/deployment/)

---

**Deployed by**: Stephen Kingori - PLP Student (2025)  
**Last Updated**: November 20, 2025
