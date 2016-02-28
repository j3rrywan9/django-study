# Learning Django

## Checking Django version
```python
python -c "import django; print(django.get_version())"
```

## Creating a project
```python
django-admin startproject mysite
```

## Database setup
```python
python manage.py migrate
```
The **migrate** command looks at the **INSTALLED_APPS** setting and creates any necessary database tables according to the database settings in your **mysite/settings.py** file and the database migrations shipped with the app.

You can show a list of all known migrations and which are applied using
```python
python manage.py migrate --list
```

## The development server
```python
python manage.py runserver
```
You've started the Django development server, a lightweight Web server written purely in Python.
