# Python

* [Object-Oriented Programming in Python vs Java](https://realpython.com/oop-in-python-vs-java/#inheritance-and-polymorphism)

## Accessing object properties

```python
# via getattr
print getattr(e1,'name')
# default values to avoid no attribute errors
a={}
a.get("b",{}).get("c")
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

## Pip

```bash
pip install requests-mock
```

## Virtual Env

* [Primer on Python Virtual Environments](https://realpython.com/python-virtual-environments-a-primer/)

```bash
# activate
source venv/bin/activate
# deactivate
deactivate
# create
virtualenv -p python2.7 munimap
```

## Tests

### Mocking

* [Getting Started with Mocking in Python](https://semaphoreci.com/community/tutorials/getting-started-with-mocking-in-python)
* [Mocking External APIs in Python](https://realpython.com/testing-third-party-apis-with-mocks/)

```python
    # Inject a mock for function "get" of imported module requests in module 'quality.plugins.etf'
    # control return values of functions by adding '.return_value'
    @patch('quality.plugins.etf.requests.post')
    def test_upload_test_object_ok(self, mock_post):
        mock_post.return_value.status_code = 200
        mock_post.return_value.json.return_value = {
            'testObject': {
                'id': 1
            }
        }
        test_object_id = self.etf_client.upload_test_object("<upload_document/>")
        self.assertEquals(test_object_id, 1)


class TestBlog(TestCase):
    @patch('main.Blog')
    def test_blog_posts(self, MockBlog):
        blog = MockBlog()

        blog.posts.return_value = [
            {
                'userId': 1,
                'id': 1,
                'title': 'Test Title',
                'body': 'Far out in the uncharted backwaters of the unfashionable  end  of the  western  spiral  arm  of  the Galaxy\ lies a small unregarded yellow sun.'
            }
        ]

        response = blog.posts()
        self.assertIsNotNone(response)
        self.assertIsInstance(response[0], dict)

        # Additional assertions
        assert MockBlog is main.Blog # The mock is equivalent to the original

        assert MockBlog.called # The mock wasP called

        blog.posts.assert_called_with() # We called the posts method with no arguments

        blog.posts.assert_called_once_with() # We called the posts method once with no arguments

        # blog.posts.assert_called_with(1, 2, 3) - This assertion is False and will fail since we called blog.posts with no arguments

        blog.reset_mock() # Reset the mock object
        
        blog.posts.assert_not_called() # After resetting, posts has not been called.
```

## Misc

* [PEP8 Style Guide](https://www.python.org/dev/peps/pep-0008/)
* [Django ORM vs SQLAlchemy](https://dzone.com/articles/django-vs-sqlalchemy-which-python-orm-is-better)
