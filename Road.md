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
