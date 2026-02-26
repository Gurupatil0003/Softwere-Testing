```python

import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from webdriver_manager.chrome import ChromeDriverManager
import time

# ---------------- FIXTURE ----------------
@pytest.fixture
def driver():
    service = Service(ChromeDriverManager().install())
    driver = webdriver.Chrome(service=service)
    driver.maximize_window()
    yield driver
    time.sleep(3)
    driver.quit()

# ---------------- TEST CASE ----------------
def test_saucedemo_order(driver):
    
    wait = WebDriverWait(driver, 10)

    # Open website slowly
    driver.get("https://www.saucedemo.com/")
    time.sleep(3)

    # Login
    driver.find_element(By.ID, "user-name").send_keys("standard_user")
    time.sleep(2)

    driver.find_element(By.ID, "password").send_keys("secret_sauce")
    time.sleep(2)

    driver.find_element(By.ID, "login-button").click()
    time.sleep(4)

    print("✅ Login Successful")

    # Add products slowly
    driver.find_element(By.ID, "add-to-cart-sauce-labs-backpack").click()
    print("🛒 Backpack added")
    time.sleep(3)

    driver.find_element(By.ID, "add-to-cart-sauce-labs-bike-light").click()
    print("🛒 Bike Light added")
    time.sleep(3)

    # Check cart count
    cart_count = driver.find_element(By.CLASS_NAME, "shopping_cart_badge").text
    print("Cart Count =", cart_count)
    time.sleep(2)

    assert cart_count == "1"

    # Go to cart
    driver.find_element(By.CLASS_NAME, "shopping_cart_link").click()
    time.sleep(3)

    # Checkout
    driver.find_element(By.ID, "checkout").click()
    time.sleep(3)

    # Fill details slowly
    driver.find_element(By.ID, "first-name").send_keys("Mounesh")
    time.sleep(2)

    driver.find_element(By.ID, "last-name").send_keys("Goud")
    time.sleep(2)

    driver.find_element(By.ID, "postal-code").send_keys("560001")
    time.sleep(2)

    driver.find_element(By.ID, "continue").click()
    time.sleep(4)

    # Finish order
    driver.find_element(By.ID, "finish").click()
    time.sleep(4)

    print("✅ Order Completed")

    # Assertion
    success_text = driver.find_element(By.CLASS_NAME, "complete-header").text
    assert "Thank you for your order!" in success_text

    # Logout slowly
    driver.find_element(By.ID, "react-burger-menu-btn").click()
    time.sleep(3)

    driver.find_element(By.ID, "logout_sidebar_link").click()
    time.sleep(3)

    print("✅ Logged Out")

```


```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# ---------- FIXTURE FOR BROWSER SETUP & TEARDOWN ----------
@pytest.fixture
def driver():
    driver = webdriver.Chrome()
    driver.maximize_window()
    yield driver
    driver.quit()


# ---------- TEST CASE ----------
def test_saucedemo_order(driver):
    
    # Open website
    driver.get("https://www.saucedemo.com/")
    time.sleep(2)

    # Login
    driver.find_element(By.ID, "user-name").send_keys("standard_user")
    driver.find_element(By.ID, "password").send_keys("secret_sauce")
    driver.find_element(By.ID, "login-button").click()
    time.sleep(2)

    print("✅ Logged in")

    # Add products
    driver.find_element(By.ID, "add-to-cart-sauce-labs-backpack").click()
    print("Added Backpack")
    time.sleep(1)

    driver.find_element(By.ID, "add-to-cart-sauce-labs-bike-light").click()
    print("Added Bike Light")
    time.sleep(1)

    # Go to cart
    driver.find_element(By.CLASS_NAME, "shopping_cart_link").click()
    time.sleep(2)

    # Checkout
    driver.find_element(By.ID, "checkout").click()
    time.sleep(1)

    # Fill details
    driver.find_element(By.ID, "first-name").send_keys("Mounesh")
    driver.find_element(By.ID, "last-name").send_keys("Goud")
    driver.find_element(By.ID, "postal-code").send_keys("560001")
    driver.find_element(By.ID, "continue").click()
    time.sleep(2)

    # Finish order
    driver.find_element(By.ID, "finish").click()
    time.sleep(2)

    print("✅ Order Completed")

    # Assertion (Very Important in PyTest)
    success_text = driver.find_element(By.CLASS_NAME, "complete-header").text
    assert "THANK YOU" in success_text

    # Logout
    driver.find_element(By.ID, "react-burger-menu-btn").click()
    time.sleep(1)
    driver.find_element(By.ID, "logout_sidebar_link").click()

    print("✅ Logged Out")



```

