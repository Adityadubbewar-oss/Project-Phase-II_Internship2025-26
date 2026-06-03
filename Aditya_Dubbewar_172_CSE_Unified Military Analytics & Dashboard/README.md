# Unified Military Analytics Dashboard

Unified Military Analytics Dashboard is a comprehensive web application designed to visualize, compare, and analyze military data. Built with a robust Flask backend and an interactive frontend, it provides deep insights into military capabilities, inequalities, and various metrics across different nations.

## 🚀 Features

- **Interactive Dashboard**: Rich visualizations and data representations of global military analytics.
- **Admin Panel & Database Management**: Secure admin tools to manage the underlying dataset (`admin_db.html`, `admin.html`).
- **User Authentication**: Secure login system with `Flask-Login` and hashed passwords (`login.html`).
- **Feedback System**: Collect insights and feedback from users (`feedback.html`).
- **RESTful API**: Structured backend routes returning JSON and rendering data for the frontend dashboards.
- **SQLite Database**: Lightweight, file-based database for seamless data storage out-of-the-box.

## 🛠️ Technology Stack

- **Backend**: Python 3.10+, Flask, Flask-SQLAlchemy, Flask-Login, Pandas
- **Frontend**: HTML5, CSS3, JavaScript (Vanilla JS for dashboard logic)
- **Database**: SQLite (Development), configurable for PostgreSQL (Production)

## 📁 Project Structure

```text
Unified-Military-Analytics/
├── backend/                  # Flask Backend application logic
│   ├── app.py                # Main Flask application and routes
│   └── requirements.txt      # Backend dependencies
├── frontend/                 # Frontend assets and templates
│   ├── static/               # CSS, JavaScript, and Images
│   │   ├── css/              # Stylesheets (dashboard_native.css)
│   │   ├── js/               # Frontend logic (dashboard_logic.js)
│   │   └── images/           # Static assets
│   └── templates/            # HTML templates (Jinja2)
│       ├── base.html         # Base layout template
│       ├── home.html         # Landing page
│       ├── dashboard.html    # Main analytics dashboard
│       ├── login.html        # User login
│       ├── admin.html        # Admin interface
│       ├── admin_db.html     # Admin database viewer
│       ├── feedback.html     # Feedback form
│       └── about.html        # About page
├── instance/                 # SQLite database storage (database.db)
├── api/                      # Additional API integrations (index.py)
├── requirements.txt          # Root project dependencies
└── pythonanywhere_deployment.md  # Guide for deploying to PythonAnywhere
```

## 💻 Local Development Setup

Follow these steps to run the project locally on your machine.

### 1. Clone the repository
```bash
git clone https://github.com/Adityadubbewar-oss/Unified-Military-Analytics.git
cd Unified-Military-Analytics
```

### 2. Create a Virtual Environment (Optional but recommended)
```bash
python -m venv venv

# Activate on Windows:
venv\Scripts\activate

# Activate on macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the Application
Start the Flask server by running the main `app.py` script from the root directory:
```bash
python backend/app.py
```
The application will be available at `http://127.0.0.1:5000`.

## 🌐 Deployment

This project includes a comprehensive deployment guide for hosting the application on PythonAnywhere for free. 
Please refer to the [pythonanywhere_deployment.md](./pythonanywhere_deployment.md) file for step-by-step instructions.

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 📝 License
This project is open-source and available under the MIT License.
