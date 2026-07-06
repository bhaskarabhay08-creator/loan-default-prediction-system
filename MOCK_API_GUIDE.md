# Mock API Guide - Test Without Backend

The frontend now supports **Mock API** for testing and demos without needing the Flask backend running.

## Quick Start - Test Login Now

The system comes with mock API **enabled by default**. Just run:

```bash
pnpm dev
```

Visit `http://localhost:3000` and use these credentials to sign in:

### Demo User Account
- **Email**: `user@example.com`
- **Password**: `password123`

### Demo Admin Account
- **Email**: `admin@example.com`
- **Password**: `admin123`

## What the Mock API Provides

### Authentication
- ✅ User login with demo credentials
- ✅ User registration (creates new mock users)
- ✅ JWT token generation
- ✅ Auto-logout on token expiry

### Dashboard
- ✅ User dashboard with mock applications
- ✅ Application statistics
- ✅ Application list

### ML Predictions
- ✅ Real-time loan default predictions
- ✅ Risk level classification
- ✅ Confidence scoring
- ✅ Approval recommendations

## Configuration

### Enable Mock API (Default)
In `.env.local`:
```
NEXT_PUBLIC_USE_MOCK_API=true
```

### Disable Mock API (Use Real Backend)
In `.env.local`:
```
NEXT_PUBLIC_USE_MOCK_API=false
```

Then start your Flask backend:
```bash
cd backend
python app.py
```

## Mock API Endpoints

When `NEXT_PUBLIC_USE_MOCK_API=true`, these endpoints work with mock data:

```
POST /auth/login              → Login with credentials
POST /auth/register           → Create new user
GET  /dashboard/user          → Get dashboard data
POST /ml/predict              → Get loan predictions
GET  /admin/dashboard         → Get admin stats
```

## Testing Flow

1. **Start Frontend Only**
   ```bash
   pnpm dev
   ```

2. **Register a New User**
   - Visit: http://localhost:3000/auth/register
   - Fill in any details (mock accepts all valid formats)
   - Submit

3. **Login**
   - Visit: http://localhost:3000/auth/login
   - Use credentials: `user@example.com` / `password123`
   - Or use your newly registered account

4. **Use Dashboard**
   - View mock applications
   - See statistics
   - Test all features

5. **Test Loan Prediction**
   - Go to: http://localhost:3000/dashboard/apply
   - Fill loan application form
   - See real-time ML predictions
   - Submit application

## Mock Data Details

### Mock Users
```javascript
{
  'user@example.com': {
    password: 'password123',
    user: {
      id: '1',
      email: 'user@example.com',
      full_name: 'Demo User',
      role: 'user',
      aadhaar: '123456789012',
      pan: 'ABCDE1234F',
      phone: '9876543210'
    }
  },
  'admin@example.com': {
    password: 'admin123',
    user: {
      id: '2',
      email: 'admin@example.com',
      full_name: 'Admin User',
      role: 'admin',
      aadhaar: '123456789012',
      pan: 'ABCDE1234F',
      phone: '9876543210'
    }
  }
}
```

### Mock Dashboard Data
```json
{
  "applications": [
    {
      "id": "1",
      "loan_amount": 500000,
      "status": "approved",
      "created_at": "2026-06-26T..."
    },
    {
      "id": "2",
      "loan_amount": 1000000,
      "status": "pending",
      "created_at": "2026-06-26T..."
    }
  ],
  "stats": {
    "total_applications": 2,
    "approved": 1,
    "rejected": 0,
    "pending": 1
  }
}
```

### Mock ML Predictions
```json
{
  "default_probability": 0.23,
  "approved_probability": 0.77,
  "risk_level": "LOW",
  "confidence": 0.88,
  "recommendation": "APPROVE"
}
```

## Switching to Real Backend

When ready to test with the real backend:

1. **Update .env.local**
   ```
   NEXT_PUBLIC_USE_MOCK_API=false
   ```

2. **Start Flask Backend**
   ```bash
   cd backend
   pip install -r requirements.txt
   python train_model.py    # Train ML models once
   python app.py            # Start server
   ```

3. **Frontend will connect to backend**
   - API calls go to `http://localhost:5000`
   - Real ML predictions from trained models
   - Real database queries

## Troubleshooting

### Login not working?
1. Check if `.env.local` has `NEXT_PUBLIC_USE_MOCK_API=true`
2. Use demo credentials: `user@example.com` / `password123`
3. Try registering a new account

### Still getting API errors?
1. Run: `pnpm dev` (frontend on port 3000)
2. Check browser console for errors
3. Verify `.env.local` is in project root

### Want to use real backend?
1. Set `NEXT_PUBLIC_USE_MOCK_API=false` in `.env.local`
2. Start Flask: `cd backend && python app.py`
3. Reload frontend in browser

## Features Tested with Mock API

- ✅ User registration & login
- ✅ Form validation
- ✅ Dark theme UI
- ✅ Responsive design
- ✅ Dashboard display
- ✅ ML predictions
- ✅ Error handling
- ✅ Loading states
- ✅ Token persistence
- ✅ Auto-logout

## Next Steps

1. **Test All Pages**
   - Landing page
   - Login/Register pages
   - Dashboard
   - Loan application form
   - Admin dashboard

2. **Customize Mock Data**
   - Edit `/lib/api.ts` in `handleMockRequest` function
   - Add more mock users
   - Modify mock predictions

3. **Connect Real Backend**
   - When ready, disable mock API
   - Start Flask server
   - Update `.env.local`
   - Test real ML models

---

**Happy Testing! The entire frontend works with mock API enabled.** 🚀
