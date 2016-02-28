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
