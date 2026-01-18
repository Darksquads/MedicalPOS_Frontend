# Frontend Deployment Guide

This folder contains the deployment-ready frontend code for the Medical Store POS system.

## Prerequisites

- Node.js (v16 or higher)
- npm (v8 or higher) or yarn

## Installation

1. Install dependencies:
```bash
npm install
```

## Build for Production

```bash
npm run build
```

This will create a `dist/medical-store-pos/browser` folder with the production-ready files.

## Development Server

```bash
npm start
```

The application will be available at `http://localhost:4200`

## Environment Configuration

Update the API endpoint in:
- `src/environments/environment.ts` (development)
- `src/environments/environment.prod.ts` (production)

## Deployment

### Static Hosting (Netlify, Vercel, etc.)

1. Build the application: `npm run build`
2. Deploy the `dist/medical-store-pos/browser` folder

### Nginx/Apache

1. Build the application: `npm run build`
2. Configure your web server to serve files from `dist/medical-store-pos/browser`
3. Set up URL rewriting to redirect all routes to `index.html` for Angular routing

### Docker

Create a Dockerfile:
```dockerfile
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist/medical-store-pos/browser /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## Notes

- `node_modules` and `dist` folders are excluded from this deployment package
- Run `npm install` before building
- Ensure the backend API is accessible from the frontend domain

