# django-bookstore

## Description

A complete production-ready Full Stack Bookstore application built with Django. This is a dummy project and does not contain ordering functionality. The app allows users to login, register, search for books, and view book details. The app is built using Django, HTML, CSS, and Bootstrap.

## Features

- User Authentication using django-allauth (Login, Register, Logout)
- Search functionality using Q lookup
- Dockerized application
- Testing using Django's TestCase
- Static files served using Whitenoise
- Best practices for secure deployment

## Installation

You can pull the docker image from [here](https://hub.docker.com/repository/docker/akmxdd/bookstore-project-web/general)

Alternatively, you can clone the repository and run the following commands:

```bash
mkdir django-bookstore
cd django-bookstore
<clone using your preferred method>
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
docker-compose up -d --build
```

The application will be available at `http://localhost:8000/` automatically, since the `docker-compose.yml` file has been configured to run the application on port 8000 when the image is built. You can change this behavior by modifying the `docker-compose.yml` file.

## Usage

Create a superuser to access the admin panel:

```bash
docker-compose exec web python manage.py createsuperuser
```

Access the application at `http://localhost:8000/`

Access the admin panel at `http://localhost:8000/definitely-not-admin/`

## Testing

The application has a total of 18 tests. To run the tests, execute the following command:

```bash
docker-compose exec web python manage.py test
```

The tests may fail when the application is first installed. This is because the tests are run before the database is created. To fix this, run the tests again after the application has been installed.

Two tests are expected to fail, namely: `test_aboutpage_template` and `test_homepage_template`. This is because after enabling caching for deployment in our settings, the tests are unable to access the templates parallelly. This will not affect the functionality of the application. It is a known issue and can be ignored. For for information, refer to this [issue](https://stackoverflow.com/questions/71583690/django-cache-isolation-when-running-tests-in-parallel).

## Future Improvements

- Add ordering functionality
- Add user profile and dashboard
- Sorting and filtering
- Social Authentication using custom allauth templates
