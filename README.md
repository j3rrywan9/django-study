# Learning Django

## Checking Django version
```
python -c "import django; print(django.get_version())"
```

## Creating a project
```
django-admin startproject mysite
```

## Database setup
```
python manage.py migrate
```
The **migrate** command looks at the **INSTALLED_APPS** setting and creates any necessary database tables according to the database settings in your **mysite/settings.py** file and the database migrations shipped with the app.

You can show a list of all known migrations and which are applied using
```
python manage.py migrate --list
```

## The development server
```
python manage.py runserver
```
You've started the Django development server, a lightweight Web server written purely in Python.

## Creating models
Create an app called "polls":
```
python manage.py startapp polls
```
The first step in writing a database Web app in Django is to define your models - essentially, your database layout, with additional metadata.

Each model is represented by a class that subclasses **django.db.models.Models**. Each model has a number of class variables, each of which represents a database field in the model.

Each field is represented by an instance of a **Field** class. This tells Django what type of data each field holds.

## Activating models
First tell the project that the **polls** app is installed.

Edit the **mysite/settings.py** file again, and change the **INSTALLED_APPS** setting to include the string **'polls'**.

```
python manage.py makemigrations polls
```
By running **makemigrations**, you're telling Django that you've made some changes to your models and that you'd like the changes to be stored as a *migration*.

Migrations are how Django stores changes to your models (and thus your database schema) - they're just files on disk. You can read the migration for your new model if you like; it's the file **polls/migrations/0001_initial.py**.

There's a command that you will run the migrations for you and manage your database schema automatically - that's called **migrate**.

Let's see what SQL that migration would run. The **sqlmigrate** command takes migration names and returns their SQL:
```
python manage.py sqlmigrate polls 0001
```
Table names are automatically generated by combining the name of the app (**polls**) and the lowercase name of the model - **question** and **choice**. (You can override this behavior.)

The **sqlmigrate** command doesn't actually run the migration on your database - it just prints it to the screen so that you can see what SQL Django thinks is required.

Now, run **migrate** again to create those model tables in your database:
```
python manage.py migrate
```
The **migrate** command takes all the migrations that haven't been applied (Django tracks which ones are applied using a special table in your database called **django_migration**) and runs them against your database - essentially, synchonizing the changes you made to your models with the schema in the database.
