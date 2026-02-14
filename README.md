🌟 Overview
Trithon is a dual-product AI platform addressing critical gaps in Indian healthcare and education sectors:
MedQueue AI - Hospital Queue & Bed Predictor
EduMatch AI - Personalized Career Counselor
📋 Table of Contents
Products
MedQueue AI
EduMatch AI
Tech Stack
Project Structure
Getting Started
Installation
Configuration
Development
Deployment
API Documentation
Contributing
License
🏥 Products
🏥 MedQueue AI
Problem: Patients waste 3-5 hours in hospital queues; emergency patients visit 4-5 hospitals before finding beds.
Solution: AI-powered platform providing:
Real-time queue status with ML-based wait time predictions
Live bed availability across multiple hospitals
Virtual queue booking system
LLM-powered symptom checker
Surge prediction alerts for hospitals
Ambulance routing integration
Impact:
85% reduction in average wait time
75% reduction in hospital search time for emergencies
40,000+ lives saved annually (projected)
Revenue Model:
Hospital subscriptions: ₹15K-50K/month
Patient booking fees: ₹20-50/slot
Government analytics contracts
24-month target: ₹40-60 lakhs
🎓 EduMatch AI
Problem: 90% of tier-2/3 students lack career counseling; 40% college dropout rate.
Solution: LLM-powered career guidance platform with:
AI-driven aptitude and personality assessments
Personalized career roadmaps
College and scholarship matching
24/7 AI mentor chatbot
Success probability predictions
Parent dashboard
Impact:
50,000+ students guided in 24 months
60% improvement in career-course alignment
₹500 crores in scholarships unlocked
Revenue Model:
Student subscriptions: ₹999-2,999
College partnerships: ₹50K-2L/year
School white-label: ₹1-3L/year
24-month target: ₹60-90 lakhs
🛠 Tech Stack
Frontend
{
  "framework": "React 18 + TypeScript",
  "styling": "Tailwind CSS + shadcn/ui",
  "state": "Zustand",
  "routing": "React Router v6",
  "maps": "Google Maps API / Mapbox GL JS",
  "charts": "Recharts",
  "forms": "React Hook Form + Zod",
  "realtime": "Socket.io-client",
  "mobile": "React Native",
  "build": "Vite"
}
Backend
{
  "runtime": "Node.js 20 LTS",
  "framework": "Express.js / Fastify",
  "language": "TypeScript",
  "database": {
    "primary": "Firebase Firestore",
    "realtime": "Firebase Realtime Database",
    "cache": "Redis",
    "vector": "Pinecone (for AI embeddings)"
  },
  "ml": {
    "framework": "Python (FastAPI)",
    "libraries": ["TensorFlow", "scikit-learn", "XGBoost", "Prophet"]
  },
  "llm": {
    "providers": ["OpenAI GPT-4", "Anthropic Claude"],
    "framework": "LangChain"
  },
  "queue": "Bull (Redis-based)",
  "auth": "Firebase Authentication"
}
Infrastructure
Cloud: Google Cloud Platform / AWS
Hosting: Firebase Hosting (frontend), Cloud Run (backend)
CI/CD: GitHub Actions
Monitoring: Sentry, Firebase Performance
Payments: Razorpay
📁 Project Structure
trithon/
├── apps/
│   ├── medqueue-patient-web/       # MedQueue patient web app
│   ├── medqueue-patient-mobile/    # MedQueue mobile app (React Native)
│   ├── medqueue-admin/             # Hospital admin dashboard
│   ├── medqueue-ambulance/         # Ambulance driver app
│   ├── medqueue-government/        # Government portal
│   ├── edumatch-student-web/       # EduMatch student platform
│   ├── edumatch-student-mobile/    # EduMatch mobile app
│   ├── edumatch-school/            # School admin portal
│   └── edumatch-college/           # College partner portal
│
├── services/
│   ├── core-api/                   # Main API service (Node.js)
│   │   ├── src/
│   │   │   ├── routes/
│   │   │   ├── controllers/
│   │   │   ├── services/
│   │   │   ├── middleware/
│   │   │   └── models/
│   │   └── package.json
│   │
│   ├── ml-service/                 # Python ML service
│   │   ├── app/
│   │   │   ├── models/
│   │   │   │   ├── wait_time_predictor.py
│   │   │   │   ├── surge_predictor.py
│   │   │   │   ├── career_matcher.py
│   │   │   │   └── success_predictor.py
│   │   │   └── routes/
│   │   └── requirements.txt
│   │
│   ├── llm-service/                # LLM service (Python)
│   │   ├── app/
│   │   │   ├── chains/
│   │   │   │   ├── symptom_checker.py
│   │   │   │   └── career_mentor.py
│   │   │   └── prompts/
│   │   └── requirements.txt
│   │
│   └── routing-service/            # Ambulance routing (Node.js)
│
├── firebase-functions/             # Firebase Cloud Functions
│   ├── src/
│   │   ├── triggers/
│   │   ├── scheduled/
│   │   └── callable/
│   └── package.json
│
├── shared/                         # Shared code
│   ├── types/
│   ├── utils/
│   └── constants/
│
├── docs/                           # Documentation
│   ├── PRD_MedQueue.md
│   ├── PRD_EduMatch.md
│   ├── API_DOCS.md
│   └── ARCHITECTURE.md
│
├── docker-compose.yml              # Local development
├── package.json                    # Root package.json
└── README.md                       # This file
🚀 Getting Started
Prerequisites
Node.js: 20.x or higher
Python: 3.11 or higher
Firebase Account: Set up Firebase project
Google Cloud Account: For Maps API
Redis: For caching and queues
Git: Latest version
Quick Start
# Clone the repository
git clone https://github.com/iamgulu74/trithon.git
cd trithon

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your credentials

