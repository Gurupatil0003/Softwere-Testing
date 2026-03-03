```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import os
import time

# Start browser
driver = webdriver.Chrome()
driver.maximize_window()

# Open iLovePDF PDF to Word tool
driver.get("https://www.ilovepdf.com/pdf_to_word")

time.sleep(3)

# Get absolute path of PDF
file_path = os.path.abspath("sample.pdf")  # Make sure this exists

# Find file upload input
file_input = driver.find_element(By.XPATH, "//input[@type='file']")

# Upload PDF
file_input.send_keys(file_path)

print("Uploading PDF...")

time.sleep(5)

# Click Convert button
convert_btn = driver.find_element(By.ID, "processTask")
convert_btn.click()

print("Converting to Word...")

time.sleep(10)

# Click Download button
download_btn = driver.find_element(By.XPATH, "//a[contains(@class,'download')]")
download_btn.click()

print("Download started!")

time.sleep(5)

driver.quit()
```
