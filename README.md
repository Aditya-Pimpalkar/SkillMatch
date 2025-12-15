# SkillMatch - AI-Powered Collaboration Platform by Aditya

<div align="center">

![SkillMatch Logo](https://via.placeholder.com/150x150/6366f1/ffffff?text=SkillMatch)

**Connect with people who have complementary skills and shared interests**

[![React Native](https://img.shields.io/badge/React_Native-0.74-61dafb?style=flat&logo=react)](https://reactnative.dev/)
[![Expo](https://img.shields.io/badge/Expo-51.0-000020?style=flat&logo=expo)](https://expo.dev/)
[![Flask](https://img.shields.io/badge/Flask-3.0-000000?style=flat&logo=flask)](https://flask.palletsprojects.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791?style=flat&logo=postgresql)](https://www.postgresql.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.3-3178c6?style=flat&logo=typescript)](https://www.typescriptlang.org/)

</div>

## 📋 Overview

SkillMatch is a full-stack mobile application that uses AI to match users based on their skills and interests. Built with React Native and Flask, it demonstrates modern mobile development practices with real-time data fetching, AI integration, and professional UI/UX design.

### ✨ Key Features

- 🤖 **AI-Powered Matching**: Uses OpenAI GPT-4 to analyze compatibility between users
- 🎯 **Smart Algorithm**: Considers complementary skills, shared interests, and learning opportunities
- 📊 **Detailed Analysis**: Get AI-generated insights on collaboration potential
- 📱 **Cross-Platform**: Works on iOS and Android via React Native
- 🔄 **Real-Time Updates**: TanStack Query for efficient data synchronization
- 🎨 **Modern UI**: Built with NativeWind (Tailwind CSS for React Native)

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      Mobile App (Expo)                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │    Home      │  │   Matches    │  │   Settings   │      │
│  │   Screen     │  │    Screen    │  │    Screen    │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│           │                 │                 │              │
│           └─────────────────┴─────────────────┘              │
│                             │                                │
│                   ┌─────────▼─────────┐                      │
│                   │  TanStack Query   │                      │
│                   │   (Data Layer)    │                      │
│                   └─────────┬─────────┘                      │
│                             │                                │
│                   ┌─────────▼─────────┐                      │
│                   │  Axios API Client │                      │
│                   └─────────┬─────────┘                      │
└─────────────────────────────┼─────────────────────────────────┘
                              │ HTTPS
                              │
┌─────────────────────────────▼─────────────────────────────────┐
│                     Flask REST API                            │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │
│  │    Users     │  │   Matches    │  │    Stats     │       │
│  │  Endpoints   │  │  Endpoints   │  │  Endpoints   │       │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘       │
│         │                 │                 │                │
│         └─────────────────┴─────────────────┘                │
│                           │                                  │
│                 ┌─────────▼─────────┐                        │
│                 │   SQLAlchemy ORM  │                        │
│                 └─────────┬─────────┘                        │
│                           │                                  │
│          ┌────────────────┼────────────────┐                 │
│          │                │                │                 │
│   ┌──────▼──────┐  ┌──────▼──────┐  ┌──────▼──────┐         │
│   │  PostgreSQL │  │   OpenAI    │  │   Caching   │         │
│   │  Database   │  │  GPT-4 API  │  │   Layer     │         │
│   └─────────────┘  └─────────────┘  └─────────────┘         │
└─────────────────────────────────────────────────────────────┘
```

## 🛠️ Tech Stack

### Frontend
- **React Native** 0.74 - Cross-platform mobile framework
- **Expo** 51.0 - Development platform and toolchain
- **TypeScript** 5.3 - Type-safe JavaScript
- **Expo Router** 3.5 - File-based routing
- **TanStack React Query** 5.17 - Data fetching and caching
- **NativeWind** 4.0 - Tailwind CSS for React Native
- **Axios** 1.6 - HTTP client

### Backend
- **Flask** 3.0 - Python web framework
- **PostgreSQL** - Relational database
- **SQLAlchemy** 3.1 - Python ORM
- **OpenAI API** - GPT-4 for AI matching
- **Flask-CORS** - Cross-origin resource sharing
- **Gunicorn** - Production WSGI server

## 📦 Installation

### Prerequisites

- **Node.js** 18+ and npm/yarn
- **Python** 3.11+
- **PostgreSQL** 14+
- **OpenAI API Key** ([Get one here](https://platform.openai.com/api-keys))
- **Expo Go** app on your phone (iOS/Android)

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/skillmatch.git
cd skillmatch
```

### 2. Backend Setup

```bash
# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Create .env file
cp .env .env

# Edit .env and add your credentials:
# - DATABASE_URL: Your PostgreSQL connection string
# - OPENAI_API_KEY: Your OpenAI API key
# - SECRET_KEY: A random secret key

# Initialize database
python run.py
# This will create all necessary tables
```

### 3. Frontend Setup

```bash
# Open a new terminal and navigate to frontend
cd frontend

# Install dependencies
npm install
# or
yarn install

# Update API_BASE_URL in services/api.ts
# Replace 'http://localhost:5000/api' with your local IP
# Example: 'http://192.168.1.100:5000/api'
# To find your IP:
# - macOS: ifconfig | grep "inet " | grep -v 127.0.0.1
# - Windows: ipconfig
# - Linux: ip addr show
```

### 4. Start the Application

**Terminal 1 - Backend:**
```bash
cd backend
source venv/bin/activate  # or venv\Scripts\activate on Windows
python run.py
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm start
# or
expo start
```

**On Your Phone:**
1. Install Expo Go from App Store (iOS) or Play Store (Android)
2. Scan the QR code shown in your terminal
3. Wait for the app to load

## 🚀 Usage

### Creating a Profile

1. Open the app and navigate to the **Home** tab
2. Fill in your details:
   - Name and email
   - Bio (optional)
   - Skills (e.g., "React", "Python", "UI Design")
   - Interests (e.g., "AI", "Mobile Apps", "Startups")
3. Click **Create Profile**
4. Save your User ID for later use

### Finding Matches

1. Navigate to the **Matches** tab
2. Enter your User ID
3. Click the search icon
4. Click **Generate New Matches** to find compatible users
5. Browse your matches sorted by compatibility score
6. Tap any match to view detailed analysis

### Viewing Match Details

Each match shows:
- **Compatibility Score**: AI-calculated percentage
- **AI Analysis**: Detailed reasoning for the match
- **Complementary Skills**: Skills that complement each other
- **Shared Interests**: Common ground for collaboration
- **Collaboration Potential**: What you could build together
- **Learning Opportunities**: What each person can learn

## 📡 API Documentation

### Base URL
```
http://localhost:5000/api
```

### Endpoints

#### Users

**Create User**
```http
POST /users
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "bio": "Full-stack developer passionate about AI",
  "skills": ["React", "Python", "PostgreSQL"],
  "interests": ["AI", "Mobile Apps", "Cloud Computing"]
}
```

**Get All Users**
```http
GET /users?limit=50&offset=0
```

**Get User by ID**
```http
GET /users/{user_id}
```

**Update User**
```http
PUT /users/{user_id}
Content-Type: application/json

{
  "bio": "Updated bio",
  "skills": ["React", "Python", "Docker"]
}
```

**Delete User**
```http
DELETE /users/{user_id}
```

#### Matches

**Get User Matches**
```http
GET /users/{user_id}/matches
```

**Find New Matches**
```http
POST /users/{user_id}/find-matches?limit=10
```

**Get Match by ID**
```http
GET /matches/{match_id}
```

**Delete Match**
```http
DELETE /matches/{match_id}
```

#### Utility

**Health Check**
```http
GET /health
```

**Get Stats**
```http
GET /stats
```

## 🌐 Deployment

### Backend Deployment (Railway)

1. **Create a Railway account** at [railway.app](https://railway.app)

2. **Install Railway CLI:**
```bash
npm i -g @railway/cli
```

3. **Deploy:**
```bash
railway login
cd backend
railway init
railway up
```

4. **Add PostgreSQL:**
   - Go to your Railway dashboard
   - Click "New" → "Database" → "PostgreSQL"
   - Railway will automatically set DATABASE_URL

5. **Set Environment Variables:**
   - Go to your project → Variables
   - Add:
     - `OPENAI_API_KEY`: Your OpenAI API key
     - `SECRET_KEY`: Random secret key
     - `FLASK_ENV`: production

6. **Get your deployment URL** from Railway dashboard

### Backend Deployment (Render)

1. **Create account** at [render.com](https://render.com)
2. Click **New** → **Web Service**
3. Connect your GitHub repository
4. Configure:
   - **Name**: skillmatch-api
   - **Environment**: Python
   - **Build Command**: `cd backend && pip install -r requirements.txt`
   - **Start Command**: `cd backend && gunicorn -b 0.0.0.0:$PORT run:app`
5. Add environment variables in the dashboard
6. Deploy!

### Database Setup (Supabase)

1. **Create account** at [supabase.com](https://supabase.com)
2. Create a new project
3. Go to **Settings** → **Database**
4. Copy the connection string
5. Use it as your `DATABASE_URL`

### Frontend Configuration

Update `frontend/services/api.ts`:
```typescript
const API_BASE_URL = 'https://your-backend-url.railway.app/api';
```

## 🗂️ Project Structure

```
skillmatch/
├── backend/
│   ├── app/
│   │   ├── __init__.py          # Flask app factory
│   │   ├── config.py            # Configuration
│   │   ├── models.py            # SQLAlchemy models
│   │   ├── routes.py            # API endpoints
│   │   └── services/
│   │       ├── __init__.py
│   │       └── ai_matcher.py    # AI matching logic
│   ├── requirements.txt         # Python dependencies
│   ├── run.py                   # Application entry point
│   └── .env.example             # Environment template
├── frontend/
│   ├── app/
│   │   ├── (tabs)/              # Tab navigation screens
│   │   │   ├── index.tsx        # Home/Profile screen
│   │   │   ├── matches.tsx      # Matches list screen
│   │   │   ├── settings.tsx     # Settings screen
│   │   │   └── _layout.tsx      # Tab layout
│   │   ├── match/
│   │   │   └── [id].tsx         # Match detail screen
│   │   └── _layout.tsx          # Root layout
│   ├── components/              # Reusable components
│   ├── services/
│   │   └── api.ts               # API client
│   ├── types/
│   │   └── index.ts             # TypeScript types
│   ├── package.json             # Node dependencies
│   ├── tsconfig.json            # TypeScript config
│   ├── tailwind.config.js       # Tailwind config
│   └── app.json                 # Expo config
├── .gitignore
├── railway.toml                 # Railway deployment
├── Procfile                     # Heroku/Render deployment
└── README.md                    # This file
```

## 🧪 Testing the API

You can test the API using curl or Postman:

```bash
# Health check
curl http://localhost:5000/api/health

# Create a user
curl -X POST http://localhost:5000/api/users \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Alice Smith",
    "email": "alice@example.com",
    "skills": ["Python", "Machine Learning"],
    "interests": ["AI", "Data Science"]
  }'

# Get all users
curl http://localhost:5000/api/users

# Find matches for user ID 1
curl -X POST http://localhost:5000/api/users/1/find-matches?limit=5
```

## 🐛 Troubleshooting

### Backend Issues

**Database connection error:**
- Verify PostgreSQL is running: `pg_isready`
- Check DATABASE_URL in `.env`
- Ensure database exists

**OpenAI API error:**
- Verify your API key is valid
- Check you have credits available
- Ensure internet connection

**Port already in use:**
```bash
# Find process using port 5000
lsof -i :5000
# Kill the process
kill -9 <PID>
```

### Frontend Issues

**Can't connect to backend:**
- Use your local IP address, not `localhost`
- Ensure backend is running
- Check firewall settings
- Verify phone and computer are on same WiFi

**Expo Go not loading:**
- Clear Expo cache: `expo start -c`
- Restart Metro bundler
- Check for JavaScript errors in terminal

**Styling not working:**
- Ensure NativeWind is installed correctly
- Check `global.css` is imported in `_layout.tsx`
- Restart development server

## 📚 Learning Resources

- [React Native Docs](https://reactnative.dev/docs/getting-started)
- [Expo Documentation](https://docs.expo.dev/)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [TanStack Query](https://tanstack.com/query/latest)
- [NativeWind](https://www.nativewind.dev/)
- [OpenAI API](https://platform.openai.com/docs)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- OpenAI for the GPT-4 API
- Expo team for the amazing development experience
- TanStack for React Query
- All open-source contributors

## 📧 Contact



---

<div align="center">
Made with ❤️ and ☕ | SkillMatch © 2024
</div>
