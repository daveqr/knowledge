# Django Development and Debugging

## Using SQLite3 from the Command Line

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

## Interactive Python Shell

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


## Find the SITE_ID in the database
Inside the database, django has a django_site table with(id, domain, name). This is where django stores the SITE_IDs.