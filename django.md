# Django

- [Start a new project](#start-a-new-project)
- [Migration](#migration)
  - [Resetting the Database](#resetting-the-database)
- [Functions](#functions)
  - [django.urls.reverse()](#djangourlsreverse)
- [Django Tests](#django-tests)
  - [Structure](#structure)
  - [Running Tests](#running-tests)
  - [Assertions](#assertions)
    - [assertRedirects](#assertredirects)
    - [assertTemplateUsed](#asserttemplateused)

## Start a new project
```sh
mkdir project_name
cd project_name

# Create Python virtual env
python3 -m venv venv

# Activate virtual env
source venv/bin/activate

# Install django
pip install django

# New django project
django-admin startproject config .

# Create app
python manage.py startapp app_name
```

Start server:
```sh
python manage.py runserver
```
Visit http://127.0.0.1:8000/

## Migration
Django create a database table for each models in `models.py`.

Makemigrations generates migration files based on the changes you made to your models.
```sh
python manage.py makemigrations

```

Migrate applies the migration files to update the database and tables.
```sh
python manage.py migrate
```

### Resetting the Database
Errors can occur in situations such as attempting to create a table that already exists.

When there is no need to retain data, resetting the database and re-applying migrations is the simplest solution.

```sh
docker compose down -v  # Removes Docker containers and volumes
docker compose up -d    # Rebuilds and starts the Docker containers
```

## Functions
### django.urls.reverse()

Why 'reverse'?

- **URL Resolution: URL -> view**

  Starting with a URL requested by the user/browser, it calls the right Django view.

- **Reverse URL resolution: view -> URL**

  Starting with the identification of the corresponding Django, view obtain the associated URL.

## Django Tests

Django's testing framework is built on Python's **unittest** module.

### Structure
Only use `tests.py` or `tests/` directory.

- Automatically a tests.py is added to each app
- Or you can create tests/ subdirectory
  - Test modules must start with test_
  - tests/ directories must contain `__init__.py` which is an empty file.

The file should import django.test.TestCase:
```python
from django.test import TestCase
```

If you don't use database for test:
```python
from django.test import SimpleTestCase
```

### Running Tests
```sh
python manage.py test
```

### Assertions

#### assertRedirects

ex. `self.assertRedirects(response, reverse('top'))`
- This method checks that the response has a proper redirect
(HTTP status code is `302 Found` or `301 Moved Permanently`)

- Use this method when a user should be automatically sent to another page after performing a particular action, such as a redirect after logout or login.


#### assertTemplateUsed
ex. `self.assertTemplateUsed(response, 'top.html')`

- This method verifies whether the specified template was used to render the response.

- Use this method when a view uses a particular template to generate HTML content.


