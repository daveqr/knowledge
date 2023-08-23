# Django



## Commands

1. Start the server.

	```bash
	$ python manage.py runserver
	```

2. Update your database when you make changes to your Django models or database schema.

	```bash
	$ python manage.py makemigrations
	$ python manage.py migrate
	```

## Development and Debugging

### Using SQLite3 from the Command Line

SQLite3 is a lightweight, file-based relational database management system. You can interact with SQLite3 databases directly from the command line.

1. Access the shell.
	
	```bash
	$ sqlite3 db.sqlite3		
	```

2. Run database commands.

	```bash
	>>>	.tables
	>>> select * from mytable;
	>>> .exit
	```

### Interactive Python Shell

Run this command to enter an interactive Python shell with the Django project's environment loaded. This allows you to interact with your Django project, its models and libraries in a live environment.

```
$ python manage.py shell
```

Here are some key aspects of the interactive shell:

1. Interactivity: Unlike a regular Python script, which runs and terminates, the Django shell stays open, allowing you to enter multiple Python commands interactively.

1. Access to Django Models: You can access and manipulate Django models, including querying the database, creating, updating, or deleting records. This is particularly useful for testing database interactions and data manipulation.

1. Access to Django Configuration: You can access your project's settings and configurations directly from the shell, which can be helpful for debugging or checking settings.

1. Importing Libraries: You can import and use Python libraries and modules, just like in a regular Python script. This is useful when you need to perform tasks beyond Django's built-in functionality.

1. Debugging: You can use the shell for debugging purposes. For example, you can print variables, test code snippets, and quickly experiment with different parts of your application.


Example usage:

```bash
# Import Django models
from myapp.models import MyModel

# Query the database
my_objects = MyModel.objects.all()

# Create a new object
new_object = MyModel(name="New Object")
new_object.save()

# Access Django settings
from django.conf import settings
print(settings.DEBUG)

# Perform other Python operations and tests
```


### Find the SITE_ID in the database
Inside the database, django has a django_site table with(id, domain, name). This is where django stores the SITE_IDs.

## Project Setup and Cofiguration

### Settings

#### ALLOWED_HOSTS

The ALLOWED_HOSTS setting in Django is a security measure that helps prevent a class of security vulnerabilities known as "Host header attacks." It defines a list of host/domain names or IP addresses that the Django application is allowed to serve. For local development, you can configure it so that requests from your local machine are accepted. It can be set as an environment variable for other environments.

```
# settings.py

ALLOWED_HOSTS = ['localhost', '127.0.0.1']
```
	
It can be set as an environment variable for other environments.

```
# settings.py

import os

# Default value for ALLOWED_HOSTS (for development)
ALLOWED_HOSTS = ['localhost']

# Use the environment variable if it's set
if 'ALLOWED_HOSTS' in os.environ:
    ALLOWED_HOSTS = os.environ['ALLOWED_HOSTS'].split(',')
```	
	
### Find the SITE_ID in the database
Inside the database, django has a django_site table with(id, domain, name). This is where django stores the SITE_IDs.

### Creating an App

In Django, an "app" (short for "application") is a self-contained module or component of a web application that encapsulates specific functionality. Apps are Django's way of organizing code within a project, and they are designed to be reusable and pluggable.

Here's a step-by-step guide to creating a Django app:


1. **Create the App**

    To create a new app, use the following command, replacing `<app_name>` with your desired app name:

    ```bash
    python manage.py startapp <app_name>
    ```

    For example, to create an app named "myapp," you would run:

    ```bash
    python manage.py startapp myapp
    ```

2. **Implement the View (views.py)**

    In your app's `views.py` file, you'll define the views that handle HTTP requests and return responses. Implement the necessary view functions and logic here.

    Example (`views.py`):

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def my_view(request):
        return HttpResponse("Hello, World!")
    ```

3. **Configure URLs (urls.py)**

    Create a `urls.py` file within your app to define the URL patterns for your views. Map URLs to the corresponding view functions.

    Example (`urls.py`):

    ```python
    from django.urls import path
    from . import views

    urlpatterns = [
        path('myapp/', views.my_view, name='my-view'),
    ]
    ```

4. **Add the App to `INSTALLED_APPS` (settings.py)**

    Open your project's `settings.py` file and add your app to the `INSTALLED_APPS` list. This tells Django to include your app in the project.

    Example (`settings.py`):

    ```python
    INSTALLED_APPS = [
        # …
        'myapp',  # Replace 'myapp' with your app's name
    ]
    ```

5. **Run Migrations**

    Migrations are used to apply changes to your database schema. Run the following commands to create and apply migrations:

    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

That's it! You've successfully created a Django app and integrated it into your project.

For more information on Django app development, refer to the [Django documentation](https://docs.djangoproject.com/en/stable/topics/apps/).

## Reset Migrations by Dropping the Database

In certain situations, you may need to reset your database migrations to their initial state. This process involves dropping the existing database and recreating it from scratch.


1. Remove the SQLite3 database file. (If using MySQL or PostgreSQL, manually delete the database and create the DB again.)

	```bash
	$ rm -rf db.sqlite3
	```

2. Create the initial migrations and generate the database schema:

	```bash
	$ python manage.py makemigrations
	$ python manage.py migrate
	```

