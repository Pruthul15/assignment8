# Assignment 8: FastAPI Calculator with Testing and CI/CD

A FastAPI calculator application with unit, integration, and end-to-end tests, comprehensive logging, and automated CI/CD pipeline.

**Author:** Pruthul Patel  
**Repository:** https://github.com/Pruthul15/assignment8  
**Docker Hub:** https://hub.docker.com/r/pruthul123/assignment8

---

## Features

- 4 arithmetic operations: add, subtract, multiply, divide
- RESTful API with FastAPI
- Interactive web-based calculator interface
- Unit tests (21), Integration tests (5), End-to-End tests (3)
- Comprehensive logging throughout application
- Automated CI/CD with GitHub Actions
- Docker containerization and deployment

---

## Installation

### Run with Docker

```bash
docker pull pruthul123/assignment8:latest
docker run -p 8000:8000 pruthul123/assignment8:latest
```

Open browser: http://localhost:8000

### Run Locally

```bash
git clone https://github.com/Pruthul15/assignment8.git
cd assignment8
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
playwright install
playwright install-deps
python main.py
```

---

## Usage

### Web Interface

1. Open http://localhost:8000
2. Enter two numbers
3. Click operation button (Add, Subtract, Multiply, Divide)
4. View result

Example:
```
10 + 5 = 15
10 - 5 = 5
10 × 5 = 50
10 ÷ 5 = 2
10 ÷ 0 = Error: Cannot divide by zero!
```

### API Usage

```bash
curl -X POST "http://localhost:8000/add" \
  -H "Content-Type: application/json" \
  -d '{"a": 10, "b": 5}'
```

Response: `{"result": 15.0}`

API Docs: http://localhost:8000/docs

---

## Project Structure

```
assignment8/
│
├── .github/
│   └── workflows/
│       └── test.yml                         # GitHub Actions CI/CD pipeline
│
├── app/
│   └── operations/
│       └── __init__.py                      # Arithmetic operations with logging
│
├── templates/
│   └── index.html                           # Web calculator interface
│
├── tests/
│   ├── unit/
│   │   ├── test_calculator.py               # Unit tests (21 tests)
│   │   └── conftest.py                      # Pytest fixtures
│   │
│   ├── integration/
│   │   └── test_fastapi_calculator.py       # API endpoint tests (5 tests)
│   │
│   └── e2e/
│       └── test_e2e.py                      # Playwright browser tests (3 tests)
│
├── htmlcov/                                 # Code coverage HTML reports
│
├── main.py                                  # FastAPI application entry point
├── Dockerfile                               # Docker container configuration
├── docker-compose.yml                       # Docker Compose orchestration
├── requirements.txt                         # Python dependencies
├── pytest.ini                               # Pytest configuration
├── .trivyignore                             # Security vulnerability exceptions
├── .gitignore                               # Git ignore patterns
├── LICENSE                                  # MIT License
└── README.md                                # Project documentation
---

## Testing

### Run Tests

```bash
pytest
```

**Results:** 29 tests passing, 100% coverage on operations

### Test Categories

**Unit Tests (21)** - Tests individual arithmetic operations  
**Integration Tests (5)** - Tests API endpoints  
**End-to-End Tests (3)** - Tests web interface with Playwright

---

## Logging

Logging implemented throughout application:

**Operations Module:**
- Logs each operation performed
- Logs results and errors
- Example: `INFO:app.operations:Performing addition: 10.0 + 5.0`

**Main Application:**
- Logs API requests/responses
- Logs validation errors
- Logs HTTP exceptions

---

## GitHub Actions CI/CD

Automated pipeline with 3 stages:

1. **Test** - Runs all 29 tests
2. **Security** - Scans for vulnerabilities with Trivy
3. **Deploy** - Builds and pushes to Docker Hub

View: https://github.com/Pruthul15/assignment8/actions

All stages passing ✓

---

## Git Version Control

Repository demonstrates:
- Regular commits with descriptive messages
- Clear development progression
- Proper .gitignore for Python

Example commits:
- "Initial commit: Base code for assignment 8"
- "Fix E2E tests by adding wait for async JavaScript results"
- "Add comprehensive logging to operations module"

---

## Assignment Requirements Checklist

**Submission Completeness (50 Points):**
- ✓ GitHub repository link provided
- ✓ All necessary files included
- ✓ Screenshot: GitHub Actions passing
- ✓ Screenshot: Application running in browser

**Functionality (50 Points):**
- ✓ FastAPI calculator runs without errors
- ✓ All arithmetic operations work correctly
- ✓ Unit tests implemented and passing (21 tests)
- ✓ Integration tests implemented and passing (5 tests)
- ✓ End-to-end tests implemented and passing (3 tests)
- ✓ All tests pass in GitHub Actions
- ✓ Logging implemented throughout

**Learning Outcome:**
- ✓ CLO10: Create, Consume and Test REST APIs using Python

---

## Technologies Used

- FastAPI - Web framework
- Pytest - Testing framework
- Playwright - Browser automation
- Docker - Containerization
- GitHub Actions - CI/CD
- Python 3.10

---

## Contact

**Student:** Pruthul Patel  
**Course:** IS 601 - Module 8  
**Repository:** https://github.com/Pruthul15/assignment8

---

**Author: Pruthul Patel - Assignment 8**