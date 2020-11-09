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
```
