# Module 1 – Testing Basics

## What is Software Testing?
Software Testing is the process of evaluating and verifying that a software application or system meets the specified requirements and works as expected. It ensures the quality, reliability, and performance of the software.

---

## Software Development Life Cycle (SDLC)
The **Software Development Life Cycle (SDLC)** is a systematic process for building software that ensures quality and correctness.  
Typical phases include:
- **Requirement Analysis** – Understanding what the user needs.
- **Design** – Planning the architecture and components.
- **Implementation / Coding** – Writing the actual code.
- **Testing** – Verifying that the software works correctly.
- **Deployment** – Releasing the software to users.
- **Maintenance** – Fixing issues and updating the software as needed.

<img width="650" height="381" alt="image" src="https://github.com/user-attachments/assets/60e1b201-ed5e-4bbd-b08c-2d977f226b73" />


---

## Software Testing Life Cycle (STLC)
The **Software Testing Life Cycle (STLC)** is a sequence of specific actions conducted during the testing process to ensure software quality.  
Key phases:
1. **Requirement Analysis** – Understanding testing requirements.
2. **Test Planning** – Defining the strategy, scope, resources, and schedule.
3. **Test Case Development** – Creating detailed test scenarios and cases.
4. **Environment Setup** – Preparing the test environment.
5. **Test Execution** – Running the tests.
6. **Defect Reporting & Tracking** – Logging and tracking defects.
7. **Test Closure** – Evaluating the testing process and reporting results.

---
<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/b65894de-31e2-45df-ab2a-1b3dedd2e5e3" />


## Types of Testing

### 1. Unit Testing
- Tests individual components or functions of the software.
- Ensures that each unit works correctly in isolation.

### 2. Integration Testing
- Verifies that different modules or components of the system interact correctly.
- Can be done as **Top-down**, **Bottom-up**, or **Big Bang** approach.

### 3. System Testing
- Validates the complete and integrated software system.
- Checks compliance with functional and non-functional requirements.

### 4. Regression Testing
- Ensures that recent code changes do not break existing functionality.
- Important when software is updated or modified.

### 5. Smoke Testing
- Quick, preliminary testing to check if the basic functionalities work.
- Often called **"Build Verification Testing"**.

---

## Manual vs Automation Testing

| Feature | Manual Testing | Automation Testing |
|---------|----------------|------------------|
| Execution | Performed manually by a tester | Performed using automated tools/scripts |
| Time | Time-consuming for large projects | Faster for repetitive tests |
| Accuracy | Prone to human error | High accuracy |
| Tools | None required | Selenium, QTP, TestComplete, etc. |
| Best Use | Exploratory, UI testing | Regression, load testing |

---

## Black Box vs White Box Testing

| Feature | Black Box Testing | White Box Testing |
|---------|-----------------|-----------------|
| Focus | Functionality of the software | Internal code structure |
| Knowledge Required | No knowledge of internal code | Requires coding knowledge |
| Test Cases | Based on requirements and specifications | Based on code logic and paths |
| Examples | Functional testing, UAT | Unit testing, Code coverage testing |

---

> **Note:** Understanding these basics is essential for ensuring software quality and delivering reliable applications.

# Module 2 – Testing Basics (Continued)

## Test Case Writing
A **test case** is a set of conditions or steps used to verify that a software feature works as expected.  
**Key components of a test case:**
- **Test Case ID** – Unique identifier for the test case.
- **Test Scenario** – The situation or functionality being tested.
- **Preconditions** – Conditions that must be met before executing the test.
- **Test Steps** – Step-by-step instructions to perform the test.
- **Expected Result** – The expected outcome of the test.
- **Actual Result** – The actual outcome after execution.
- **Status** – Pass/Fail based on comparison of expected vs actual results.

---

## Test Scenario
A **test scenario** is a high-level description of a functionality to be tested.  
- Represents a user story or a feature of the application.
- Each scenario can have multiple **test cases**.
- Helps in ensuring all functionalities are covered during testing.

---

## Bug Report Writing
A **bug report** is a document that records details of a defect found in the software.  
**Key elements of a bug report:**
- **Bug ID** – Unique identifier.
- **Summary** – Short description of the bug.
- **Steps to Reproduce** – Detailed steps to encounter the bug.
- **Expected Result** – What should happen.
- **Actual Result** – What actually happened.
- **Severity** – Impact of the bug on the system.
- **Priority** – Urgency of fixing the bug.
- **Environment** – Software version, OS, and other relevant setup.

---

## Severity vs Priority

| Aspect | Severity | Priority |
|--------|---------|----------|
| Definition | Indicates the impact of a bug on the system | Indicates the urgency to fix the bug |
| Focus | Effect on functionality | Scheduling and business needs |
| Levels | Critical, Major, Minor | High, Medium, Low |
| Example | Crash of the application = Critical | Cosmetic issue in UI = Low Priority |

---

## Agile Methodology
**Agile** is an iterative approach to software development and testing that emphasizes flexibility, collaboration, and customer feedback.  
**Key principles:**
- Iterative development with short cycles (**sprints**)
- Continuous collaboration between developers, testers, and stakeholders
- Adaptive planning and response to changes
- Regular delivery of working software

**Popular Agile Practices:**
- Scrum
- Kanban
- Extreme Programming (XP)

---

## Jira Basics
**Jira** is a project management tool widely used in Agile for tracking tasks, bugs, and progress.  
**Key Concepts:**
- **Project** – Container for all tasks and workflows.
- **Issue** – A single work item (can be a bug, task, or story).
- **Epic** – Large feature or initiative that can be broken into multiple issues.
- **Sprint** – Time-boxed iteration for completing a set of tasks.
- **Workflow** – Defines the states an issue goes through (To Do → In Progress → Done).

**Common Jira Actions:**
- Creating and assigning issues
- Updating issue status
- Adding comments and attachments
- Generating reports and dashboards


# Module 5 – Selenium Introduction

## What is Selenium?
**Selenium** is an open-source automation tool used for testing web applications across different browsers and platforms.  
**Key features:**
- Supports multiple programming languages (Python, Java, C#, etc.)
- Works across major browsers (Chrome, Firefox, Edge, Safari)
- Allows automation of repetitive web application tasks
- Supports parallel test execution

---

## WebDriver Architecture
Selenium WebDriver follows a client-server architecture:
1. **Client Library** – Your test script written in Python, Java, or other supported languages.
2. **JSON Wire Protocol** – Communication protocol between client and browser driver.
3. **Browser Driver** – Translates commands from WebDriver to the browser.
4. **Browser** – Executes the commands and returns the response to the client.

**Flow:**
Test Script → WebDriver API → Browser Driver → Browser → Response

---

## Browser Drivers
Browser drivers are specific to each browser and are required for Selenium WebDriver to interact with them.  
**Common browser drivers:**
- **ChromeDriver** – For Google Chrome
- **GeckoDriver** – For Mozilla Firefox
- **EdgeDriver** – For Microsoft Edge
- **SafariDriver** – For Safari

**Note:** Make sure the driver version matches the browser version.

---

## Installing Selenium
**Python Installation:**
```bash
pip install selenium
```


## example script

```python




```
