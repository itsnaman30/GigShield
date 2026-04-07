# Render Deployment Guide for Iron House Gym

## Prerequisites
- GitHub repository: https://github.com/itsnaman30/CrowdCover
- Render account (free at render.com)

## Step 1: Prepare Backend for Production

### Update backend/package.json
Add start script:
```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  }
}
```

### Create backend/.env file for production
```
NODE_ENV=production
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

## Step 2: Prepare Frontend for Production

### Update frontend/vite.config.js
```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  server: {
    host: '0.0.0.0',
    port: 5173,
    strictPort: true,
    open: true
  },
  build: {
    outDir: 'dist',
    assetsDir: 'assets'
  }
})
```

### Update frontend/package.json
Add build script:
```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  }
}
```

## Step 3: Deploy to Render

### Backend Deployment
1. Go to [render.com](https://render.com)
2. Click "New" -> "Web Service"
3. Connect your GitHub repository
4. Select "CrowdCover" repository
5. Configure:
   - Name: iron-house-gym-api
   - Environment: Node
   - Build Command: cd backend && npm install
   - Start Command: cd backend && npm start
   - Instance Type: Free

### Frontend Deployment
1. Click "New" -> "Static Site"
2. Connect your GitHub repository
3. Select "CrowdCover" repository
4. Configure:
   - Name: iron-house-gym
   - Build Command: cd frontend && npm install && npm run build
   - Publish Directory: frontend/dist
   - Instance Type: Free

## Step 4: Environment Variables

### Backend Environment Variables
In Render dashboard, add these to your backend service:
- NODE_ENV=production
- MONGODB_URI=your_mongodb_atlas_connection
- JWT_SECRET=your_secret_key

## Step 5: Update Frontend API URL

### Create production environment variable
In frontend/.env.production:
```
VITE_API_URL=https://your-backend-service-name.onrender.com/api
```

## Step 6: Deploy!

1. Push changes to GitHub
2. Render will automatically build and deploy
3. Your app will be live at:
   - Frontend: https://iron-house-gym.onrender.com
   - Backend: https://iron-house-gym-api.onrender.com

## Step 7: Test Your Live App

Visit your frontend URL and test all features:
- Navigation between pages
- API connectivity
- All 9 pages working

## Troubleshooting

### Common Issues:
1. **Build fails**: Check package.json scripts
2. **API connection errors**: Verify environment variables
3. **Database connection**: Ensure MongoDB Atlas is accessible
4. **CORS errors**: Update backend CORS settings

### Get Help:
- Check Render logs
- Review build output
- Test locally first
