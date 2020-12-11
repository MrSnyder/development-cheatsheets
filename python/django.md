# Django

* [Homepage](https://www.djangoproject.com/)

## ORM

* [Many-to-many relations](https://docs.djangoproject.com/en/3.1/topics/db/examples/many_to_many/)

### SQL migrations

```bash
# models -> SQL scripts
python manage.py makemigrations <app>
# show SQL migration script 0001
python manage.py sqlmigrate <app> 0001
# apply SQL migration scripts
python manage.py migrate
```

### From the django shell

```python
from shop.models import Product
Product.objects.all() #to get all the products
```

## i18n
```bash
# create "locale/de/LC_MESSAGES/django.po" from gettext calls (code) and lang directives (templates)
python ./manage.py makemessages --locale=de --ignore=venv --ignore=docker

```

## Misc

```bash
# invoke shell
python manage.py shell
# create user for admin site
python manage.py createsuperuser
# tests
python manage.py test tests.unit_tests.service_app.test_tables:ServiceTestCase.test_wms_service_table_sorting
# only run tests that failed before
python manage.py test tests --failed
```

## Add new app to existing project

* `python manage.py startapp <appName>`


## Persistent trees

* [django-mptt](https://github.com/django-mptt/django-mptt)
* [django-treebeard](https://github.com/django-treebeard/django-treebeard)
* [django-treewidget](https://github.com/netzkolchose/django-treewidget)
