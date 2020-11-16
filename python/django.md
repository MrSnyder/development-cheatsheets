# Django

* [Homepage](https://www.djangoproject.com/)

## SQL migration

```bash
# models -> SQL scripts
python manage.py makemigrations <app>
# show SQL migration script 0001
python manage.py sqlmigrate <app> 0001
# apply SQL migration scripts
python manage.py migrate
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
