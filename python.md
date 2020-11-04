# Python Cheatsheet V2
## Language
* [Object-Oriented Programming in Python vs Java](https://realpython.com/oop-in-python-vs-java/#inheritance-and-polymorphism)
```python
# list comprehension
names = ['Apple', 'Banana', 'wtf']
names_length = [len(v) for v in a]
name_to_length = {v:len(v) for v in a if len(v) < 4}
```
## Dependency management
* pip
* requirements.txt
## Virtual Env
* [Primer on Python Virtual Environments](https://realpython.com/python-virtual-environments-a-primer/)
* PyCharm: File -> Settings -> Project -> Python Interpreter -> Wheel
```bash
# create venv
virtualenv -p python2.7 munimap
```
## Misc
* [PEP8 Style Guide](https://www.python.org/dev/peps/pep-0008/)
## Django
* [Django](https://www.djangoproject.com/)
### SQL migration
```bash
# create SQL scripts for table creation / migration
python manage.py makemigrations <app>
# show SQL migration script 0001
python manage.py sqlmigrate <app> 0001
# apply SQL migration scripts
python manage.py migrate
```
## Misc
```
# invoke shell
python manage.py shell
# create user for admin site
python manage.py createsuperuser
```
