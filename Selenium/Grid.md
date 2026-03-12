```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PDF to Word Converter</title>

    <!-- Bootstrap 5 CDN -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

    <style>
        body {
            background: linear-gradient(to right, #4e73df, #1cc88a);
            height: 100vh;
        }

        .card {
            border-radius: 15px;
        }

        #downloadBtn {
            display: none;
        }

        .progress {
            height: 20px;
            display: none;
        }
    </style>
</head>
<body class="d-flex align-items-center justify-content-center">

<div class="container">
    <div class="row justify-content-center">
        <div class="col-md-6">
            <div class="card shadow-lg p-4">
                <h3 class="text-center mb-4">PDF to Word Converter</h3>

                <div class="mb-3">
                    <label class="form-label">Upload PDF File</label>
                    <input class="form-control" type="file" id="pdfFile" accept=".pdf">
                </div>

                <div class="d-grid gap-2">
                    <button id="convertBtn" class="btn btn-success" onclick="convertFile()">
                        Convert to Word
                    </button>

                    <div class="progress mt-3" id="progressBar">
                        <div class="progress-bar progress-bar-striped progress-bar-animated"
                             role="progressbar"
                             style="width: 0%"
                             id="progressFill">
                        </div>
                    </div>

                    <button id="downloadBtn" class="btn btn-primary mt-3" onclick="downloadFile()">
                        Download Word File
                    </button>
                </div>

                <div id="status" class="text-center mt-3 fw-bold"></div>
            </div>
        </div>
    </div>
</div>

<script>
    function convertFile() {
        let fileInput = document.getElementById("pdfFile");
        let status = document.getElementById("status");
        let progressBar = document.getElementById("progressBar");
        let progressFill = document.getElementById("progressFill");
        let downloadBtn = document.getElementById("downloadBtn");

        if (fileInput.files.length === 0) {
            alert("Please upload a PDF file.");
            return;
        }

        progressBar.style.display = "block";
        status.innerText = "Converting...";

        let width = 0;
        let interval = setInterval(function () {
            if (width >= 100) {
                clearInterval(interval);
                status.innerText = "Conversion Successful!";
                downloadBtn.style.display = "block";
            } else {
                width += 10;
                progressFill.style.width = width + "%";
            }
        }, 200);
    }

    function downloadFile() {
        const element = document.createElement("a");
        const file = new Blob(["This is a dummy Word file for Selenium automation testing."],
            {type: "application/msword"});
        element.href = URL.createObjectURL(file);
        element.download = "converted.doc";
        document.body.appendChild(element);
        element.click();
        document.body.removeChild(element);
    }
</script>

</body>
</html>



```



```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
import time
import os


driver = webdriver.Chrome()
driver.maximize_window()

# Open the HTML file
html_file = "file://" + os.path.abspath("index.html")
driver.get(html_file)

time.sleep(2)  # wait for page to load

# Upload PDF
upload = driver.find_element(By.ID, "pdfFile")
upload.send_keys(os.path.abspath("d.pdf"))

time.sleep(1)

# Click Convert
convert_btn = driver.find_element(By.ID, "convertBtn")
convert_btn.click()

time.sleep(3)  # wait for conversion to "finish"

# Click Download
download_btn = driver.find_element(By.ID, "downloadBtn")
download_btn.click()

time.sleep(1)

driver.quit()
print("Automation Completed Successfully")



```


### version chnage

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options as ChromeOptions
from selenium.webdriver.edge.options import Options as EdgeOptions
import time
import os

GRID_URL = "http://localhost:4444"

# Chrome driver
chrome_driver = webdriver.Remote(
    command_executor=GRID_URL,
    options=ChromeOptions()
)

# Edge driver
edge_driver = webdriver.Remote(
    command_executor=GRID_URL,
    options=EdgeOptions()
)

# List of browsers
drivers = [chrome_driver, edge_driver]

for driver in drivers:

    driver.maximize_window()

    # Open HTML file
    html_file = "file://" + os.path.abspath("index.html")
    driver.get(html_file)

    time.sleep(2)

    # Upload PDF
    upload = driver.find_element(By.ID, "pdfFile")
    upload.send_keys(os.path.abspath("d.pdf"))

    time.sleep(1)

    # Click Convert
    convert_btn = driver.find_element(By.ID, "convertBtn")
    convert_btn.click()

    time.sleep(3)

    # Click Download
    download_btn = driver.find_element(By.ID, "downloadBtn")
    download_btn.click()

    time.sleep(1)

    driver.quit()

print("Automation Completed Successfully")

```

```python
java -jar selenium-server-4.41.0.jar
```