# Start development servers
npm run dev
📦 Installation
1. Clone Repository
git clone https://github.com/iamgulu74/trithon.git
cd trithon
2. Install Node.js Dependencies
# Install root dependencies
npm install

# Install app-specific dependencies
cd apps/medqueue-patient-web && npm install && cd ../..
cd apps/edumatch-student-web && npm install && cd ../..

# Install service dependencies
cd services/core-api && npm install && cd ../..
3. Install Python Dependencies
# ML Service
cd services/ml-service
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
cd ../..

# LLM Service
cd services/llm-service
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cd ../..
4. Set Up Firebase
# Install Firebase CLI
npm install -g firebase-tools

# Login to Firebase
firebase login

# Initialize Firebase
firebase init

# Select services:
# ✓ Firestore
# ✓ Functions
# ✓ Storage
# ✓ Hosting
5. Set Up Redis
# Using Docker
docker run -d -p 6379:6379 redis:7-alpine

# Or install locally (macOS)
brew install redis
brew services start redis

# Or install locally (Ubuntu)
sudo apt-get install redis-server
sudo systemctl start redis
⚙️ Configuration
Environment Variables
Create .env files in respective directories:
Root .env
# Node Environment
NODE_ENV=development

# Firebase
FIREBASE_PROJECT_ID=your-project-id
FIREBASE_API_KEY=your-api-key
FIREBASE_AUTH_DOMAIN=your-project.firebaseapp.com
FIREBASE_STORAGE_BUCKET=your-project.appspot.com
FIREBASE_MESSAGING_SENDER_ID=123456789
FIREBASE_APP_ID=1:123456789:web:abc123

# Google Services
GOOGLE_MAPS_API_KEY=your-maps-api-key
GOOGLE_SPEECH_API_KEY=your-speech-api-key

# Redis
REDIS_URL=redis://localhost:6379

# ML Service
ML_SERVICE_URL=http://localhost:8001

# LLM Service
LLM_SERVICE_URL=http://localhost:8002
OPENAI_API_KEY=your-openai-key
ANTHROPIC_API_KEY=your-anthropic-key

# Payments
RAZORPAY_KEY_ID=your-razorpay-key
RAZORPAY_KEY_SECRET=your-razorpay-secret

