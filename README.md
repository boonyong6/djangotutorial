# Writing your first Django app, part 1

- Create a basic **poll application**.
- Two parts:
  1. Public site - View polls and vote.
  2. Admin site - Add, change, and delete polls.

## Creating a project (environment)

- Initial setup - bootstrap a Django project - generate settings:
  - Database configuration
  - Django-specific options
  - Application-specific settings
- Command to bootstrap a new Django project:
  ```bash
  projects/ 
  $ django-admin startproject mysite djangotutorial
  ```
- **Note:** Avoid naming projects after built-in Python or Django components (packages).
- Generated files:
  File | Description
  -----|------------
  `manage.py` | Command-line utility for interacting with the Django project.
  `mysite/` | **Main Python package** for the Django project.
  `mysite/urls.py` | URL declarations. A **"table of contents"** of the Django powered site.
  `mysite/asgi.py` | Entry-point for **ASGI-compatible web servers**.
  `mysite/wsgi.py` | Entry-point for **WSGI-compatible web servers**.

## The development server

- Command to start the **development server**.
  ```bash
  projects/djangotutorial 
  $ python manage.py runserver
  ```
- **Don't** use this server in production.
- **Auto reloading** for code changes (adding files don't trigger a restart). 

## Creating the Polls app

- Projects vs. apps
  - An **app** is a **web application** (e.g. poll app)
  - A **project** is  **a collection of configuration and apps** for a particular website.
- Command to create an app:
  ```bash
  projects/djangotutorial 
  $ python manage.py startapp polls
  ```

## Write your first view

- Implement the view in `polls/views.py`.
- Define a URL configuration (**URLconf**) **inside the Django app** to map a view to a URL.
  - Create the `polls/urls.py` file.
- Next, **configure the global URLconf** in the `mysite` project **to include** the URLconf defined in `polls.urls`.
  - `django.urls.include()`
    - Allows referencing **other URLconf**.
    - To **plug-and-play URLs**.
    - Always use `include()` to include other URL patterns.
