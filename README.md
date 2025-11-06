# Sudo Admin Panel - How to Run

## Prerequisites

Before running the project, ensure you have the following installed:

- Python 3.8 or higher
- pip (Python package installer)
- Firebase Admin SDK credentials (configured in views.py)

## Installation & Setup

### Step 1: Navigate to Project Directory

```bash
cd /Users/muhmammedaslamt/Documents/GitHub/sudo_admin
```

### Step 2: Install Dependencies

Install all required Python packages:

```bash
pip3 install -r requirements.txt
```

Or if using a virtual environment:

```bash
# Create virtual environment (optional but recommended)
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate  # On macOS/Linux
# OR
venv\Scripts\activate  # On Windows

# Install dependencies
pip install -r requirements.txt
```

### Step 3: Verify Django Installation

Check if Django is properly installed:

```bash
python3 manage.py check
```

You should see: `System check identified no issues (0 silenced).`

## Running the Development Server

### Basic Run Command

```bash
python3 manage.py runserver
```

The server will start on: **http://127.0.0.1:8000/**

### Run on Specific Port

```bash
python3 manage.py runserver 8080
```

Server will run on: **http://127.0.0.1:8080/**

### Run on All Interfaces (Network Access)

```bash
python3 manage.py runserver 0.0.0.0:8000
```

Server will be accessible from other devices on your network.

## Accessing the Admin Panel

### 1. Open Browser

Navigate to: **http://127.0.0.1:8000/**

### 2. Login Page

Go to: **http://127.0.0.1:8000/login/**

### 3. Admin Credentials

You need to have an admin user in Firebase with:
- `roleId = 1` (Admin role)
- Valid email and password

## Common Commands

### Check for Errors

```bash
python3 manage.py check
```

### View Django Version

```bash
python3 manage.py version
```

### Create Database Migrations (if using SQLite)

```bash
python3 manage.py makemigrations
python3 manage.py migrate
```

### Run in Background (Linux/macOS)

```bash
nohup python3 manage.py runserver > server.log 2>&1 &
```

### Stop the Server

Press `Ctrl + C` in the terminal where the server is running.

## Troubleshooting

### Issue: ModuleNotFoundError

**Problem**: Missing Python packages

**Solution**:
```bash
pip3 install -r requirements.txt
```

### Issue: Port Already in Use

**Problem**: Port 8000 is already in use

**Solution**: Use a different port
```bash
python3 manage.py runserver 8080
```

### Issue: Firebase Connection Error

**Problem**: Firebase credentials not configured

**Solution**: Check `admin_app/views.py` for Firebase configuration

### Issue: Import Errors

**Problem**: Missing dependencies

**Solution**:
```bash
# Install missing packages
pip3 install qrcode cloudinary firebase-admin django
```

## Project Structure

```
sudo_admin/
├── manage.py              # Django management script
├── requirements.txt       # Python dependencies
├── admin_app/            # Main admin application
│   ├── views.py          # View functions
│   ├── urls.py           # URL routing
│   ├── templates/        # HTML templates
│   └── static/           # Static files (CSS, JS)
├── sudo_admin/           # Project settings
│   ├── settings.py       # Django settings
│   └── urls.py           # Main URL configuration
└── landing/              # Landing page app
```

## Available Endpoints

Once the server is running, you can access:

- **Dashboard**: http://127.0.0.1:8000/dashboard/
- **Login**: http://127.0.0.1:8000/login/
- **Generate QR**: http://127.0.0.1:8000/generate-qr/
- **Manage Users**: http://127.0.0.1:8000/manage-users/
- **Manage QRs**: http://127.0.0.1:8000/manage-qrs/
- **View Orders**: http://127.0.0.1:8000/view-orders/
- **Flowchart**: http://127.0.0.1:8000/flowchart/

## Features

- ✅ Rate Limiting System (4 calls/day, 5 push notifications/day)
- ✅ QR Code Generation
- ✅ User Management
- ✅ Order Management
- ✅ Push Notifications (FCM)
- ✅ Phone Calls (Twilio)
- ✅ SMS Notifications (Twilio)

## Development Tips

1. **Enable Debug Mode**: Already enabled in `settings.py` (DEBUG = True)
2. **Check Logs**: Server logs appear in the terminal
3. **Hot Reload**: Django automatically reloads on code changes
4. **Static Files**: Ensure static files are collected if deploying

## Production Deployment

For production deployment:

1. Set `DEBUG = False` in `settings.py`
2. Configure `ALLOWED_HOSTS`
3. Set up proper secret keys
4. Use a production WSGI server (Gunicorn)
5. Configure reverse proxy (Nginx)
6. Set up SSL certificates

## Support

For issues or questions:
- Check the terminal for error messages
- Review Django logs
- Verify Firebase connection
- Check Firestore collections

---

**Last Updated**: January 2025

