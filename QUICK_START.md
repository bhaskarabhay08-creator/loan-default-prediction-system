# LoanPredict - Quick Start Guide

## 🚀 Getting Started in 5 Minutes

### Step 1: Clone or Download Project
```bash
cd /path/to/v0-project
```

### Step 2: Install Frontend Dependencies
```bash
npm install
# or
pnpm install
```

### Step 3: Setup Python Backend
```bash
cd backend
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Step 4: Setup Environment Variables
```bash
# Copy environment template
cp .env.local.example .env.local

# Edit .env.local with your settings
# At minimum, set:
# NEXT_PUBLIC_API_URL=http://localhost:5000
```

### Step 5: Start Frontend (Terminal 1)
```bash
npm run dev
# App will be at http://localhost:3000
```

### Step 6: Start Backend (Terminal 2)
```bash
cd backend
python app.py
# API will be at http://localhost:5000
```

### Step 7: Access the Application
- **User Dashboard**: http://localhost:3000/
- **Admin Dashboard**: http://localhost:3000/admin/dashboard
- **API Documentation**: http://localhost:5000/docs

## 📝 Demo Credentials

### User Login
- Email: `user@example.com`
- Password: `password123`

### Admin Login
- Email: `admin@example.com`
- Password: `admin123`

## 🎯 What to Test First

1. **Register a New Account**
   - Go to http://localhost:3000/auth/register
   - Fill in all required fields with test data
   - Aadhaar: Any 12 digits (e.g., `123456789012`)
   - PAN: Format like `ABCDE1234F`
   - Phone: 10 digits (e.g., `9876543210`)

2. **Apply for a Loan**
   - Go to Dashboard → New Loan Application
   - Fill in loan details
   - Click "Get ML Prediction"
   - Review the risk assessment
   - Click "Submit Application"

3. **Check Admin Dashboard**
   - Go to /admin/dashboard
   - Login with admin credentials
   - View all applications
   - See model metrics and risk analysis

## 🛠️ Project Structure

```
v0-project/
├── app/                          # Next.js app directory
│   ├── page.tsx                 # Landing page
│   ├── auth/                    # Authentication pages
│   ├── dashboard/               # User dashboard
│   └── admin/                   # Admin dashboard
├── backend/                      # Flask backend
│   ├── routes/                  # API endpoints
│   ├── models/                  # ML models
│   ├── utils/                   # Utilities
│   ├── dataset/                 # Training data
│   └── app.py                   # Flask app
├── components/                   # React components
├── lib/                         # Utilities and types
│   ├── types.ts                # TypeScript types
│   ├── api.ts                  # API client
│   ├── validators.ts           # Input validation
│   └── auth-context.tsx        # Auth provider
└── public/                      # Static files
```

## 📚 API Endpoints

### Authentication
- `POST /auth/login` - User login
- `POST /auth/register` - User registration
- `POST /auth/logout` - User logout

### Loan Application
- `POST /loan/apply` - Submit loan application
- `GET /loan/applications` - Get user applications
- `GET /loan/applications/{id}` - Get specific application

### ML Predictions
- `POST /ml/predict` - Get ML prediction for loan
- `GET /ml/metrics` - Get model performance metrics
- `POST /ml/batch-predict` - Batch predictions

### Admin
- `GET /admin/dashboard` - Admin dashboard data
- `GET /admin/stats` - Admin statistics
- `GET /admin/applications` - All applications

## 🐛 Troubleshooting

### Backend Not Starting
```bash
# Check if port 5000 is in use
lsof -i :5000  # macOS/Linux
netstat -ano | findstr :5000  # Windows

# Try different port
export FLASK_PORT=5001
```

### Frontend Can't Connect to Backend
```bash
# Check NEXT_PUBLIC_API_URL in .env.local
# Should be: http://localhost:5000

# Clear cache and restart
rm -rf .next
npm run dev
```

### Database Connection Error
```bash
# Check credentials in .env.local
# Ensure MySQL is running and database exists

# Create database
mysql -u root -p -e "CREATE DATABASE loanpredict;"
```

### Import Errors in Backend
```bash
# Activate virtual environment
source backend/venv/bin/activate  # macOS/Linux
backend\venv\Scripts\activate      # Windows

# Reinstall dependencies
pip install -r requirements.txt
```

## 📖 Documentation Files

- `README.md` - Full documentation
- `SYSTEM_COMPLETE.md` - System architecture
- `PROFESSIONAL_FEATURES.md` - Features overview
- `ML_TESTING_GUIDE.md` - ML testing guide
- `BUILDING_GUIDE.md` - Implementation guide

## 🔑 Key Features Implemented

✅ User authentication with JWT  
✅ Loan application form with validation  
✅ ML prediction with 2 models (LR + RF)  
✅ Risk level assessment (Low/Medium/High)  
✅ Admin dashboard with analytics  
✅ Application history and tracking  
✅ Responsive design for all devices  
✅ Type-safe TypeScript code  
✅ Professional banking UI  
✅ Error handling and logging  

## 🚀 Next Steps

1. **Customize**: Modify colors, fonts, and branding
2. **Deploy**: Deploy frontend to Vercel, backend to Heroku/Railway
3. **Database**: Move from SQLite to MySQL/PostgreSQL
4. **Testing**: Run comprehensive test suite
5. **Monitoring**: Set up logging and error tracking

## 💡 Tips

- Check browser console for frontend errors
- Check terminal for backend errors
- Use network tab to debug API calls
- Test with different loan amounts and credit scores
- Try edge cases (very high/low amounts)

## 📞 Support

For issues or questions:
1. Check error messages in console
2. Review documentation files
3. Check API endpoint responses
4. Verify environment variables
5. Ensure database is running

---

**Happy Lending! 🎉**
