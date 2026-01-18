# Medical Store POS - Angular Frontend

Production-grade Angular frontend for Medical Store Point of Sale system.

## 🏗️ Architecture

### Technology Stack
- **Angular 17+** with TypeScript strict mode
- **Bootstrap 5** for UI components
- **RxJS** for reactive programming
- **JWT** authentication
- **Lazy loading** for feature modules

### Project Structure

```
src/app/
├── auth/                    # Authentication module
│   ├── login/              # Login component
│   ├── auth.service.ts     # Auth service (re-export)
│   ├── auth.guard.ts       # Route guard
│   ├── role.guard.ts       # Role-based guard
│   └── token.interceptor.ts # JWT interceptor
│
├── core/                    # Core services and models
│   ├── services/           # API services
│   │   ├── api.service.ts
│   │   ├── auth.service.ts
│   │   ├── billing.service.ts
│   │   ├── inventory.service.ts
│   │   ├── report.service.ts
│   │   └── return.service.ts
│   └── models/             # TypeScript interfaces
│
├── modules/                 # Feature modules (lazy loaded)
│   ├── billing/            # Billing module (MOST IMPORTANT)
│   ├── inventory/          # Inventory management
│   ├── medicines/          # Medicine management
│   ├── returns/            # Returns & refunds
│   └── reports/            # Reports & analytics
│
├── shared/                  # Shared components
│   └── components/
│
├── app-routing.module.ts   # Main routing
└── app.module.ts           # Root module
```

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn
- Angular CLI 17+

### Installation

```bash
cd frontend
npm install
```

### Development Server

```bash
npm start
# or
ng serve
```

Navigate to `http://localhost:4200`

### Build for Production

```bash
ng build --configuration production
```

## 🔐 Authentication Flow

1. **Login**: User enters credentials
2. **Token Storage**: JWT token stored in localStorage
3. **Interceptor**: TokenInterceptor adds `Authorization: Bearer <token>` header to all requests
4. **Guards**: 
   - `AuthGuard`: Checks if user is authenticated
   - `RoleGuard`: Checks if user has required role
5. **Auto Logout**: On 401 response, user is logged out

### Default Credentials
- Username: `admin`
- Password: `admin123`

## 💰 Billing Module (Most Important)

### Features
- **Medicine Search**: Real-time search by name
- **FIFO Batch Selection**: Backend automatically selects earliest expiring batch
- **Expiry Warnings**: Visual indicators for expiring batches
- **Low Stock Alerts**: Warnings when stock is low
- **GST Calculation**: Automatic GST breakdown (CGST/SGST)
- **Payment Processing**: 
  - Multiple payment modes (Cash/UPI/Card)
  - Split payments support
  - Payment validation
- **Invoice Preview**: Printable invoice with all details

### Billing Flow

1. **Search Medicine**: Type medicine name in search box
2. **Select Medicine**: Click on medicine from results
3. **Auto Batch Selection**: System selects FIFO batch automatically
4. **Add to Bill**: Medicine added with quantity 1 (editable)
5. **Update Quantities**: Edit quantities directly in table
6. **Process Payment**: Click "Process Payment" button
7. **Add Payments**: Add one or more payment methods
8. **Confirm Bill**: Submit bill (stock deducted on backend)
9. **View Invoice**: Invoice displayed with print option

### Key Business Rules (Frontend)

- **No Expired Batches**: Expired batches cannot be added to bill
- **Stock Validation**: Quantity cannot exceed available stock
- **Payment Validation**: Total payment must equal bill amount
- **GST Display**: Shows GST breakdown but backend calculates actual values

## 📦 Other Modules

### Inventory Module
- View expired batches
- View low stock batches
- Batch management

### Medicines Module
- List all medicines
- Add new medicines
- Update medicine status

### Returns Module
- Search bill by bill number
- Select items for return
- Process refunds
- Stock restored to original batch (backend)

### Reports Module
- Daily sales report
- GST report with HSN-wise breakdown
- Date range filtering

## 🔧 Services

### API Service
Central HTTP service with error handling:
```typescript
this.apiService.get<Medicine[]>('/pharmacist/medicines')
this.apiService.post<BillResponse>('/cashier/bills', request)
```

### Auth Service
Manages authentication state:
```typescript
this.authService.login(credentials)
this.authService.isAuthenticated()
this.authService.hasRole(UserRole.ADMIN)
```

## 🛡️ Security

### Route Guards
- **AuthGuard**: Protects routes requiring authentication
- **RoleGuard**: Protects routes based on user role

### Role-Based Access
- **ADMIN**: All modules
- **PHARMACIST**: Billing, Inventory, Medicines, Returns
- **CASHIER**: Billing, Returns

### JWT Interceptor
Automatically adds token to all HTTP requests:
```typescript
Authorization: Bearer <token>
```

## 🎨 UX Features (POS-Optimized)

- **Keyboard Navigation**: Auto-focus on search input
- **Minimal Clicks**: Streamlined workflows
- **Clear Errors**: User-friendly error messages
- **No Animations**: Fast, responsive UI
- **Visual Indicators**: Color-coded warnings (expiry, low stock)

## 📝 Error Handling

### Centralized Error Handler
All API errors handled in `ApiService`:
- Maps backend errors to user-friendly messages
- Logs errors to console
- Shows alerts for critical errors

### Error Display
- Form validation errors shown inline
- API errors shown as alerts
- Network errors handled gracefully

## 🔄 State Management

Currently using:
- **Services with BehaviorSubject** for auth state
- **Component state** for module-specific data
- **RxJS Observables** for async operations

## 📱 Responsive Design

- Bootstrap 5 grid system
- Mobile-friendly layouts
- Print-optimized invoice view

## 🧪 Testing

```bash
# Unit tests
ng test

# E2E tests (if configured)
ng e2e
```

## 🚨 Important Notes

1. **Backend is Source of Truth**: Frontend displays backend-calculated values
2. **No Business Logic**: All calculations done on backend
3. **Validation**: Frontend validates for UX, backend validates for security
4. **Error Handling**: Always show user-friendly error messages
5. **Performance**: Lazy loading reduces initial bundle size

## 🔗 Backend Integration

### API Base URL
Configured in `environments/environment.ts`:
```typescript
apiUrl: 'http://localhost:8080/api'
```

### Endpoints Used
- `/api/auth/login` - Authentication
- `/api/cashier/bills` - Billing
- `/api/pharmacist/medicines` - Medicine management
- `/api/pharmacist/batches` - Batch management
- `/api/cashier/returns` - Returns
- `/api/admin/reports/*` - Reports

## 📄 License

Proprietary - Medical Store POS System

---

**Built for production-grade healthcare retail systems**



