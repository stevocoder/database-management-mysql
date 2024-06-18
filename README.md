# database-management-mysql
database mangement mysql
In order to create these database designs in MySQL using Object Relational Mapping, i define corresponding classes for each entity in the  application. Here's a sample structure using Python and SQLAlchemy for ORM:

1. Users:
```python
from sqlalchemy import Column, Integer, String, DateTime
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class User(Base):
    __tablename__ = 'users'
    
    user_id = Column(Integer, primary_key=True)
    username = Column(String)
    email = Column(String)
    password = Column(String)
    created_at = Column(DateTime)
    updated_at = Column(DateTime)
```

2. Expenses:
```python
from sqlalchemy import ForeignKey
from sqlalchemy.orm import relationship

class Expense(Base):
    __tablename__ = 'expenses'
    
    expense_id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.user_id'))
    category_id = Column(Integer, ForeignKey('categories.category_id'))
    amount = Column(Integer)
    date = Column(DateTime)
    description = Column(String)
    created_at = Column(DateTime)
    updated_at = Column(DateTime)
    
    user = relationship('User')
    category = relationship('Category')
```

3. Categories:
```python
class Category(Base):
    __tablename__ = 'categories'
    
    category_id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.user_id'))
    category_name = Column(String)
    created_at = Column(DateTime)
    updated_at = Column(DateTime)
    
    user = relationship('User')
```

4. Payment Methods:
```python
class PaymentMethod(Base):
    __tablename__ = 'payment_methods'
    
    payment_method_id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.user_id'))
    payment_method_name = Column(String)
    created_at = Column(DateTime)
    updated_at = Column(DateTime)
    
    user = relationship('User')
```

5. Budgets:
```python
class Budget(Base):
    __tablename__ = 'budgets'
    
    budget_id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.user_id'))
    category_id = Column(Integer, ForeignKey('categories.category_id'))
    amount = Column(Integer)
    start_date = Column(DateTime)
    end_date = Column(DateTime)
    created_at = Column(DateTime)
    updated_at = Column(DateTime)
    
    user = relationship('User')
    category = relationship('Category')
```

