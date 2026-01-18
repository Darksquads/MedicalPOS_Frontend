# Vercel Deployment Guide

## Configuration Files

### vercel.json
- **Output Directory**: `dist/medical-store-pos/browser`
- **Build Command**: `npm run build` (uses production configuration)
- **Rewrites**: All routes redirect to `index.html` for Angular SPA routing

## Deployment Steps

1. **Connect Repository to Vercel**
   - Go to [Vercel Dashboard](https://vercel.com)
   - Click "Add New Project"
   - Import your Git repository
   - Select the `frontend_DeployReady` folder as the root directory

2. **Configure Build Settings**
   - **Framework Preset**: Other
   - **Root Directory**: `frontend_DeployReady` (or leave empty if repo root)
   - **Build Command**: `npm run build` (already in vercel.json)
   - **Output Directory**: `dist/medical-store-pos/browser` (already in vercel.json)
   - **Install Command**: `npm install`

3. **Environment Variables** (if needed)
   - No environment variables required for frontend
   - API URL is already configured in `environment.prod.ts`

4. **Deploy**
   - Click "Deploy"
   - Vercel will automatically build and deploy

## Troubleshooting

### Build Fails
- Check Node.js version (Angular 17 requires Node 18+)
- Verify all dependencies are in `package.json`
- Check build logs for specific errors

### Routing Issues
- The `vercel.json` includes rewrites for SPA routing
- All routes redirect to `index.html`

### API Connection Issues
- Verify `environment.prod.ts` has correct API URL
- Check CORS settings on backend
- Ensure backend is deployed and accessible

## Build Output

The production build creates:
- `dist/medical-store-pos/browser/` - Contains all static files
- `index.html` - Entry point
- Optimized and minified JavaScript/CSS bundles

