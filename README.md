Assignment 8: FastAPI Calculator with Testing and CI/CD

A FastAPI calculator application with comprehensive testing, logging, and automated CI/CD pipeline.

Author: Pruthul Patel
Repository: https://github.com/Pruthul15/assignment8
Docker Hub: https://hub.docker.com/r/pruthul123/assignment8

Features
- 4 arithmetic operations: add, subtract, multiply, divide
- RESTful API with FastAPI
- Interactive web-based calculator interface
- Comprehensive logging throughout application
- Unit, Integration, and End-to-End tests
- Automated CI/CD with GitHub Actions
- Docker containerization and deployment
- 29 tests with 100% coverage on operations module

Installation Instructions

1. Run with Docker (Recommended)

docker pull pruthul123/assignment8:latest
docker run -p 8000:8000 pruthul123/assignment8:latest

Open browser: http://localhost:8000

2. Run Locally

git clone https://github.com/Pruthul15/assignment8.git
cd assignment8
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
playwright install
playwright install-deps
python main.py

Usage Guide

Using the Web Interface:

1. Open http://localhost:8000 in your browser
2. Enter two numbers in the input fields
3. Click operation button (Add, Subtract, Multiply, Divide)
4. View result displayed on the page

Example Session:

Enter first number: 10
Enter second number: 5
Click "Add" button
Result: Calculation Result: 15

Click "Divide" button
Result: Calculation Result: 2

Enter second number: 0
Click "Divide" button
Result: Error: Cannot divide by zero!

Using the API:

curl -X POST "http://localhost:8000/add" \
  -H "Content-Type: application/json" \
  -d '{"a": 10, "b": 5}'
Response: {"result": 15.0}

curl -X POST "http://localhost:8000/divide" \
  -H "Content-Type: application/json" \
  -d '{"a": 10, "b": 0}'
Response: {"error": "Cannot divide by zero!"}

Project Structure

Project Structure

assignment8/
├── .github/
│   └── workflows/
│       └── test.yml             # CI/CD pipeline configuration
├── app/
│   └── operations/
│       ├── __pycache__/
│       └── __init__.py          # Arithmetic operations with logging
├── htmlcov/                     # Code coverage HTML reports
│   ├── class_index.html
│   ├── function_index.html
│   ├── index.html
│   ├── status.json
│   ├── style_cb_8e611ae1.css
│   └── z_053b8412cf8b8a96___init___py.html
├── templates/
│   └── index.html               # Web interface (HTML/CSS/JavaScript)
├── tests/
│   ├── e2e/
│   │   ├── __pycache__/
│   │   ├── __init__.py
│   │   └── test_e2e.py          # Playwright browser automation tests
│   ├── integration/
│   │   ├── __pycache__/
│   │   └── test_fastapi_calculator.py  # FastAPI endpoint tests
│   └── unit/
│       ├── __pycache__/
│       ├── __init__.py
│       ├── test_calculator.py   # Unit tests for operations
│       └── conftest.py          # Pytest fixtures
├── venv/                        # Virtual environment (not in repo)
├── .coverage                    # Coverage data file
├── .gitignore                   # Git ignore rules
├── .trivyignore                 # Security scan exceptions
├── docker-compose.yml           # Docker Compose orchestration
├── Dockerfile                   # Docker container configuration
├── LICENSE                      # MIT License
├── main.py                      # FastAPI application entry point
├── pytest.ini                   # Pytest configuration
├── README.md                    # This file
└── requirements.txt             # Python dependencies


Logging Implementation

The application implements comprehensive logging to track operations and errors:

Operations Module (app/operations/__init__.py):
- Logs each arithmetic operation performed
- Logs operation results
- Logs errors (e.g., division by zero attempts)

Main Application (main.py):
- Logs API requests and responses
- Logs validation errors
- Logs HTTP exceptions

Example Log Output:

INFO:app.operations:Performing addition: 10.0 + 5.0
INFO:app.operations:Addition result: 15.0
INFO:app.operations:Performing division: 10.0 / 0
ERROR:app.operations:Division by zero attempted: 10.0 / 0

Testing

Run Tests

pytest                          # Run all tests
pytest -v                       # Verbose output
pytest tests/unit/              # Unit tests only
pytest tests/integration/       # Integration tests only
pytest tests/e2e/               # E2E tests only

Test Coverage

Total Tests: 29 (21 unit + 5 integration + 3 E2E)
Coverage: 100% on operations module
Test Files: 3 comprehensive test modules

Test Breakdown:

Unit Tests (tests/unit/test_calculator.py):
- Tests add, subtract, multiply, divide functions
- Validates error handling for division by zero
- Tests input validation
- Uses parameterized tests for multiple scenarios

Integration Tests (tests/integration/test_fastapi_calculator.py):
- Tests /add, /subtract, /multiply, /divide endpoints
- Validates request/response handling
- Tests error responses (400, 500 status codes)
- Validates JSON response format

End-to-End Tests (tests/e2e/test_e2e.py):
- Uses Playwright to simulate real user interactions
- Tests web interface functionality
- Validates calculator operations in browser
- Tests error message display

CI/CD with GitHub Actions

Automated pipeline runs on every push:

Stage 1: Test
- Sets up Python 3.10 environment
- Installs dependencies
- Runs all 29 tests with coverage
- Status: ✓ Passing

Stage 2: Security Scan
- Builds Docker image
- Runs Trivy vulnerability scanner
- Checks for critical vulnerabilities
- Status: ✓ Passing

Stage 3: Deploy
- Builds multi-platform Docker image
- Tags with 'latest' and git SHA
- Pushes to Docker Hub automatically
- Status: ✓ Passing

View workflow: .github/workflows/test.yml
Check status: https://github.com/Pruthul15/assignment8/actions

Git Version Control

Repository demonstrates proper Git practices:
- Regular commits with descriptive messages
- Clear development progression
- Proper .gitignore for Python projects

Example Commit Messages:
- "Initial commit: Base code for assignment 8 from module 8"
- "Fix E2E tests by adding wait for async JavaScript results"
- "Configure Trivy to report but not fail on vulnerabilities"
- "Personalize application with custom branding and documentation"
- "Add comprehensive README documentation"

Docker Deployment

Build and Run:

docker build -t pruthul123/assignment8:latest .
docker run -p 8000:8000 pruthul123/assignment8:latest

Image Details:
- Base Image: python:3.10-slim
- Exposed Port: 8000
- Platforms: linux/amd64, linux/arm64
- User: Non-root appuser

Requirements

Python 3.10
FastAPI
Uvicorn
Pydantic
Pytest
Playwright
Docker

Author

Pruthul Patel
IS 601 - Module 8 Assignment