## Professional structure

```python
conftest.py → browser setup

config.py → test data & URLs

pages/ → Page Object Model (POM)

tests/ → actual test cases

This is industry-level Selenium + PyTest structure 👌
```
```python
✅ Recommended Project Structure
project/
│
├── config.py
├── conftest.py
│
├── pages/
│   ├── login_page.py
│   ├── products_page.py
│   ├── cart_page.py
│   └── checkout_page.py
│
└── tests/
    └── test_order.py
```
### 1️⃣ config.py
```python
# config.py

BASE_URL = "https://www.saucedemo.com/"

USERNAME = "standard_user"
PASSWORD = "secret_sauce"

FIRST_NAME = "Mounesh"
LAST_NAME = "Goud"
POSTAL_CODE = "560001"
```
### 2️⃣ conftest.py (Browser Setup)
```python
# conftest.py

import pytest
from selenium import webdriver

@pytest.fixture
def driver():
    driver = webdriver.Chrome()
    driver.maximize_window()
    yield driver
    driver.quit()
```
### 3️⃣ pages/login_page.py
```python
from selenium.webdriver.common.by import By
import config

class LoginPage:

    def __init__(self, driver):
        self.driver = driver

    def open(self):
        self.driver.get(config.BASE_URL)

    def login(self):
        self.driver.find_element(By.ID, "user-name").send_keys(config.USERNAME)
        self.driver.find_element(By.ID, "password").send_keys(config.PASSWORD)
        self.driver.find_element(By.ID, "login-button").click()
```
### 4️⃣ pages/products_page.py
```python
from selenium.webdriver.common.by import By

class ProductsPage:

    def __init__(self, driver):
        self.driver = driver

    def add_backpack(self):
        self.driver.find_element(By.ID, "add-to-cart-sauce-labs-backpack").click()

    def add_bike_light(self):
        self.driver.find_element(By.ID, "add-to-cart-sauce-labs-bike-light").click()

    def go_to_cart(self):
        self.driver.find_element(By.CLASS_NAME, "shopping_cart_link").click()
```
### 5️⃣ pages/cart_page.py
```python
from selenium.webdriver.common.by import By

class CartPage:

    def __init__(self, driver):
        self.driver = driver

    def checkout(self):
        self.driver.find_element(By.ID, "checkout").click()
```
### 6️⃣ pages/checkout_page.py
```python
from selenium.webdriver.common.by import By
import config

class CheckoutPage:

    def __init__(self, driver):
        self.driver = driver

    def fill_details(self):
        self.driver.find_element(By.ID, "first-name").send_keys(config.FIRST_NAME)
        self.driver.find_element(By.ID, "last-name").send_keys(config.LAST_NAME)
        self.driver.find_element(By.ID, "postal-code").send_keys(config.POSTAL_CODE)
        self.driver.find_element(By.ID, "continue").click()

    def finish_order(self):
        self.driver.find_element(By.ID, "finish").click()

    def get_success_message(self):
        return self.driver.find_element(By.CLASS_NAME, "complete-header").text
```
### 7️⃣ tests/test_order.py
```python
from pages.login_page import LoginPage
from pages.products_page import ProductsPage
from pages.cart_page import CartPage
from pages.checkout_page import CheckoutPage


def test_saucedemo_order(driver):

    login = LoginPage(driver)
    products = ProductsPage(driver)
    cart = CartPage(driver)
    checkout = CheckoutPage(driver)

    # Open & Login
    login.open()
    login.login()

    # Add Products
    products.add_backpack()
    products.add_bike_light()
    products.go_to_cart()

    # Checkout
    cart.checkout()
    checkout.fill_details()
    checkout.finish_order()

    # Assertion
    success_text = checkout.get_success_message()
    assert "THANK YOU" in success_text
```

```python
🚀 Why This Structure Is Professional

✅ Separation of concerns
✅ Reusable code
✅ Easy maintenance
✅ Scalable for 100+ test cases
✅ Follows Page Object Model (POM)
```
