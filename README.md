# Medical Store POS - Frontend

Production-ready Angular frontend for Medical Store POS system.

## Prerequisites

- Node.js 18+ 
- npm 9+

## Local Development

1. Install dependencies:
```bash
npm install
```

2. Update API URL in `src/environments/environment.ts`:
```typescript
apiUrl: 'http://localhost:8080/api'
```

3. Run development server:
```bash
npm start
```

4. Build for production:
```bash
npm run build
```

## Deployment

### Vercel (Recommended)

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Deploy:
```bash
vercel
```

Or connect your GitHub repository directly to Vercel dashboard.

3. The production API URL is already configured in `src/environments/environment.prod.ts`:
   - Current: `https://medicalpos-backend.onrender.com/api`
   - To change: Update the `apiUrl` in `environment.prod.ts` before building

### Netlify

1. Build command: `npm run build`
2. Publish directory: `dist/medical-store-pos/browser`
3. The production API URL is already configured in `src/environments/environment.prod.ts`:
   - Current: `https://medicalpos-backend.onrender.com/api`

### Other Static Hosting

1. Build the project:
```bash
npm run build
```

2. Deploy the `dist/medical-store-pos/browser` folder to your hosting provider

## Environment Variables

The production API URL is configured in `src/environments/environment.prod.ts`:
- Current production API: `https://medicalpos-backend.onrender.com/api`
- Development API: `http://localhost:8080/api` (configured in `environment.ts`)

## Build Configuration

The project is configured to build with:
- Output directory: `dist/medical-store-pos/browser`
- Base href: `/`
- Production optimizations enabled

## Notes

- The production API URL is already configured to `https://medicalpos-backend.onrender.com/api`
- To change the API URL, update `src/environments/environment.prod.ts` before building
- The frontend uses Angular routing, so ensure your hosting provider supports SPA routing (all routes redirect to index.html)

