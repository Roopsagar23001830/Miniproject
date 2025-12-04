<<<<<<< HEAD
# 🚌 Real-Time Bus Tracking Management System (SEC)
A smart, real-time GPS-based solution that tracks and monitors college buses through a live dashboard. This system enhances student safety and transport efficiency using real-time bus location updates, alerts, and route monitoring.

## 🌟 Overview
This project uses GPS + cloud technologies to:
Track bus location in real-time
Show bus routes & stop-wise ETA
Provide a web dashboard for students & admins
Send notifications for delays, breakdowns, or route changes
Maintain student & bus data with secure authentication
No manual tracking needed — just live updates from the bus to the screen.

## 🧠 Features
Live map with bus markers
ETA calculation for each stop
Student login & assigned bus view
Admin panel for bus, route & student management
Notification & feedback management
Firebase real-time location updates
Secure DB for student transport records

## 🔧 Tech Stack
### Backend
 FastAPI / Flask
 Python
 SQLAlchemy ORM
 Firebase Realtime Database
 JWT Authentication (optional)
### Frontend
 Streamlit (Admin Panel)
 React + Vite + TailwindCSS (Student/Parent UI)
 Google Maps API / LeafletJS
### GPS + Realtime Layer
 IoT/GPS Device or Simulation Script
 Firebase sync for instant map update

## 🚀 Getting Started
### 1️⃣ Clone the Repository
````git clone https://github.com/yourusername/real-time-bus-tracking.git
cd real-time-bus-tracking
````

## 🖥️ Backend Setup
### 2️⃣ Install Dependencies
``` pip install -r requirements.txt ```
Example requirements:
fastapi
uvicorn
sqlalchemy
firebase-admin
python-dotenv
streamlit
pydantic

### 3️⃣ Setup Environment Variables
``` Create .env: ```
``` DATABASE_URL=sqlite:///./bus_tracking.db
FIREBASE_KEY_PATH=/absolute/path/firebase-key.json
FIREBASE_DATABASE_URL=https://your-app.firebaseio.com
```
### 4️⃣ Initialize Database
```python
from database import init_db
init_db()
```
### 5️⃣ Run Backend API
```
uvicorn main_auth:app --reload
```
Runs at:
```
http://127.0.0.1:8000
```
### 🎛️ Admin Panel (Streamlit)
Runs at:
```
http://localhost:8501
```
#### Allows managing:
 Students
 Buses
 Live Location Updates
 Feedback
 Notifications

### 🛰️ Bus GPS Simulator (for Testing)
```python
from time import sleep
from firebase import update_bus_location

BUS_NUMBER = "SEC_01"
route = [(13.0827, 80.2707), (13.0700, 80.2400), (13.0500, 80.2300)]

while True:
    for lat, lng in route:
        update_bus_location(BUS_NUMBER, lat, lng, speed=40)
        print("Location Updated:", lat, lng)
        sleep(5)
```

### 🌐 Frontend (React Dashboard)
```
cd frontend
npm install
npm run dev
```

Runs at:
```
http://localhost:5173/
```
#### User View:
 Live Map + Bus Tracking
 ETA + Stop Information
 Notifications
 Feedback Form

### 📡 API Endpoints
#### Authentication
```
POST /api/auth/login
```
#### Bus Routes & Tracking
```
 GET  /api/buses
 GET  /api/buses/{bus_number}
 GET  /api/buses/{bus_number}/location
 POST /api/buses/{bus_number}/location   # GPS device update
```
#### Student Transport Data
```
GET /api/students/{id}/assigned-bus
```
#### Feedback Management
```
   POST /api/feedback
   GET  /api/feedback
```
#### Sample location update payload:
```json
{
  "latitude": 13.0827,
  "longitude": 80.2707,
  "speed": 38.2,
  "timestamp": 1735902301.12
}
```
### 🗂️ Folder Structure
```pgsql
real-time-bus-tracking-system/
├── backend/
│   ├── main_auth.py
│   ├── database.py
│   ├── firebase.py
│   ├── routers/
│   ├── schemas/
│   └── services/
├── admin_panel/
│   └── admin_interface.py
├── gps_simulator/
│   └── gps_sim.py
├── frontend/
│   ├── src/
│   ├── public/
│   └── package.json
├── docs/
│   └── screenshots/
└── README.md
```

### 🛣️ Roadmap
 RFID student attendance
 Push notifications (SMS/WhatsApp)
 Over-speeding and route deviation alerts
 AI-based ETA prediction
 Native Mobile App (Flutter)

