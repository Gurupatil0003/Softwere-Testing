# 🧪 Software Testing with PyTest – Complete Guide

This repository contains a **complete beginner-to-advanced guide to Software Testing using PyTest**, with examples and real-world use cases.

---

# 📌 What is PyTest?

**PyTest** is a powerful Python testing framework used to write simple and scalable test cases.  
It is widely used in **industry, startups, and open-source projects**.

---

# ⚙️ Installation

```bash
pip install pytest

```


```python
pytest --version

```


## ✅ 3. Basic Test Structure
```python

File naming rules:

File must start with test_

Function must start with test_

```

## ✅ 4. Assertions in PyTest

```python
Assertions check expected output.

def test_assertions():
    assert 5 == 5
    assert 10 > 5
    assert "python".upper() == "PYTHON"

```


## ✅ 5. Running PyTest
```python
pytest               # run all tests
pytest -v            # verbose
pytest test_math.py  # run specific file
pytest -k add        # run tests with "add" in name
```

## ✅ 6. Test Classes
```python
class TestMath:

    def test_add(self):
        assert 2 + 3 == 5

    def test_sub(self):
        assert 5 - 3 == 2
```
## ✅ 7. PyTest Fixtures (Very Important)

```python
Fixtures are used for setup & teardown.

Example:
import pytest

@pytest.fixture
def sample_data():
    return [1, 2, 3, 4]

def test_sum(sample_data):
    assert sum(sample_data) == 10
```
## 🔹 Fixture with setup & teardown
```python
@pytest.fixture
def db_connection():
    print("Connecting DB")
    yield "DB Connected"
    print("Closing DB")

def test_db(db_connection):
    assert db_connection == "DB Connected"

```   
## ✅ 8. Parameterized Testing

```python
Run same test with multiple inputs.

import pytest

@pytest.mark.parametrize("a,b,expected", [
    (2, 3, 5),
    (1, 1, 2),
    (10, 5, 15)
])
def test_add(a, b, expected):
    assert a + b == expected

```

```python
✅ 1. PyTest Directory Structure (Best Practice)
project/
│
├── app/
│   └── main.py
│
├── tests/
│   ├── test_main.py
│   └── conftest.py
│
└── requirements.txt


```

## ✅ 2️⃣ app/main.py (Your Application Code)
```python
# app/main.py

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

👉 This is your actual software code (business logic).
```

## ✅ 3️⃣ tests/test_main.py (Your Test File)
```python
# tests/test_main.py

from app.main import add, subtract

def test_add():
    assert add(2, 3) == 5

def test_subtract():
    assert subtract(10, 5) == 5

👉 These are your automated test cases.
```

## ✅ 4️⃣ tests/conftest.py (Global Fixture File)
```python
# tests/conftest.py

import pytest

@pytest.fixture
def sample_numbers():
    return (10, 5)
```
## ✅ 5️⃣ Use Fixture in test_main.py
```python
Update test_main.py:

from app.main import add, subtract

def test_add(sample_numbers):
    a, b = sample_numbers
    assert add(a, b) == 15

def test_subtract(sample_numbers):
    a, b = sample_numbers
    assert subtract(a, b) == 5
```
## ✅ 6️⃣ requirements.txt

```python
pytest

```


