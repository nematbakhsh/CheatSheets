# Django App Boilerplate
> [!NOTE]  
> Django version 5.0.6.

## Step 1: Set Up Virtual Environment and Django Project

### Create a Virtual Environment

Choose an appropriate directory where you want to create it:

```sh
# Create a new virtual environment
python3 -m venv 'venv' # Replace 'venv' with your preferred virtual environment name 

# Activate the virtual environment
venv\Scripts\activate # On Windows
source venv/bin/activate # On macOS and Linux
```
Your command prompt should now show the name of the virtual environment (`(venv)` in this case).

### Install Django and Create Project

```sh
pip install --upgrade pip
# Install Django inside the virtual environment
pip install django
# Create a new Django project
django-admin startproject myproject # Replace `myproject` with the name of your project
cd myproject
python manage.py startapp myapp # Replace `myapp` with your preferred name for the application
code .
```

## Step 2: Configure Django Project

### Project Structure

Your project structure should now look something like this:

```
myproject/            # Root directory of your Django project
│
├── manage.py         # Command-line utility for administrative tasks
│
├── myproject/        # Django project settings and configuration directory
│   ├── __init__.py   # An empty file that tells Python this directory should be considered a Python package
│   ├── settings.py   # Project settings and configuration
│   ├── urls.py       # URL routing configuration for the project
│   ├── wsgi.py       # WSGI config for deployment (Web Server Gateway Interface)
│   └── asgi.py       # ASGI config for deployment (Asynchronous Server Gateway Interface)
│
└── myapp/            # Example Django app directory (you can have multiple apps)
    ├── migrations/  # Database migrations for this app
    ├── __init__.py  # Package initializer
    ├── admin.py     # Django admin configuration for this app
    ├── apps.py      # AppConfig for this app
    ├── models.py    # Database models for this app
    ├── tests.py     # Unit tests for this app
    ├── views.py     # Views (controller logic) for this app
    ├── urls.py      # URL routing for this app
    └── templates/   # HTML templates for this app

```

### Configure Settings

In `myproject/settings.py`, configure your Django project settings. Some common settings to configure include:

```python
DEBUG = True
ALLOWED_HOSTS = ['localhost', '127.0.0.1']
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',  # Add your app here
]
```

## Step 3: Define URLs and Views

### Define Project URLs

In `myproject/urls.py`, define your project-level URLs:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('myapp', include('myapp.urls')), # use `''` if this is your main app
]
```

### Define App URLs and Views

1. In `myapp/urls.py` (cretae it!), define URLs specific to your app:

    ```python
    from django.urls import path
    from . import views

    urlpatterns = [
        path('', views.index, name='index'),
        # Add more paths as needed
    ]
    ```

2. In `myapp/views.py`, define your views (controller logic):

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, world. You're at the index.")
    ```

## Step 4: Run Migrations and Start Server

```sh
python manage.py migrate # Apply initial migrations to set up your database (SQLite by default)
python manage.py createsuperuser # Create a superuser to access the Django admin interface (optional)
python manage.py runserver [8000] # Start the Django development server
```

## Step 5: Access the App

Open a web browser and go to `http://localhost:8000/myapp` to see your Django app in action.

### Additional Steps

- **Templates**: Create a `templates/` directory in your app directory (`myapp/templates/`) to store HTML templates.
- **Static Files**: Create a `static/` directory in your app directory (`myapp/static/`) to store CSS, JavaScript, and other static files.

## Step 6: Set Up Git Repository

### Create `.gitignore` File

Create a `.gitignore` file to specify which files and directories to ignore in version control and place it in the root directory. Example `.gitignore` for a typical Django project:

    ```plaintext
    # Ignore virtual environment
    venv/

    # Ignore Django media files
    media/

    # Ignore Django static files
    staticfiles/
    static/

    # Ignore IDE/Editor specific files
    .vscode/
    .idea/
    *.pyc

    # Ignore local settings
    myproject/settings_local.py
    ```
    
### Initialize Git Repository and First Commit

Initialize a new Git repository in your project directory (`myproject`):

```sh
cd .. # Go to main directory (with 'venv' folder) I find it good practice to initialize there
echo "# MyProject" >> README.md
git init
git config [--global] user.name "Your Name"
git config [--global] user.email "your.email@example.com"
git add .
git commit -m "Initial commit: Setup Django project"
git branch -M main
git remote add origin <remote-repository-url> # Replace `<remote_repository_url>` with the URL of your remote Git repository
git push -u origin main
```
## Step 7: Configure an IDE (vscode)

```sh
mkdir .vscode
cd .vscode
touch settings.json
```

### Create the `settings.json` file
```json
{
    "python.defaultInterpreterPath": "${workspaceFolder}/venv/bin/python", // on linux
    // "python.defaultInterpreterPath": "${workspaceFolder}/venv/Scripts/python.exe", // on windows
    "python.terminal.activateEnvironment": true,
    "python.envFile": "${workspaceFolder}/.env"
}
```

### Verify Python Interpreter in VSCode:

To ensure that VSCode is using the correct Python interpreter from your virtual environment:

1. Open the Command Palette:
    Press Ctrl+Shift+P (Windows/Linux) or Cmd+Shift+P (macOS) to open the Command Palette.

2. Select Python Interpreter:
    Type Python: Select Interpreter and select it from the dropdown.

3. Choose the Interpreter:
    You should see a list of available Python interpreters. Look for the one that points to your virtual environment (e.g., ${workspaceFolder}/venv/bin/python or ${workspaceFolder}/venv/Scripts/python.exe) and select it.

4. Relaunch your terminal
    
## Conclusion

This boilerplate provides a basic structure for starting a Django project and app with a virtual environment. You can expand upon it by adding models, forms, additional views, templates, static files, and more as your project grows. Make sure to refer to the [Django documentation](https://docs.djangoproject.com/en/stable/) for detailed information on each component and for advanced configurations.
