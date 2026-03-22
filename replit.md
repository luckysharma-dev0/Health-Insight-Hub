# HealthMate AI Pro - Workspace

## Overview

Full-stack AI healthcare web application — a complete intelligent healthcare ecosystem built with React, Vite, Express, and PostgreSQL.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Auth**: bcryptjs + JWT (jsonwebtoken)
- **Frontend**: React + Vite + Tailwind CSS + Framer Motion + Recharts
- **Build**: esbuild (CJS bundle)

## Application Features

1. **Auth System**: JWT-based login/register with bcrypt password hashing, role-based (patient/doctor/admin)
2. **Dashboard**: Health score, appointments, payment dues, notifications
3. **Physical Health / Symptom Checker**: AI disease prediction with probability scores, lab test recommendations
4. **Mental Health Chatbot**: Sentiment analysis, emotion detection, mood tracking, therapy suggestions, voice input
5. **Drug Risk Predictor**: Drug interaction analysis, risk level assessment
6. **Doctors & Specialists**: Doctor listing with filters, specialist recommendation based on disease
7. **Appointments**: Book/cancel appointments, Pay Now or Postpaid
8. **Payments**: Payment history, postpaid credit system, dues tracking
9. **Health Reports**: Generate and download PDF health reports
10. **Notifications**: Payment due reminders, appointment alerts
11. **Admin/Doctor Panel**: Stats dashboard, manage appointments, doctors, users, health trends analytics
12. **User Profile**: Edit profile, health history

## Structure

```text
artifacts-monorepo/
├── artifacts/
│   ├── api-server/           # Express API backend
│   └── healthmate/           # React + Vite frontend
├── lib/
│   ├── api-spec/             # OpenAPI spec + Orval codegen config
│   ├── api-client-react/     # Generated React Query hooks
│   ├── api-zod/              # Generated Zod schemas
│   └── db/                   # Drizzle ORM schema + DB connection
├── scripts/                  # Utility scripts
└── pnpm-workspace.yaml
```

## Database Schema

- **users**: id, email, password_hash, name, age, gender, role, blood_group, allergies, chronic_conditions, is_verified
- **doctors**: id, name, specialty, rating, fee, distance, location, available, experience, qualifications
- **appointments**: id, user_id, doctor_id, appointment_date, time_slot, status, fee, payment_status
- **payments**: id, user_id, appointment_id, amount, type, status, due_date
- **credit_scores**: id, user_id, credit_score, credit_limit, used_credit, payment_history
- **health_records**: id, user_id, symptoms, predictions, overall_risk_level, physical_score
- **chat_messages**: id, user_id, role, content, sentiment, emotion, mood_score
- **health_reports**: id, user_id, title, mental_score, physical_score, overall_score, risk_level
- **notifications**: id, user_id, type, title, message, is_read

## API Routes

- `/api/auth/register` - Register new user
- `/api/auth/login` - Login
- `/api/auth/doctor/login` - Doctor/Admin login
- `/api/users/profile` - Get/update user profile
- `/api/users/health-score` - Get health score
- `/api/predict/disease` - AI disease prediction
- `/api/predict/drug-risk` - Drug risk analysis
- `/api/predict/credit-score` - Get credit score
- `/api/chat/message` - Send mental health chat
- `/api/chat/history` - Get chat history
- `/api/chat/mood-history` - Get mood tracking
- `/api/doctors` - List/create doctors
- `/api/doctors/recommend` - Recommend specialist
- `/api/appointments` - Book/list appointments
- `/api/payments` - Payment management
- `/api/reports` - Health reports
- `/api/notifications` - Notifications
- `/api/admin/stats` - Admin stats

## Environment Variables

- `DATABASE_URL` - PostgreSQL connection (auto-provided by Replit)
- `JWT_SECRET` - JWT signing secret (set for production)
- `PORT` - Server port (auto-assigned)

## Default Accounts

To test as admin: register with `role: "admin"`
To test as doctor: register with `role: "doctor"`
