# 🎓 EduManager: Student Management System

EduManager is a full-stack **Student Management System** featuring a high-performance **FastAPI backend** (Python) and a dynamic **Angular 17 frontend** (TypeScript & Bootstrap). It provides school administration, role-based access (Admins, Teachers, Students), attendance tracking, grade sheets, and analytical dashboards.

---
# Download from Google Drive

[![Google Drive](https://www.vectorlogo.zone/logos/google_drive/google_drive-icon.svg)](https://drive.google.com/drive/folders/1y2a6i0q7E4LjIDoBE2dKO7ktv7DnSIi1?usp=drive_link)

---

# Download from Google Drive

[![Google Drive](https://upload.wikimedia.org/wikipedia/commons/0/0b/Google_Drive_icon_%282026%29.svg)](https://drive.google.com/uc?export=download&id=YOUR_FILE_ID)


### 🚀 Quick Setup & Run Guide

#### 1️⃣ Backend API Setup (`/backend`)
```bash
# Navigate & Install dependencies
cd backend
pip install -r requirements.txt

# Seed the database (creates schools, default users & dummy data)
python seed.py

# Run the FastAPI server
run_server.bat
```
*API runs at **`http://localhost:3001`**. Swagger docs open at **`http://localhost:3001/docs`**.*

#### 2️⃣ Frontend Setup (`/frontend`)
```bash
# Navigate & Install dependencies
cd frontend
npm install

# Run the Angular dev server
npm start
```
*Web application runs at **`http://localhost:4200`**.*

---

### 👥 Seed Login Accounts (Default Credentials)

| Role | Email | Password | Details |
| :--- | :--- | :--- | :--- |
| **Super Admin** | `admin@edumanager.com` | `admin123` | Global analytics and school registration |
| **School Admin** | `principal@dps.edu.in` | `school123` | Manage teachers, students, and courses |
| **Teacher** | `anita.sharma@dps.edu.in` | `teacher123` | Mark attendance and record exam grades |
| **Student** | `rahul.verma@dps.edu.in` | `student123` | Personal academic and attendance dashboard |


---

*Made with 💖 by [Yash](https://github.com/your-username)*
