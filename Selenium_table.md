# Selenium Locators and WebElement Names

---

## 🔹 Selenium Locator Names

- ID  
- Name  
- Class Name  
- Tag Name  
- Link Text  
- Partial Link Text  
- CSS Selector  
- XPath  

---

## 🔹 WebElement Method Names

- click()  
- send_keys()  
- clear()  
- text  
- get_attribute()  
- is_displayed()  
- is_enabled()  
- is_selected()  
- submit()  

# Selenium Locators and WebElement Guide (Python)

---

## 🔹 1️⃣ Selenium Locators – Complete Table

| Locator Type | Syntax (Python) | When to Use | Example HTML | Notes |
|--------------|----------------|-------------|--------------|-------|
| ID | `driver.find_element(By.ID, "id_value")` | When element has unique id | `<input id="username">` | ✅ Fastest & Recommended |
| Name | `driver.find_element(By.NAME, "name_value")` | When name attribute is available | `<input name="email">` | ✅ Good alternative |
| Class Name | `driver.find_element(By.CLASS_NAME, "class_value")` | When class is unique | `<button class="btn-primary">` | ⚠ Avoid if class repeats |
| Tag Name | `driver.find_element(By.TAG_NAME, "tag")` | When targeting tag directly | `<input>` | ❌ Not preferred (multiple tags exist) |
| Link Text | `driver.find_element(By.LINK_TEXT, "Login")` | For exact link text | `<a>Login</a>` | ✅ Works only for `<a>` |
| Partial Link Text | `driver.find_element(By.PARTIAL_LINK_TEXT, "Log")` | When partial text is known | `<a>Login</a>` | ⚠ May match multiple links |
| CSS Selector | `driver.find_element(By.CSS_SELECTOR, "css")` | For flexible & fast selection | `input#username` | 🔥 Very Powerful |
| XPath | `driver.find_element(By.XPATH, "xpath")` | For complex or dynamic elements | `//input[@id='username']` | 💪 Most Powerful |

---

## 🔹 2️⃣ XPath vs CSS Selector – Comparison Table

| Feature | XPath | CSS Selector |
|----------|--------|--------------|
| Syntax Style | XML path style | CSS style |
| Performance | Slightly slower | Slightly faster |
| Supports Parent Traversal | ✅ Yes | ❌ No |
| Supports Text Matching | ✅ Yes (`text()`) | ❌ No |
| Complex Navigation | ✅ Yes | Limited |
| Recommended For | Dynamic & complex elements | General use |

---

## 🔹 3️⃣ WebElement Methods – Complete Table

| Method | Syntax | Purpose | Example |
|---------|--------|----------|----------|
| `click()` | `element.click()` | Click button/link | Clicking login button |
| `send_keys()` | `element.send_keys("text")` | Enter text | Enter username |
| `clear()` | `element.clear()` | Clear input field | Remove old text |
| `text` | `element.text` | Get visible text | Get label text |
| `get_attribute()` | `element.get_attribute("attr")` | Get attribute value | Get value, href |
| `is_displayed()` | `element.is_displayed()` | Check visibility | Returns True/False |
| `is_enabled()` | `element.is_enabled()` | Check if enabled | Returns True/False |
| `is_selected()` | `element.is_selected()` | Check checkbox/radio | Returns True/False |
| `submit()` | `element.submit()` | Submit form | Submit form directly |

---

## 🔹 4️⃣ find_element vs find_elements

| Feature | `find_element()` | `find_elements()` |
|-----------|----------------|-----------------|
| Return Type | Single WebElement | List of WebElements |
| If Not Found | Throws Exception | Returns Empty List |
| Use Case | Single element | Multiple elements |
| Example | `driver.find_element(By.ID, "username")` | `driver.find_elements(By.CLASS_NAME, "item")` |

---

## 🔹 5️⃣ Locator Priority (Best Practice Order)

| Priority | Locator |
|----------|----------|
| 1 | ID |
| 2 | Name |
| 3 | CSS Selector |
| 4 | XPath |
| 5 | Class Name (if unique) |
| 6 | Tag Name |

---

## 🔹 6️⃣ Common XPath Examples Table

| Purpose | XPath |
|----------|--------|
| By ID | `//input[@id='username']` |
| By Name | `//input[@name='email']` |
| By Class | `//div[@class='container']` |
| By Text | `//a[text()='Login']` |
| Contains Attribute | `//input[contains(@id,'user')]` |
| Starts With | `//input[starts-with(@id,'user')]` |
| Parent | `//input[@id='username']/..` |
| Child | `//div[@class='box']//button` |

---

## 🚀 Basic Import Setup

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://example.com")

```


https://demoqa.com/automation-practice-form