# SMS/Email
TWILIO_ACCOUNT_SID=your-twilio-sid
TWILIO_AUTH_TOKEN=your-twilio-token
SENDGRID_API_KEY=your-sendgrid-key
ML Service .env (services/ml-service/.env)
PORT=8001
FIREBASE_CREDENTIALS_PATH=./serviceAccountKey.json
MODEL_PATH=./models
REDIS_URL=redis://localhost:6379
LLM Service .env (services/llm-service/.env)
PORT=8002
OPENAI_API_KEY=your-openai-key
ANTHROPIC_API_KEY=your-anthropic-key
PINECONE_API_KEY=your-pinecone-key
PINECONE_ENVIRONMENT=us-west1-gcp
FIREBASE_CREDENTIALS_PATH=./serviceAccountKey.json
Firebase Configuration
Download service account key from Firebase Console
Save as serviceAccountKey.json in:
services/core-api/
services/ml-service/
services/llm-service/
firebase-functions/
Update Firestore security rules:
firebase deploy --only firestore:rules
Create Firestore indexes:
firebase deploy --only firestore:indexes
🛠 Development
Run All Services (Development Mode)
# Start all services concurrently
npm run dev
This will start:
MedQueue Patient Web: http://localhost:3000
EduMatch Student Web: http://localhost:3001
Core API: http://localhost:5000
ML Service: http://localhost:8001
LLM Service: http://localhost:8002
Run Individual Services
# MedQueue Patient Web
cd apps/medqueue-patient-web
npm run dev

# Core API
cd services/core-api
npm run dev

# ML Service
cd services/ml-service
uvicorn app.main:app --reload --port 8001

# LLM Service
cd services/llm-service
uvicorn app.main:app --reload --port 8002

# Firebase Functions (local emulator)
cd firebase-functions
npm run serve
Testing
# Run all tests
npm test

# Run tests for specific app
cd apps/medqueue-patient-web
npm test

# Run E2E tests
npm run test:e2e

# Run ML model tests
cd services/ml-service
pytest tests/
Linting & Formatting
# Lint all code
npm run lint

# Format code
npm run format

# Type check
npm run type-check
🚢 Deployment
Production Build
# Build all apps
npm run build

# Build specific app
cd apps/medqueue-patient-web
npm run build
Deploy to Firebase
# Deploy everything
firebase deploy

# Deploy specific services
firebase deploy --only hosting
firebase deploy --only functions
firebase deploy --only firestore:rules
Deploy Backend Services
Using Docker
# Build Docker images
docker-compose build

# Push to registry
docker-compose push

# Deploy to Cloud Run (GCP)
gcloud run deploy core-api \
  --source services/core-api \
  --region us-central1 \
  --allow-unauthenticated

gcloud run deploy ml-service \
  --source services/ml-service \
  --region us-central1 \
  --allow-unauthenticated
Using Kubernetes
# Apply Kubernetes configs
kubectl apply -f k8s/

# Check deployment status
kubectl get pods
kubectl get services
Environment-Specific Deployment
# Deploy to staging
firebase use staging
firebase deploy

# Deploy to production
firebase use production
firebase deploy
📚 API Documentation
MedQueue API Endpoints
Hospitals
GET    /api/hospitals                    # Search hospitals
GET    /api/hospitals/:id                # Hospital details
GET    /api/hospitals/:id/beds           # Bed availability
GET    /api/hospitals/:id/queue          # Queue status
GET    /api/hospitals/:id/predict-wait   # Wait time prediction
Bookings
POST   /api/bookings                     # Create booking
GET    /api/bookings/my-bookings         # User's bookings
POST   /api/bookings/:id/check-in        # Check-in
POST   /api/bookings/:id/cancel          # Cancel booking
GET    /api/bookings/:id/queue-position  # Live queue position
Symptom Checker
POST   /api/symptom-checker/start        # Start session
POST   /api/symptom-checker/message      # Chat with AI
GET    /api/symptom-checker/:id/assessment  # Get assessment
EduMatch API Endpoints
Students
POST   /api/students/register            # Register student
GET    /api/students/profile             # Get profile
PUT    /api/students/profile             # Update profile
Assessments
GET    /api/assessments                  # List assessments
POST   /api/assessments/:id/start        # Start test
POST   /api/assessments/:id/submit       # Submit answers
GET    /api/assessments/:id/results      # Get results
Career Matching
POST   /api/career/match                 # AI career matching
GET    /api/career/:id/roadmap           # Generate roadmap
GET    /api/career/:id/success-probability  # ML prediction
Full API Documentation: See API_DOCS.md
🧪 Testing
Unit Tests
# Run all unit tests
npm test

# Run with coverage
npm run test:coverage

# Watch mode
npm run test:watch
Integration Tests
# Run integration tests
npm run test:integration

