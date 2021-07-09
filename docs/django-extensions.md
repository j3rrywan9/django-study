# Django Extensions

Django Extensions is a collection of custom extensions for the Django Framework.

These include management commands, additional database fields, admin extensions and much more.

## Installation instructions

### Installing

```
pip install django-extensions
```

### Development

### Configuration

You will need to add the *django_extensions* application to the `INSTALLED_APPS` setting of your Django project *settings.py* file:
```python
INSTALLED_APPS = (
    ...
    'django-extensions',
)
```
This will make sure that Django finds the additional management commands provided by *django-extensions*.

The next time you invoke `./manage.py help` you should be able to see all the newly available commands.

## Admin Extensions

## Command Extensions

### RunScript

#### Introduction

The runscript command lets you run an arbitrary set of python commands within the Django context.
It offers the same usability and functionality as running a set of commands in shell accessed by:
```
python manage.py shell
```

#### Getting Started

#### Usage

#### Passing Arguments
