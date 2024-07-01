# Django App Boilerplate

## Step 1: Set Up Virtual Environment and Django Project

### Create a Virtual Environment

1. First, ensure you have `virtualenv` installed. If not, you can install it using pip:

    ```sh
    pip install virtualenv
    ```

2. Create a new virtual environment for your Django project. Choose an appropriate directory where you want to create it:

    ```sh
    # Replace 'venv' with your preferred name for the virtual environment
    virtualenv venv
    ```

### Activate the Virtual Environment

3. Activate the virtual environment. This step is platform-specific:

   - **On Windows**:

     ```sh
     venv\Scripts\activate
     ```

   - **On macOS and Linux**:

     ```sh
     source venv/bin/activate
     ```

   Your command prompt should now show the name of the virtual environment (`(venv)` in this case).

### Install Django and Create Project

4. Install Django inside the virtual environment:

    ```sh
    pip install django
    ```

5. Create a new Django project using the `django-admin` command:

    ```sh
    django-admin startproject myproject
    ```

   Replace `myproject` with the name of your project.

6. Move into the project directory:

    ```sh
    cd myproject
    ```

## Step 2: Configure Django Project

### Project Structure

Your project structure should now look something like this:

```
myproject/
├── myproject/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── myapp/
    ├── migrations/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    └── views.py
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
from django.urls import path, include
from django.contrib import admin

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```

### Define App URLs and Views

1. In `myapp/urls.py`, define URLs specific to your app:

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

1. Apply initial migrations to set up your database (SQLite by default):

    ```sh
    python manage.py migrate
    ```

2. Create a superuser to access the Django admin interface (optional):

    ```sh
    python manage.py createsuperuser
    ```

   Follow the prompts to create a superuser account.

3. Start the Django development server:

    ```sh
    python manage.py runserver
    ```

## Step 5: Access the App

Open a web browser and go to `http://localhost:8000/` to see your Django app in action.

### Additional Steps

- **Templates**: Create a `templates/` directory in your app directory (`myapp/templates/`) to store HTML templates.
- **Static Files**: Create a `static/` directory in your app directory (`myapp/static/`) to store CSS, JavaScript, and other static files.

## Step 6: Set Up Git Repository

### Initialize Git Repository

1. Initialize a new Git repository in your project directory (`myproject`):

    ```sh
    git init
    ```

### Create `.gitignore` File

2. Create a `.gitignore` file to specify which files and directories to ignore in version control. Example `.gitignore` for a typical Django project:

    ```plaintext
    # Ignore virtual environment
    venv/

    # Ignore Django media files
    media/

    # Ignore Django static files
    staticfiles/

    # Ignore IDE/Editor specific files
    .vscode/
    .idea/
    *.pyc

    # Ignore local settings
    myproject/settings_local.py
    ```

3. Save the `.gitignore` file in the root of your project directory (`myproject`).

### Commit Initial Changes

4. Add all files to the staging area and commit them:

    ```sh
    git add .
    git commit -m "Initial commit: Setup Django project"
    ```

### Additional Git Configuration (Optional)

5. If you haven't already, set up your Git username and email:

    ```sh
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```

6. Optionally, connect your local repository to a remote repository on GitHub, GitLab, etc., and push your changes:

    ```sh
    git remote add origin <remote_repository_url>
    git push -u origin master
    ```

Replace `<remote_repository_url>` with the URL of your remote Git repository.


## Conclusion

This boilerplate provides a basic structure for starting a Django project and app with a virtual environment. You can expand upon it by adding models, forms, additional views, templates, static files, and more as your project grows. Make sure to refer to the [Django documentation](https://docs.djangoproject.com/en/stable/) for detailed information on each component and for advanced configurations.
