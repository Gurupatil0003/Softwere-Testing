# Selenium Waits Cheat Sheet

Selenium waits are used to **pause the execution** until a certain condition is met or elements are available on a page. Different types of waits have their **pros, drawbacks, and best use cases**.

---

| **Wait Type**        | **Scope / Applies To**           | **Purpose / What it Does**                                         | **When to Use**                                  | **Drawbacks / Notes** |
|---------------------|---------------------------------|--------------------------------------------------------------------|-------------------------------------------------|----------------------|
| **Implicit Wait**    | Global (all elements in session) | Waits a maximum time for elements to appear before throwing error | Simple/static pages where elements load quickly | ❌ Not precise, applies to all elements <br> ❌ Can slow down tests unnecessarily if set too high <br> ✅ Easy to implement |
| **Explicit Wait**    | Specific element / condition     | Waits until a certain condition is met for an element             | Dynamic pages, AJAX-loaded content, slow elements | ❌ Slightly more code <br> ✅ Precise and reliable <br> ✅ Can wait for clickable, visible, presence, text, etc. |
| **Fluent Wait**      | Specific element / condition     | Like Explicit Wait but allows custom polling interval and ignores exceptions | Complex conditions, elements appearing randomly | ❌ More verbose code <br> ✅ Maximum control <br> ✅ Can define polling frequency and ignore exceptions |
| **No Wait (Default)** | None | Selenium tries to find element immediately, throws `NoSuchElementException` if not found | Fast-loading pages, elements already present | ❌ Fails if element is not immediately available <br> ✅ Very fast for simple pages |

---

## 💡 Quick Tips (CSAT style)
1. **Implicit Wait** → Use for **simple/static pages**, but avoid for dynamic content.  
2. **Explicit Wait** → Best choice for **dynamic websites or AJAX content**.  
3. **Fluent Wait** → Use when elements are **slow or appear randomly**, need custom polling or exception handling.  
4. **No Wait** → Only for **fast-loading pages** where elements are immediately present.  
5. **Never mix Implicit and Explicit Waits** → Can cause **unexpected delays**.  

---


## ✅ Examples

### 1. Implicit Wait
```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.implicitly_wait(10)  # Wait up to 10 seconds for any element
driver.get("https://example.com")
element = driver.find_element("id", "submit_button")
element.click()
```

### 2. Explicit Wait
```python
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com")

# Wait until the button is clickable
button = WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.ID, "submit_button"))
)
button.click()
```
### 3. Fluent Wait
```python
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.common.exceptions import NoSuchElementException
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com")

# Wait up to 15s, check every 2s, ignore NoSuchElementException
wait = WebDriverWait(driver, 15, poll_frequency=2, ignored_exceptions=[NoSuchElementException])
element = wait.until(
    EC.presence_of_element_located((By.ID, "my_element"))
)
element.click()
```
### 4. No Wait (Default)
```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com")
element = driver.find_element("id", "submit_button")
element.click()
```

## 💡 Quick Tips

- **Implicit Wait** → “Look everywhere for X seconds.”  
- **Explicit Wait** → “Wait until this element is ready.”  
- **Fluent Wait** → “Wait until this element is ready, check every Y seconds, ignore errors.”  
- **No Wait** → Only works if elements are instantly available.  



## ✅ STEP 1 — Replace time.sleep() with IMPLICIT WAIT (Small Change)

```python
👉 Only 1 new line added

from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

# 🔹 Added Implicit Wait
driver.implicitly_wait(5)

driver.get("file:///C:/Users/LENOVO/Downloads/New folder (49)/a.html")

username = driver.find_element(By.ID, "username")
username.send_keys("Guru")

password = driver.find_element(By.NAME, "password")
password.send_keys("12345")

driver.find_element(By.ID, "loginBtn").click()

print("Button Clicked Successfully")

driver.quit()

🧠 Implicit wait replaces all sleep()
```
## ✅ STEP 2 — EXPLICIT WAIT (Small Modification)

```python
👉 Add 2 imports + change find_element lines

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.get("file:///C:/Users/LENOVO/Downloads/New folder (49)/a.html")

wait = WebDriverWait(driver, 5)

# 🔹 Wait for username
username = wait.until(EC.visibility_of_element_located((By.ID, "username")))
username.send_keys("Guru")

# 🔹 Wait for password
password = wait.until(EC.visibility_of_element_located((By.NAME, "password")))
password.send_keys("12345")

# 🔹 Wait for button
wait.until(EC.element_to_be_clickable((By.ID, "loginBtn"))).click()

print("Button Clicked Successfully")

driver.quit()

🧠 Only wait.until() added → rest same.
```
## ✅ STEP 3 — FLUENT WAIT (Very Small Change from Explicit)
```python 
👉 Only change WebDriverWait line

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.common.exceptions import NoSuchElementException

driver = webdriver.Chrome()
driver.get("file:///C:/Users/LENOVO/Downloads/New folder (49)/a.html")

# 🔹 Fluent Wait
wait = WebDriverWait(driver, 5, poll_frequency=1, ignored_exceptions=[NoSuchElementException])

username = wait.until(EC.visibility_of_element_located((By.ID, "username")))
username.send_keys("Guru")

password = wait.until(EC.visibility_of_element_located((By.NAME, "password")))
password.send_keys("12345")

wait.until(EC.element_to_be_clickable((By.ID, "loginBtn"))).click()

print("Button Clicked Successfully")

driver.quit()

🧠 Only poll_frequency and ignored_exceptions added.
```
## ✅ STEP 4 — Expected Conditions (Tiny Syntax Examples)
```python
You already used EC, but show students separately:

# Wait for element in HTML
EC.presence_of_element_located((By.ID, "username"))

# Wait for visible element
EC.visibility_of_element_located((By.ID, "username"))

# Wait for clickable button
EC.element_to_be_clickable((By.ID, "loginBtn"))

```
