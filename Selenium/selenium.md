```python
<!DOCTYPE html>
<html>
<head>
    <title>Simple Login</title>

    <!-- Bootstrap CDN -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>

<body class="bg-light d-flex justify-content-center align-items-center vh-100">

<form class="bg-white p-4 rounded shadow">
    <h2 class="text-center mb-3">Login Form</h2>

    <label>Username:</label>
    <input type="text" id="username" class="form-control mb-2">

    <label>Password:</label>
    <input type="password" name="password" class="form-control mb-3">

    <input type="button" id="loginBtn" value="Login" class="btn btn-primary w-100">
</form>

</body>
</html>


```
```python
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

## small version change

```python
<!DOCTYPE html>
<html>
<head>
<title>Login</title>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>

<body class="bg-light d-flex justify-content-center align-items-center vh-100">

<form class="bg-white p-4 rounded shadow">
    <h2 class="text-center mb-3">Login Form</h2>

    <label>Username:</label>
    <input type="text" id="username" class="form-control mb-2">

    <label>Password:</label>
    <input type="password"  name="password" class="form-control mb-3">

    <input type="button" id="loginBtn" value="Login" class="btn btn-primary w-100">

    <p id="msg">Login Successful</p>
</form>

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

# ---------- send_keys() ----------
driver.find_element(By.ID, "username").send_keys("Guru")
driver.find_element(By.NAME, "password").send_keys("12345")   # CHANGED

time.sleep(2)

# ---------- clear() ----------
driver.find_element(By.NAME, "password").clear()              # CHANGED
driver.find_element(By.NAME, "password").send_keys("newpass") # CHANGED

# ---------- click() ----------
driver.find_element(By.ID, "loginBtn").click()

# ---------- get_text() ----------
# Only works if you have <p id="msg">Something</p> in HTML
text = driver.find_element(By.ID, "msg").text
print("Message Text:", text)

# ---------- is_displayed() ----------
print("Username displayed:", driver.find_element(By.ID, "username").is_displayed())

# ---------- is_enabled() ----------
print("Login button enabled:", driver.find_element(By.ID, "loginBtn").is_enabled())

time.sleep(5)
driver.quit()
```


```python
<!DOCTYPE html>
<html>
<head>
    <title>Selenium Learning Playground</title>

    <!-- Bootstrap CSS CDN -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

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

<body class="bg-light">

<div class="container mt-5">
    <div class="card shadow p-4 mx-auto" style="max-width: 500px;">
        
        <h2 class="text-center mb-4">🚀 Selenium Beginner Practice Page</h2>

        <!-- Username -->
        <div class="mb-3">
            <label class="form-label">Username (ID Locator)</label>
            <input type="text" id="username" class="form-control" placeholder="Enter Username">
        </div>

        <!-- Password -->
        <div class="mb-3">
            <label class="form-label">Password (Name Locator)</label>
            <input type="password" name="password" class="form-control" placeholder="Enter Password">
        </div>

        <!-- Tag Name Example -->
        <div class="mb-3">
            <label class="form-label">Tag Name Example Input</label>
            <input type="text" class="form-control" placeholder="Tag Name Demo">
        </div>

        <!-- Forgot Password -->
        <div class="mb-3 text-end">
            <a href="#" class="link-primary" onclick="forgotPassword()">Forgot Password?</a>
        </div>

        <!-- Buttons -->
        <div class="d-grid gap-2">
            <input type="button" id="loginBtn" class="btn btn-primary" value="Login Button" onclick="loginFunction()">
            <button class="btn btn-success submitBtn" onclick="submitFunction()">Submit</button>
        </div>

        <!-- Output -->
        <p id="output" class="mt-3 text-success fw-bold text-center"></p>

    </div>
</div>

</body>
</html>


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


```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.get("file:///C:/Users/LENOVO/Downloads/New%20folder%20(49)/g.html")
time.sleep(2)

# send_keys()
driver.find_element(By.ID, "username").send_keys("Guru")
driver.find_element(By.ID, "password").send_keys("new")

time.sleep(1)
driver.find_element(By.ID, "password").clear()
driver.find_element(By.ID, "password").send_keys("newpass")

# click()
driver.find_element(By.ID, "loginBtn").click()
time.sleep(2)

# get_text()
text = driver.find_element(By.ID, "msg").text
print("Message Text:", text)

# is_displayed()
print("Message displayed:", driver.find_element(By.ID, "msg").is_displayed())

# is_enabled()
print("Login button enabled:", driver.find_element(By.ID, "loginBtn").is_enabled())

time.sleep(5)
driver.quit()


```


