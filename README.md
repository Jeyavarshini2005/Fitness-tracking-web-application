# 💪 FitAI – Smart Fitness Tracker

A full-stack fitness tracking application with AI chatbot, streak tracking, batch training, workout flowcharts, diet charts, and daily progress tracking.

## 🗂 Project Structure

```
fitness-app/
├── backend/          # Node.js + Express + MongoDB API
│   ├── models/       # Mongoose data models
│   ├── routes/       # API route handlers
│   ├── middleware/   # Auth middleware (JWT)
│   └── server.js     # Main server entry
└── frontend/         # React.js frontend
    └── src/
        ├── pages/    # Dashboard, Workouts, Diet, Progress, Chatbot, Trainer
        ├── components/ # Layout, Sidebar
        └── context/  # Auth context
```

## ✨ Features

| Feature | Description |
|---|---|
| 🔐 User & Trainer Login | JWT auth with role-based access (user / trainer) |
| 🏋️ Workout Tracking | Create workouts, log exercises, complete sessions |
| 📊 Workout Flowchart | Step-by-step Warm Up → Main → Cool Down → Stretch flow |
| 👥 Batch Training | Trainers assign workouts to multiple users at once |
| 🥗 Diet Chart | Log meals, track macros (protein/carbs/fats), water intake |
| 📈 Progress Tracker | Weight, BMI, body fat, measurements with visual charts |
| 🎯 Goal Progress | Daily % progress toward weight loss/gain goal |
| 🔥 Streak System | Daily login streaks with badges (3, 7, 14, 30 day milestones) |
| 🤖 AI Chatbot | Smart fitness coach powered by rule-based AI (upgrade to Claude API) |
| 🏅 Badges | Earn badges for streak milestones |
| 💾 MongoDB Storage | All gym data stored in MongoDB with full CRUD operations |

## 🚀 Setup & Installation

### Prerequisites
- Node.js v18+
- MongoDB (local or MongoDB Atlas)

### Backend Setup

```bash
cd backend
cp .env.example .env
# Edit .env: set MONGO_URI and JWT_SECRET
npm install
npm run dev
```

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

Frontend runs on **http://localhost:3000**  
Backend API runs on **http://localhost:5000**

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register user/trainer |
| POST | `/api/auth/login` | Login |
| GET | `/api/workouts` | Get all workouts |
| POST | `/api/workouts` | Create workout |
| PUT | `/api/workouts/:id/complete` | Complete workout + update streak |
| GET | `/api/diet/today` | Get today's diet |
| POST | `/api/diet` | Log meals |
| GET | `/api/progress/goal-progress` | Get % progress to goal |
| POST | `/api/progress` | Log body measurements |
| GET | `/api/streak` | Get streak + week activity |
| GET | `/api/trainer/clients` | Get trainer's clients |
| POST | `/api/trainer/assign-workout` | Batch assign workout |
| GET | `/api/trainer/gym-data` | Daily gym attendance data |
| POST | `/api/chatbot/message` | AI coach response |

## 🗄 MongoDB Collections

- **users** – Profile, goals, streak, badges, role
- **workouts** – Exercises, sets/reps, completion, batch group
- **diets** – Meals, macros, calories, water intake
- **progresses** – Weight, measurements, BMI, sleep, steps, mood

## 🤖 Upgrading the AI Chatbot to Claude API

Replace the rule-based responses in `backend/routes/chatbot.js` with:

```javascript
const Anthropic = require('@anthropic-ai/sdk');
const client = new Anthropic({ apiKey: process.env.ANTHROPIC_API_KEY });

const message = await client.messages.create({
  model: 'claude-opus-4-6',
  max_tokens: 500,
  system: 'You are a professional fitness coach...',
  messages: [{ role: 'user', content: userMessage }]
});
```

## 🛠 Tech Stack

- **Frontend**: React.js, React Router, Recharts, Axios
- **Backend**: Node.js, Express.js
- **Database**: MongoDB + Mongoose
- **Auth**: JWT (JSON Web Tokens) + bcrypt
- **Charts**: Recharts (Line, Area, Bar, Pie)

## 👨‍💻 Created For Final Year Project
