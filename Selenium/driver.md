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
