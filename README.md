# 🎓 EduManager: Premium Student Management System

EduManager is a robust, modern, and comprehensive **Student Management System** designed to streamline academic operations for schools, super administrators, school admins, teachers, and students. Built with a high-performance **FastAPI backend** (Python) and a dynamic **Angular 17 frontend** (TypeScript & Bootstrap), EduManager offers school management, attendance tracking, grading systems, user role permissions, and rich dashboard analytics.

---

## 🌟 What is a `.md` (Markdown) File?
A **Markdown (`.md`)** file is a lightweight document formatting standard used globally by developers. On **GitHub**, when you place a file named `README.md` in the root folder of your project, GitHub automatically renders it as the **homepage** of your repository. 

### Why is this file important for your project?
1. **First Impression:** Anyone who visits your GitHub repo or downloads your Google Drive folder sees this page first. It introduces your project beautifully.
2. **Setup Instructions:** It gives clear, step-by-step guidance on how to install and run your backend and frontend.
3. **Viva / Presentation Prep:** If you are presenting this project to your professor, examiner ("Sir"), or classmates, this file acts as your ultimate documentation and quick reference sheet.

---

## 🚀 Key Features

*   **Multi-Tenant Architecture:** Super Admins can manage multiple schools under different subscription plans.
*   **Role-Based Access Control (RBAC):** Custom interfaces and page-access rules for **Super Admins**, **School Admins**, **Teachers**, and **Students**.
*   **Academic Workflows:** Create and manage Courses, assign Teachers, and enroll Students.
*   **Attendance Management:** Track daily attendance status (Present, Absent, Late, Excused) with detailed remarks.
*   **Gradebook & Marks Tracker:** Log exam scores, calculate letter grades, and track progress.
*   **Analytics Dashboard:** Interactive dashboard widgets displaying school counts, attendance percentages, grade summaries, and reports.
*   **Database Fallback:** Intelligent auto-fallback to a local SQLite database (`sms_db.sqlite`) if a PostgreSQL connection is not found.

---

## 🛠️ Technology Stack

| Layer | Technology | Description / Usage |
| :--- | :--- | :--- |
| **Frontend** | Angular 17, TypeScript, Bootstrap, Bootstrap Icons | Provides a responsive, sleek, and animated single-page application (SPA). |
| **Backend** | FastAPI, Uvicorn | High-performance, asynchronous REST API serving JSON payloads at `http://localhost:3001`. |
| **Database ORM** | SQLAlchemy | Maps pythonic classes directly to relational database tables. |
| **Data Validation** | Pydantic v2 | Standardizes and validates input/output JSON schemas. |
| **Security** | JWT (JSON Web Tokens), `python-jose`, `passlib` (Bcrypt) | Secure password hashing and authorization token mechanics. |
| **Database** | PostgreSQL / SQLite | Tries connecting to PostgreSQL first. Safely falls back to SQLite file `backend/sms_db.sqlite` automatically. |

---

## 📁 Project Directory Structure

```text
student-mangment/
├── backend/
│   ├── main.py                  # FastAPI application entry point & CORS configuration
│   ├── database.py              # Engine setup, DB Session creation & Fallback handler
│   ├── models.py                # SQLAlchemy model classes (User, School, Student, Teacher, etc.)
│   ├── schemas.py               # Pydantic validation schemas for API inputs/outputs
│   ├── auth_utils.py            # Password cryptography and JWT generation helpers
│   ├── seed.py                  # Script to seed default database tables and dummy data
│   ├── create_user.py           # Helper script to create a standalone student account
│   ├── routers/                 # Modularized API routing endpoints
│   │   ├── auth.py
│   │   ├── schools.py
│   │   ├── users.py
│   │   ├── students.py
│   │   ├── teachers.py
│   │   ├── courses.py
│   │   ├── attendance.py
│   │   ├── grades.py
│   │   └── analytics.py
│   ├── requirements.txt         # Backend Python packages
│   ├── run_server.bat           # Quick batch script to launch FastAPI server
│   └── sms_db.sqlite            # Local SQLite database file
│
└── frontend/
    ├── src/
    │   ├── app/
    │   │   ├── core/            # API Services, Auth interceptors, guards & logic
    │   │   │   ├── api.service.ts
    │   │   │   └── auth.service.ts
    │   │   └── pages/           # Angular components (login, dashboard, students, teachers, etc.)
    │   └── environments/        # Environment configurations (API URL definitions)
    ├── package.json             # Frontend script triggers & dependencies
    └── angular.json             # Angular Workspace configuration
```

---

## ⚙️ How to Setup and Run the Project

Follow these steps to run both backend and frontend on your computer:

### 1️⃣ Backend Setup
1. Open a command prompt or terminal window.
2. Navigate to the `backend` folder:
   ```bash
   cd backend
   ```
3. (Optional but Recommended) Create and activate a Python virtual environment:
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```
4. Install all required Python packages:
   ```bash
   pip install -r requirements.txt
   ```
5. **Seed the database** with sample demo data (this creates schools, admin, teachers, and students automatically):
   ```bash
   python seed.py
   ```
6. Start the server using the quick batch file or directly via uvicorn:
   ```bash
   # Run batch file:
   run_server.bat

   # Or run directly:
   uvicorn main:app --reload --port 3001
   ```
   *The backend REST API will run at **`http://localhost:3001`**.*
   *Interactive API Documentation (Swagger UI) is available at **`http://localhost:3001/docs`**.*

