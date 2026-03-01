# 🌐 What is WebDriver in Selenium?

👉 **WebDriver** is a tool that controls the browser automatically using code.

## 🧭 Flow Concept

Python Code
     ↓
Selenium Library
     ↓
WebDriver (ChromeDriver, GeckoDriver)
     ↓
Browser (Chrome / Firefox / Edge)


---

## 🧠 Real-Life Example

Imagine you want to open **Google.com** in Chrome.

Normally, you do:
- Open Chrome  
- Type URL  
- Press Enter  

👉 **WebDriver does all this automatically using code.**

---

## 🧩 Simple Definition (Exam Ready)

> **WebDriver is an interface that allows Selenium to control web browsers programmatically.**

---

## 🖥️ Why WebDriver is Needed?

- Browsers are **secure**
- They **do not allow automation directly**

👉 Selenium uses WebDriver as a **bridge** between code and browser.

---

## 🧱 WebDriver Architecture (Very Important)

Python Code
     ↓
Selenium Library
     ↓
WebDriver (ChromeDriver, GeckoDriver)
     ↓
Browser (Chrome / Firefox / Edge)


---

## ✅ Example Code

```python
from selenium import webdriver

# Create WebDriver object
driver = webdriver.Chrome()

# Open website
driver.get("https://google.com")
```


#### 👉 Here, webdriver.Chrome() is the WebDriver.

🧩 Types of WebDrivers
```python
Browser	WebDriver Name
Chrome	ChromeDriver
Firefox	GeckoDriver
Edge	EdgeDriver
Safari	SafariDriver
```

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Initialize Chrome driver (no path needed if chromedriver is in PATH)
driver = webdriver.Chrome()

driver.get("https://www.google.com")
time.sleep(2)

search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Selenium Python tutorial")
search_box.send_keys(Keys.RETURN)

time.sleep(3)
print("Page Title:", driver.title)

driver.quit()



```

```python
import pytest
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Fixture for initializing and quitting the driver
@pytest.fixture
def driver():
    # Create a Service object with the path to chromedriver.exe
    service = Service("chromedriver.exe")
    driver = webdriver.Chrome(service=service)  # Pass Service object instead of executable_path
    yield driver
    driver.quit()

# Test function
def test_google_search(driver):
    driver.get("https://www.google.com")
    time.sleep(2)

    search_box = driver.find_element(By.NAME, "q")
    search_box.send_keys("Selenium Python tutorial")
    search_box.send_keys(Keys.RETURN)

    time.sleep(3)
    print("Page Title:", driver.title)

    # Simple pass assertion
    assert True
```


```python

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

driver = webdriver.Chrome()
driver.get("https://www.w3schools.com/")

search = driver.find_element(By.ID, "search2")
search.send_keys("Python")
search.send_keys(Keys.RETURN)

time.sleep(2)
print("Page Title:", driver.title)

driver.quit()



```
