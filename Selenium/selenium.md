```html
<!DOCTYPE html>
<html>
<head>
    <title>Selenium Button Example</title>
</head>
<body>

<h2>Login Form</h2>

<form>
    <!-- ID -->
    <label>Username:</label>
    <input type="text" id="username"><br><br>

    <!-- NAME -->
    <label>Password:</label>
    <input type="password" name="password"><br><br>

    <!-- BUTTON TYPE
     
      -->
    <input type="button" id="loginBtn" value="Login Button">
</form>

</body>
</html>


```

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# Open Chrome browser
driver = webdriver.Chrome()   # Make sure chromedriver is installed

# Open the HTML file (change path)
driver.get("file:///C:/Users/LENOVO/Downloads/New%20folder%20(49)/a.html")

time.sleep(2)

# Find element by ID
username = driver.find_element(By.ID, "username")
username.send_keys("Guru")

# Find element by NAME
password = driver.find_element(By.NAME, "password")
password.send_keys("12345")


# BUTTON CLICK using ID
driver.find_element(By.ID, "loginBtn").click()

print("Button Clicked Successfully")

time.sleep(3)

driver.quit()


```


```python

<!DOCTYPE html>
<html>
<head>
    <title>Selenium Learning Playground</title>

    <script>
        function loginFunction() {
            var user = document.getElementById("username").value;
            var pass = document.getElementsByName("password")[0].value;

            document.getElementById("output").innerHTML =
                "Login Clicked! Username: " + user + " | Password: " + pass;
        }

        function submitFunction() {
            alert("Submit Button Clicked!");
        }

        function forgotPassword() {
            alert("Forgot Password Link Clicked!");
        }
    </script>

</head>
<body>

<h2>🚀 Selenium Beginner Practice Page</h2>

<!-- ID -->
<label>Username (ID Locator)</label><br>
<input type="text" id="username" placeholder="Enter Username"><br><br>

<!-- NAME -->
<label>Password (Name Locator)</label><br>
<input type="password" name="password" placeholder="Enter Password"><br><br>

<!-- TAG NAME -->
<label>Tag Name Example Input</label><br>
<input type="text" placeholder="Tag Name Demo"><br><br>

<!-- LINK TEXT -->
<a href="#" onclick="forgotPassword()">Forgot Password?</a><br><br>

<!-- BUTTON TYPE -->
<input type="button" id="loginBtn" value="Login Button" onclick="loginFunction()"><br><br>

<!-- CSS + XPATH Button -->
<button class="submitBtn" onclick="submitFunction()">Submit</button>

<!-- Output -->
<p id="output" style="color:green; font-weight:bold;"></p>

</body>
</html>
```

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.alert import Alert
import time

# Open Chrome
driver = webdriver.Chrome()

# Open HTML file (CHANGE PATH)
driver.get("file:///C:/Users/LENOVO/Downloads/New%20folder%20(49)/d.html")
time.sleep(2)

# -------- ID Locator --------
driver.find_element(By.ID, "username").send_keys("Guru")

# -------- NAME Locator --------
driver.find_element(By.NAME, "password").send_keys("12345")

# -------- TAG NAME Locator --------
driver.find_element(By.TAG_NAME, "input").send_keys("Tag Example")

# -------- LINK TEXT (Alert appears) --------
driver.find_element(By.LINK_TEXT, "Forgot Password?").click()
time.sleep(2)

# Handle Alert
alert = Alert(driver)
print("Alert Message:", alert.text)
alert.accept()   # Click OK
time.sleep(2)

# -------- XPATH Locator --------
driver.find_element(By.XPATH, "//button[@class='submitBtn']").click()
time.sleep(2)

# Handle second alert
alert = Alert(driver)
print("Alert Message:", alert.text)
alert.accept()
time.sleep(2)

# -------- CSS SELECTOR --------
driver.find_element(By.CSS_SELECTOR, ".submitBtn").click()
time.sleep(2)

# Handle third alert
alert = Alert(driver)
alert.accept()

# -------- BUTTON CLICK --------
driver.find_element(By.ID, "loginBtn").click()

print("✅ All Selenium Locators Executed Successfully")

time.sleep(5)
driver.quit()


```

## Web Element Handling
```python
<!DOCTYPE html>
<html>
<head>
<title>Web Element Handling Practice</title>
</head>
<body>

<h2>Web Element Handling Demo</h2>

<label>Username:</label>
<input type="text" id="username"><br><br>

<label>Password:</label>
<input type="password" id="password"><br><br>

<button id="loginBtn">Login</button>

<p id="msg">Welcome Student!</p>

</body>
</html>

```

```python

from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.get("file:///C:/Users/LENOVO/Desktop/webelement_practice.html")
time.sleep(2)

# ---------------- send_keys() ----------------
driver.find_element(By.ID, "username").send_keys("Guru")
driver.find_element(By.ID, "password").send_keys("12345")

time.sleep(2)

# ---------------- clear() ----------------
driver.find_element(By.ID, "password").clear()
driver.find_element(By.ID, "password").send_keys("newpass")

# ---------------- click() ----------------
driver.find_element(By.ID, "loginBtn").click()

# ---------------- get_text() ----------------
text = driver.find_element(By.ID, "msg").text
print("Message Text:", text)

# ---------------- is_displayed() ----------------
print("Username displayed:", driver.find_element(By.ID, "username").is_displayed())

# ---------------- is_enabled() ----------------
print("Login button enabled:", driver.find_element(By.ID, "loginBtn").is_enabled())

time.sleep(5)
driver.quit()



```
