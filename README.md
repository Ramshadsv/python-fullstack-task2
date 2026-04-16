# Flask User Authentication System
### Python Full Stack Web Development – Task 2 | Maincrafts Technology

---

## 📌 Project Overview
This project implements a complete **User Authentication System** using Flask — including user registration, login, session management, protected routes, and logout functionality.

---

## 🛠️ Tech Stack
| Layer | Technology |
|---|---|
| Backend | Python + Flask |
| Frontend | HTML + CSS |
| Database | SQLite |
| Security | Werkzeug Password Hashing |
| Sessions | Flask built-in session |

---

## 📁 Project Structure
```
python-fullstack-task2/
├── app.py               ← Core Flask application
├── database.db          ← SQLite database (auto-created on first run)
├── README.md            ← This file
├── templates/
│   ├── register.html    ← Registration page
│   ├── login.html       ← Login page
│   └── dashboard.html   ← Protected dashboard page
└── static/
    └── style.css        ← Application styles
```

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/python-fullstack-task2.git
cd python-fullstack-task2
```

### 2. Install required packages
```bash
pip install flask werkzeug
```

### 3. Run the application
```bash
python app.py
```

### 4. Open in browser
```
http://127.0.0.1:5000/register
```

---

## 🔐 Authentication Flow

```
User → /register → Hash password → Save to DB → Redirect to /login
User → /login → Lookup in DB → Verify hash → Set session → /dashboard
User → /dashboard → Check session → Show page (or redirect to /login)
User → /logout → Clear session → Redirect to /login
```

### Step-by-step explanation:

1. **Register**: User submits username + password. The password is hashed using `generate_password_hash()` from Werkzeug and stored in SQLite. Plain-text passwords are NEVER stored.

2. **Login**: User submits credentials. The app fetches the user from the DB and uses `check_password_hash()` to verify. If valid, `session['user']` is set.

3. **Dashboard (Protected Route)**: The view checks `if 'user' not in session` — if no session exists, the user is redirected to login. This enforces access control.

4. **Logout**: `session.pop('user', None)` clears the session, effectively logging the user out and redirecting to login.

---

## 🔒 Security Concepts Learned

- **Password Hashing**: Werkzeug's `generate_password_hash` uses PBKDF2-SHA256 — a one-way cryptographic function. Passwords cannot be reversed.
- **Session-based Authentication**: Flask signs the session cookie with `app.secret_key`. Tampering is detected automatically.
- **Protected Routes**: Any route can be protected by checking `session['user']` and redirecting unauthorized users.
- **Secure Logout**: Clearing the session on logout prevents session reuse.

---

## 📸 Screenshots
*(Add your screenshots here after running the project)*
- `screenshots/register.png`
- `screenshots/login.png`
- `screenshots/dashboard.png`

---

## 👤 Author
**Intern Name**: Mohammed Rishan  
**Program**: Python Full Stack Web Development  
**Organization**: Maincrafts Technology  
**Task**: Task 2 — User Authentication System
# python-fullstack-task2
