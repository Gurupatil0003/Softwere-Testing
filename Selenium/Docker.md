# 🐳 Docker Beginner Practice Guide

---


## Docdker install 

#### Open Powershell as Administaritor

```python


##run this cmd

wsl --installl

```

 ## Goo to docker website click the link below 

https://docs.docker.com/desktop/setup/install/windows-install/

choose the Docker Desktop for Windows - x86_64


0
# After that u can work on the below commands

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

 

## 🧱 STEP 0 — Check Docker Is Installed

Open terminal and run:

    docker --version

- If it prints a version → Docker is installed.
- If not → Install Docker Desktop first.

---

## 🟢 STEP 1 — Run Your First Container (No Code)

Run:

    docker run hello-world

### What Happens?

Docker will:

- Download the image
- Create a container
- Run it
- Print a message
- Stop the container

You just created and ran your first container 🎉

### Check Images

    docker images

You should see:

    hello-world

That is an image.

### Check Containers

    docker ps -a

You will see a stopped container.

---

## 🟢 STEP 2 — Run a Real Linux Machine Inside Docker

Run:

    docker run -it ubuntu bash

Now you are inside a Linux container.

Try:

    ls
    pwd

You are inside a mini OS.

Exit:

    exit

Container stops.

---

## 🟢 STEP 3 — Create Your Own Image

### 1️⃣ Create Folder

    mkdir docker-practice
    cd docker-practice

### 2️⃣ Create app.py

Create a file named `app.py` and add:

```python
print("Docker is easy 🚀")
```

## 3️⃣ Create Dockerfile

Create a file named `Dockerfile` (no extension).

Add the following:

```dockerfile
FROM python:3.10
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

## 🟢 STEP 4 — Build Your Image

Inside the folder run:

```bash
docker build -t myapp .
```

### 🔍 Check Images

Run:

```bash
docker images
```

## 🟢 STEP 5 — Run Container From Your Image

```bash
docker run myapp
```
Output:

Docker is easy 🚀

That is your container running.

## 🧠 What Just Happened?

- Dockerfile → Blueprint  
- docker build → Creates image  
- docker run → Creates container  

Image = Template  
Container = Running instance


## 🟢 STEP 6 — See Containers

### Running containers:

```bash
docker ps
```
All containers (including stopped):

```python
docker ps -a
```

## 🟢 STEP 7 — Remove Container

### Find container ID:

```bash
docker ps -a
```
Then:
```python
docker rm <container_id>
```
### 🟢 STEP 8 — Remove Image
```python
docker rmi myapp
```

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
import time


# ---------- FIXTURE ----------
@pytest.fixture
def driver():
    chrome_options = Options()
    chrome_options.add_argument("--headless")
    chrome_options.add_argument("--no-sandbox")
    chrome_options.add_argument("--disable-dev-shm-usage")

    driver = webdriver.Chrome(options=chrome_options)
    driver.maximize_window()
    yield driver
    driver.quit()


# ---------- TEST CASE ----------
def test_tutorialsninja_order(driver):

    # Open website
    driver.get("https://tutorialsninja.com/demo/")
    time.sleep(2)

    # Search for MacBook
    driver.find_element(By.NAME, "search").send_keys("MacBook")
    driver.find_element(By.CSS_SELECTOR, "button.btn.btn-default.btn-lg").click()
    time.sleep(2)

    print("Search Completed")

    # Click first product
    driver.find_element(By.LINK_TEXT, "MacBook").click()
    time.sleep(2)

    # Add to cart
    driver.find_element(By.ID, "button-cart").click()
    time.sleep(2)

    print("Product Added to Cart")

    # Open cart dropdown
    driver.find_element(By.ID, "cart-total").click()
    time.sleep(2)

    driver.find_element(By.XPATH, "//strong[text()='View Cart']").click()
    time.sleep(2)

    # Assertion
    product_name = driver.find_element(By.LINK_TEXT, "MacBook").text
    assert "MacBook" in product_name

    print("Product Verified in Cart")


```


```python

FROM python:3.10-slim

RUN apt-get update && apt-get install -y chromium chromium-driver

WORKDIR /app
COPY . .

RUN pip install -r requirements.txt

CMD ["pytest", "-v"]
```

```python

selenium
pytest
```

```python
docker build -t selenium-wiki .

docker run selenium-wiki

```



## today docker code for wikipedia
```

```python

from selenium import webdriver
from selenium.webdriver.chrome.options import Options

options = Options()
options.add_argument("--headless")
options.add_argument("--no-sandbox")
options.add_argument("--disable-dev-shm-usage")

driver = webdriver.Chrome(options=options)

driver.get("https://www.wikipedia.org")

print(driver.title)
driver.quit()
```

```python
FROM selenium/standalone-chrome

WORKDIR /app
COPY . /app

RUN pip3 install selenium

CMD ["python3","script.py"]
```


```python

docker build -t selenium-test .
```

```python

docker run selenium-test 
```
