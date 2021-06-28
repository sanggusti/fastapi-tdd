# Test-Driven Development with FastAPI and Docker

![Continuous Integration and Delivery](https://github.com/sanggusti/fastapi-tdd/workflows/Continuous%20Integration%20and%20Delivery/badge.svg?branch=master)

## Overview

This project is delivering backend service of page summarizer using various stacks that are pivoting around `fastapi`, `docker`, `postgresql`, `pytest` and `nltk`. Dedicated to develop based on test driven as best practice in software development and also with Continuous Integration and Continuous Development.

## How to use

Simply clone, `docker-compose up -d --build` and redirect to http://localhost:8004/docs.

To do unit test, execute `docker-compose exec python -m pytest`.

## Project Structure

```
├── .github
│   └── workflows
│       └── main.yml
├── .gitignore
├── README.md
├── docker-compose.yml
├── project
│   ├── .coverage
│   ├── .coveragerc
│   ├── .dockerignore
│   ├── Dockerfile
│   ├── Dockerfile.prod
│   ├── app
│   │   ├── __init__.py
│   │   ├── api
│   │   │   ├── __init__.py
│   │   │   ├── crud.py
│   │   │   ├── ping.py
│   │   │   └── summaries.py
│   │   ├── config.py
│   │   ├── db.py
│   │   ├── main.py
│   │   ├── models
│   │   │   ├── __init__.py
│   │   │   ├── pydantic.py
│   │   │   └── tortoise.py
│   │   └── summarizer.py
│   ├── db
│   │   ├── Dockerfile
│   │   └── create.sql
│   ├── entrypoint.sh
│   ├── htmlcov
│   ├── requirements-dev.txt
│   ├── requirements.txt
│   ├── setup.cfg
│   └── tests
│       ├── __init__.py
│       ├── conftest.py
│       ├── test_ping.py
│       ├── test_summaries.py
│       └── test_summaries_unit.py
└── release.sh
```