```python
<!DOCTYPE html>
<html>
<head>
<title>Login</title>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

<script>
function validateLogin() {
    let username = document.getElementById("username").value;
    let password = document.getElementById("password").value;
    let msg = document.getElementById("msg");

    if(username === "Guru" && password === "newpass"){
        msg.innerHTML = "Login Successful ✅";
        msg.className = "text-success mt-3 text-center";
        msg.style.display = "block";
    } else {
        msg.innerHTML = "Invalid Credentials ❌";
        msg.className = "text-danger mt-3 text-center";
        msg.style.display = "block";
    }
}
</script>
</head>

<body class="bg-light d-flex justify-content-center align-items-center vh-100">

<form class="bg-white p-4 rounded shadow" style="width:350px;">
    <h2 class="text-center mb-3">Login Form</h2>

    <label>Username:</label>
    <input type="text" id="username" class="form-control mb-2">

    <label>Password:</label>
    <input type="password" id="password" class="form-control mb-3">

    <input type="button" id="loginBtn" value="Login" 
           class="btn btn-primary w-100" 
           onclick="validateLogin()">

    <!-- Hidden initially -->
    <p id="msg" style="display:none;"></p>
</form>

</body>
</html>



```

```python
from flask import Flask
from selenium import webdriver
from selenium.webdriver.common.by import By
import time
import threading

app = Flask(__name__)

def run_automation():
    time.sleep(2)  # wait for server to start

    driver = webdriver.Chrome()
    driver.maximize_window()
    driver.get("https://demoqa.com/automation-practice-form")

    time.sleep(3)

    # Fill First Name
    driver.find_element(By.ID, "firstName").send_keys("John")

    # Fill Last Name
    driver.find_element(By.ID, "lastName").send_keys("Doe")

    # Fill Email
    driver.find_element(By.ID, "userEmail").send_keys("john@example.com")

    # Select Gender
    driver.find_element(By.XPATH, "//label[text()='Male']").click()

    # Fill Mobile Number
    driver.find_element(By.ID, "userNumber").send_keys("9876543210")

    time.sleep(2)

    # Scroll Down (important for submit button)
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

    time.sleep(2)

    # Click Submit
    driver.find_element(By.ID, "submit").click()

    time.sleep(5)

    driver.quit()

    print("Automation Completed Successfully ✅")

@app.route("/")
def home():
    return "Server Running & Form Automation Executed ✅"

if __name__ == "__main__":
    threading.Thread(target=run_automation).start()
    app.run(debug=True)



```

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import os
import time

driver = webdriver.Chrome()
driver.maximize_window()
driver.implicitly_wait(10)

driver.get("https://www.ilovepdf.com/pdf_to_word")

file_path = os.path.abspath("d.pdf")

file_input = driver.find_element(By.XPATH, "//input[@type='file']")
file_input.send_keys(file_path)
print("Uploading PDF...")

convert_btn = driver.find_element(By.ID, "processTask")
convert_btn.click()
print("Converting to Word...")

time.sleep(15)

download_btn = driver.find_element(By.XPATH, "//a[contains(@class,'download')]")
download_btn.click()
print("Download started!")

time.sleep(5)
driver.quit()


```

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.maximize_window()

# ✅ Add Implicit Wait (applies globally)
driver.implicitly_wait(10)   # waits up to 10 seconds for elements

# Open local HTML file
driver.get("file:///C:/Users/LENOVO/Downloads/New%20folder%20(52)/a.html")

# Upload PDF (⚠ MUST use full absolute path)
upload = driver.find_element(By.ID, "pdfFile")
upload.send_keys("C:\\Users\\LENOVO\\Downloads\\New folder (52)\\d.pdf")

# Click Convert
driver.find_element(By.ID, "convertBtn").click()

# Click Download (implicit wait will handle delay)
driver.find_element(By.ID, "downloadBtn").click()

time.sleep(3)

driver.quit()

```

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.maximize_window()

# Directly open file using proper file URL
driver.get("file:///C:/Users/LENOVO/Downloads/New%20folder%20(52)/a.html")

time.sleep(2)

# Upload PDF (FULL ABSOLUTE PATH REQUIRED)
upload = driver.find_element(By.ID, "pdfFile")
upload.send_keys("C:\\Users\\LENOVO\\Downloads\\New folder (52)\\d.pdf")

# Click Convert
driver.find_element(By.ID, "convertBtn").click()

time.sleep(3)

# Click Download
driver.find_element(By.ID, "downloadBtn").click()

time.sleep(3)

driver.quit()


```
