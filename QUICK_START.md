# Quick Start Guide - Angular Frontend

## 🚀 Setup & Run

### 1. Install Dependencies
```bash
cd frontend
npm install
```

### 2. Start Development Server
```bash
npm start
# or
ng serve
```

Application will be available at: `http://localhost:4200`

### 3. Build for Production
```bash
ng build --configuration production
```

## 🔐 Login

1. Navigate to `http://localhost:4200`
2. You'll be redirected to login page
3. Use default credentials:
   - **Username**: `admin`
   - **Password**: `admin123`

## 📋 Available Modules

After login, you'll see navigation menu with:

- **Billing** - Create bills, process payments (All roles)
- **Inventory** - View expired/low stock batches (Pharmacist/Admin)
- **Medicines** - Manage medicines (Pharmacist/Admin)
- **Returns** - Process returns & refunds (All roles)
- **Reports** - View sales & GST reports (Admin only)

## 💰 Billing Workflow

1. **Search Medicine**: Type medicine name in search box
2. **Select Medicine**: Click on medicine from dropdown
3. **Auto-Add**: Medicine automatically added with FIFO batch
4. **Adjust Quantity**: Edit quantity in the table
5. **Process Payment**: Click "Process Payment" button
6. **Add Payments**: Add one or more payment methods
7. **Confirm**: Submit bill (invoice displayed)

## 🔧 Configuration

### API URL
Edit `src/environments/environment.ts`:
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:8080/api'  // Change if backend is on different port
};
```

## 🐛 Troubleshooting

### CORS Issues
If you see CORS errors, ensure backend allows requests from `http://localhost:4200`

### Authentication Errors
- Check if backend is running
- Verify API URL in environment file
- Check browser console for errors

### Module Not Found
Run `npm install` to ensure all dependencies are installed

## 📝 Notes

- Backend must be running on port 8080 (or update environment.ts)
- All API calls include JWT token automatically
- Token expires after 24 hours (backend default)
- Logout clears token and redirects to login



