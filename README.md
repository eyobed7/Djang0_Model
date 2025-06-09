# Djang0_Model
# Concept Overview

## Topics
- Models and Their Structure  
- Django ORM: Object-Relational Mapping  
- Database interaction with the Django ORM  
- Configuring the Database  

## Learning Objectives
- Understand the purpose and structure of Django models  
- Learn about the Django ORM and its benefits  
- Create and manipulate models using the Django ORM  
- Query the database using the Django ORM  
- Configure a database connection in Django for MySQL and set up the required database driver for the MySQL database engine  
- Apply database migrations to create or update tables based on model definitions  

---

## Models and Their Structure

In Django, models are defined as Python classes that inherit from the `django.db.models.Model` base class. Each attribute of the model represents a database field, and its type is defined using field classes provided by Django (e.g., `CharField`, `IntegerField`, `DateField`, etc.).

Example:

```python
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.CharField(max_length=100)
    published_date = models.DateField()
```

Common Field Types
CharField: Used to store text-based data with a max length. Requires max_length.

TextField: For large text content without a max length.

IntegerField: Stores integer values.

FloatField: Stores floating-point numbers.

DecimalField: Stores precise decimal values (great for currency).

BooleanField: Stores True/False values.

DateField: Stores date values.

EmailField: Subclass of CharField that validates email format.

Django allows custom fields by subclassing existing field types if needed.

**Django ORM: Object-Relational Mapping**
The Django ORM provides an abstraction layer to interact with databases using Python code instead of raw SQL.

Benefits
Database Abstraction: Work with Python objects instead of SQL.

Portability: Supports multiple database engines with minimal changes.

Schema Management: Automatically manages schema changes via migrations.

Powerful Queries: Use a Pythonic syntax for complex queries.

*Database Interaction with the Django ORM*
The ORM provides a rich query API. Examples:

```pyton
# Retrieve all books
books = Book.objects.all()

# Filter books by author
books_by_author = Book.objects.filter(author='John Doe')

# Order books by published date
books_ordered = Book.objects.order_by('published_date')

# Create a new book
new_book = Book(title='New Book', author='Jane Smith', published_date='2023-01-01')
new_book.save()
```
*Configuring the Database*
By default, Django uses SQLite for development. For production, it’s recommended to use robust engines like PostgreSQL or MySQL.

Example: Configuring MySQL in settings.py

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mydatabase',
        'USER': 'mydatabaseuser',
        'PASSWORD': 'mypassword',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```
ENGINE: Django DB engine to use (e.g., mysql).

NAME: Name of your database.

USER: DB user name.

PASSWORD: DB password.

HOST: Host address (usually localhost).

PORT: MySQL default port is 3306.

```python
pip install mysqlclient
```
**Apply Migrations**

```python
python manage.py migrate
```
```