# Test specific service
cd services/core-api
npm run test:integration
E2E Tests (Cypress)
# Open Cypress
npm run test:e2e:open

# Run headless
npm run test:e2e:run
ML Model Testing
cd services/ml-service

# Run model tests
pytest tests/test_models.py

# Test with coverage
pytest --cov=app tests/
🔧 Troubleshooting
Common Issues
Issue: Firebase authentication not working
# Solution: Check Firebase config
firebase login
firebase projects:list
firebase use <project-id>
Issue: Redis connection refused
# Solution: Start Redis
docker run -d -p 6379:6379 redis:7-alpine
# Or
redis-server
Issue: ML models not loading
# Solution: Download pre-trained models
cd services/ml-service
python scripts/download_models.py
Issue: Port already in use
# Find process using port
lsof -i :3000
# Kill process
kill -9 <PID>
🤝 Contributing
We welcome contributions! Please follow these steps:
Fork the repository
Create a feature branch
git checkout -b feature/amazing-feature
Commit your changes
git commit -m 'Add amazing feature'
Push to the branch
git push origin feature/amazing-feature
Open a Pull Request
Coding Standards
TypeScript: Follow TypeScript Style Guide
Python: Follow PEP 8
Commits: Use Conventional Commits
Testing: Maintain 80%+ code coverage
Development Workflow
Pick an issue from GitHub Issues
Comment on the issue to get assigned
Create a branch from main
Write code with tests
Submit PR with description
Address review comments
Merge after approval
📊 Project Status
Current Version: v1.0.0-beta
Roadmap
Q1 2026 (Jan-Mar)
[x] MedQueue MVP (patient web app)
[x] EduMatch MVP (student platform)
[ ] Mobile apps (React Native)
[ ] Deploy to 5 pilot hospitals
[ ] Onboard 2,000 students
Q2 2026 (Apr-Jun)
[ ] Advanced ML models (95%+ accuracy)
[ ] Multi-language support (Hindi, Tamil, etc.)
[ ] 10 hospitals live
[ ] 5 school partnerships
Q3 2026 (Jul-Sep)
[ ] Government portal launch
[ ] 50 hospitals across 3 cities
[ ] 10,000 students
[ ] Revenue: ₹15-20 lakhs
Q4 2026 (Oct-Dec)
[ ] Pan-India expansion
[ ] 100+ hospitals
[ ] 25,000 students
[ ] Revenue: ₹40-60 lakhs
📈 Metrics & Analytics
MedQueue Metrics
Wait Time Reduction: Target 85%
Bed Search Time: < 10 minutes
Patient Satisfaction: > 4.5/5
Prediction Accuracy: > 95%
EduMatch Metrics
Student Satisfaction: > 4.5/5
Career-Course Match: > 85%
Scholarship Placement: > 15%
Roadmap Completion: > 50%
Track live metrics at: https://analytics.trithon.ai
🔐 Security
Reporting Vulnerabilities
Please report security vulnerabilities to: security@trithon.ai
Security Measures
Firebase Authentication with JWT
HTTPS/TLS encryption
Input validation and sanitization
Rate limiting on APIs
Regular security audits
GDPR & data privacy compliance
🙏 Acknowledgments
Firebase team for excellent documentation
OpenAI/Anthropic for LLM APIs
Google Maps team
All open-source contributors
Our pilot hospitals and schools
Beta testing users
📚 Additional Resources
Product Requirements: PRD_MedQueue.md | PRD_EduMatch.md
Architecture: ARCHITECTURE.md
API Docs: API_DOCS.md
Firebase Guide: FIREBASE_GUIDE.md
Deployment Guide: DEPLOYMENT.md
🌟 Star History
�
Load image
Made with ❤️ in India | Solving Real Problems with AI
Quick Commands Cheatsheet
# Development
npm run dev                 # Start all services
npm test                    # Run tests
npm run lint                # Lint code
npm run format              # Format code

# Build & Deploy
npm run build               # Build all apps
firebase deploy             # Deploy to Firebase
docker-compose up           # Run with Docker

# Database
firebase emulators:start    # Start Firebase emulators
firebase firestore:delete   # Delete Firestore data

# Monitoring
npm run logs                # View logs
npm run monitor             # Monitor services
