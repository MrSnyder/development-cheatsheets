# Python

* [Object-Oriented Programming in Python vs Java](https://realpython.com/oop-in-python-vs-java/#inheritance-and-polymorphism)

## Accessing object properties

```python
# via getattr
print getattr(e1,'name')
```


## List comprehension

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
* PyCharm: File -&gt; Settings -&gt; Project -&gt; Python Interpreter -&gt; Wheel

  ```bash
  # create venv
  virtualenv -p python2.7 munimap
  ```

  **Misc**

* [PEP8 Style Guide](https://www.python.org/dev/peps/pep-0008/)