---

### 2️⃣ Frontend Setup
1. Open a **new** command prompt or terminal window (keep the backend terminal running!).
2. Navigate to the `frontend` folder:
   ```bash
   cd frontend
   ```
3. Install all frontend dependencies:
   ```bash
   npm install
   ```
4. Run the Angular development server:
   ```bash
   npm start
   # Or:
   ng serve --port 4200
   ```
5. Open your web browser and go to:
   **`http://localhost:4200`**

---

## 👥 Seed Accounts (Default Login Credentials)

When you run `python seed.py`, the system creates the following pre-configured accounts for testing and demonstration:

| Role | Email | Password | Details |
| :--- | :--- | :--- | :--- |
| **Super Admin** | `admin@edumanager.com` | `admin123` | Can create/manage new schools and view global analytics. |
| **School Admin** | `principal@dps.edu.in` | `school123` | Manages students, teachers, courses, and schedules for "Delhi Public School". |
| **Teacher** | `anita.sharma@dps.edu.in` | `teacher123` | Enters attendance, submits grades, and manages academic student details. |
| **Student** | `rahul.verma@dps.edu.in` | `student123` | Logged-in profile representing a Class 10-A student. |

---

## 🔄 How the Frontend Connects to the Backend

EduManager implements a modern, decoupled client-server architecture:

```text
[ Browser / Angular Frontend ] (Port 4200)
             │
             ▼ (Sends JSON via HTTP Requests)
   [ FastAPI REST API ] (Port 3001)
             │
             ▼ (Fetches / Stores via SQLAlchemy ORM)
[ Relational DB: PostgreSQL / SQLite ]
```

1. **API URL:** Defined globally in `frontend/src/environments/environment.ts` as `http://localhost:3001/api`.
2. **API Calls:** Managed by `frontend/src/app/core/api.service.ts` using Angular's `HttpClient`. For instance, calling `getStudents()` sends an HTTP `GET` request to `http://localhost:3001/api/students`.
3. **Backend Route Handler:** FastAPI intercepts this request in `backend/routers/students.py` at `@router.get("")`, requests data from the database using SQLAlchemy, and returns structured JSON back to Angular.
4. **Data Binding:** Angular processes the JSON payload, assigns it to a TypeScript model, and automatically updates the template table using the `*ngFor` directive.

---

## 🎓 Guide: How to Explain this Project to "Sir" (Vivas / Presentations)

When explaining this project to your examiner or supervisor, use this script as a confident outline:

> *"Good morning Sir. I have developed a Student Management System named **EduManager**. This is a full-stack web application designed with a decoupled architecture.*
>
> *For the **Backend API**, I used **Python FastAPI** and **SQLAlchemy ORM**. I chose FastAPI because it is extremely fast, provides automatic OpenAPI validation, and auto-generates interactive Swagger documentation at `/docs` which speeds up testing. The backend manages authentication via **JWT tokens** and connects to a **PostgreSQL database**. If PostgreSQL is offline, it has a built-in fallback mechanic that automatically writes to a local **SQLite database** to prevent any data loss or application downtime.*
>
> *For the **Frontend Application**, I utilized **Angular 17** combined with **Bootstrap** for a highly responsive, modern, and beautiful design. We have clear role-based access control. A Super Admin can manage various schools, a School Admin manages administrative tasks, Teachers handle grades and attendance, and Students can track their academic performance.*
>
> *Communication between Angular and FastAPI is done completely through secure **REST APIs** using JSON as the data transfer format. The frontend stores user auth tokens in LocalStorage to maintain a secure session state."*

---

## ☁️ How to upload this project to Google Drive or GitHub

### 📂 Preparing for Google Drive Upload
If you plan to zip the folder and upload it to Google Drive, **make sure to delete heavy dependency folders** first to save upload time and bandwidth!

1. Delete the `node_modules` folder inside the `frontend` directory. (Whoever downloads it can just run `npm install` to get it back).
2. Delete the Python virtual environment folder `venv` inside the `backend` directory. (Whoever downloads it can run `pip install -r requirements.txt` to re-create it).
3. Right-click the main `student mangment` folder ➡️ **Send to** ➡️ **Compressed (zipped) folder**.
4. Upload the resulting `.zip` file to your Google Drive and share the download link!

### 🐙 Uploading to GitHub
1. Open Git Bash or a terminal in the root folder (`student mangment`).
2. Initialize a git repository:
   ```bash
   git init
   ```
3. Create a `.gitignore` file (or make sure you have it) to exclude `node_modules`, `venv`, and binary databases. (Angular has one pre-configured in `frontend/.gitignore`).
4. Add all files:
   ```bash
   git add .
   ```
5. Commit files:
   ```bash
   git commit -m "Initial commit: EduManager Student Management System"
   ```
6. Create a new repository on your GitHub account (do not add a README, license, or gitignore there).
7. Copy the remote repository link from GitHub, then run:
   ```bash
   git remote add origin <YOUR_GITHUB_REPOSITORY_URL>
   git branch -M main
   git push -u origin main
   ```

---

*Made with 💖 by [Yash](https://github.com/your-username)*
