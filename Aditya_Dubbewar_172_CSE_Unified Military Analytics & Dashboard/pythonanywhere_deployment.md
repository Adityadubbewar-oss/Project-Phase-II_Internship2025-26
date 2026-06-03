# Deployment Guide: PythonAnywhere & GitHub

This guide covers how to push your local code to your GitHub account and then deploy the application on PythonAnywhere.

---

## Part 1: Pushing Code to GitHub

GitHub no longer accepts account passwords for pushing code via the command line. You must use a **Personal Access Token (PAT)**. 

### Step 1: Create a Personal Access Token
1. Go to your GitHub account: [https://github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token (classic)**.
3. Give it a note (e.g., "Deployment Token").
4. Select the **repo** scope (this gives full control of private and public repositories).
5. Click **Generate token** at the bottom.
6. **Copy this token immediately** (it will start with `ghp_` or similar) — you won't be able to see it again!

### Step 2: Create a Repository on GitHub
1. Go to GitHub and click the `+` icon at the top right -> **New repository**.
2. Name it `Unified-Military-Analytics` (or similar).
3. Do **not** initialize it with a README, .gitignore, or license (leave those unchecked).
4. Click **Create repository**.

### Step 3: Push Your Local Code
I have already initialized your local code as a Git repository and committed your files. Now, run the following commands in your terminal (make sure you are in the project folder):

```bash
git remote add origin https://github.com/Adityadubbewar-oss/Unified-Military-Analytics.git
git branch -M main
git push -u origin main
```
> **IMPORTANT:**
> When prompted for your username, enter: `Adityadubbewar-oss`
> When prompted for your password, **paste the Personal Access Token (PAT)** you generated in Step 1. Do NOT use your regular GitHub password `Adityad2004`.

---

## Part 2: Deploying to PythonAnywhere

Once your code is on GitHub, follow these steps to host it on PythonAnywhere for free.

### Step 1: Set Up PythonAnywhere Account
1. Create a free "Beginner" account at [PythonAnywhere](https://www.pythonanywhere.com/).
2. Once logged in, go to the **Consoles** tab and start a new **Bash** console.

### Step 2: Clone Your Code
In the PythonAnywhere Bash console, clone your GitHub repository:
```bash
git clone https://github.com/Adityadubbewar-oss/Unified-Military-Analytics.git
```

### Step 3: Create a Virtual Environment
Still in the Bash console, run:
```bash
mkvirtualenv --python=/usr/bin/python3.10 myenv
cd Unified-Military-Analytics
pip install -r requirements.txt
```
> **NOTE:**
> Make sure `requirements.txt` contains all your necessary libraries (like `Flask`, `Flask-SQLAlchemy`, `pandas`).

### Step 4: Configure the Web App
1. Go to the **Web** tab in PythonAnywhere and click **Add a new web app**.
2. Click **Next**, then select **Manual configuration** (do NOT select Flask).
3. Select **Python 3.10**.
4. Click **Next** to finish creating the app.

### Step 5: Update the WSGI Configuration
1. Still on the **Web** tab, scroll down to the **Code** section.
2. Click the link next to **WSGI configuration file** (it will look like `/var/www/yourusername_pythonanywhere_com_wsgi.py`).
3. Delete everything in that file and paste the following:

```python
import sys
import os

# 1. Add your project directory to the sys.path
path = '/home/YOUR_USERNAME/Unified-Military-Analytics'
if path not in sys.path:
    sys.path.insert(0, path)

# 2. Add the backend folder to sys.path so it can find app.py
backend_path = os.path.join(path, 'backend')
if backend_path not in sys.path:
    sys.path.insert(0, backend_path)

# 3. Import your Flask app
from backend.app import app as application
```
> **WARNING:**
> Replace `YOUR_USERNAME` with your actual PythonAnywhere username!
4. Save the file (top right corner).

### Step 6: Link the Virtual Environment
1. Go back to the **Web** tab.
2. Scroll down to the **Virtualenv** section.
3. Enter the path to your virtual environment: `/home/YOUR_USERNAME/.virtualenvs/myenv` (Replace `YOUR_USERNAME`).

### Step 7: Launch the Site
1. Scroll to the top of the **Web** tab and click the large green **Reload** button.
2. Click your PythonAnywhere URL (e.g., `http://yourusername.pythonanywhere.com`). Your app should now be live!
