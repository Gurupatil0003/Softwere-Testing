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

