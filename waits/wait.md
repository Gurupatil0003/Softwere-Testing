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
