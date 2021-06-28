# Test-Driven Development with FastAPI and Docker

![Continuous Integration and Delivery](https://github.com/sanggusti/fastapi-tdd/workflows/Continuous%20Integration%20and%20Delivery/badge.svg?branch=master)

## Overview

This project is delivering backend service of page summarizer using various stacks that are pivoting around `fastapi`, `docker`, `postgresql`, `pytest` and `nltk`. Dedicated to develop based on test driven as best practice in software development and also with Continuous Integration and Continuous Development.

## How to use

For development :

Simply clone, `docker-compose up -d --build` and redirect to http://localhost:8004/docs. To do unit test, execute `docker-compose exec python -m pytest`.

For usage as service :

-  Adding a new summary
```
$ http --json POST https://evening-brook-44287.herokuapp.com/summaries/ url=https://your_url.etc
```

example:
```
$ http --json POST http://localhost:8004/summaries/ url=http://testdriven.io

HTTP/1.1 201 Created
content-length: 34
content-type: application/json
date: Sun, 10 May 2020 15:59:54 GMT
server: uvicorn

{
    "id": 5,
    "url": "http://testdriven.io"
}
```
- Get the summary
```
$ http GET https://evening-brook-44287.herokuapp.com/summaries/{output_id}/
```
example
```
$ http GET http://localhost:8004/summaries/5/

HTTP/1.1 200 OK
content-length: 134
content-type: application/json
date: Sun, 10 May 2020 16:00:09 GMT
server: uvicorn

{
    "created_at": "2020-05-10T15:59:55.098074",
    "id": 5,
    "summary": "",
    "url": "http://testdriven.io"
}
```

feel free to try hit this service as api to your webapp!


## Objectives
- [x] Develop an asynchronous RESTful API with Python and FastAPI
- [x] Practice Test-Driven Development
- [x] Test a FastAPI app with pytest
- [x] Interact with a Postgres database asynchronously
- [x] Containerize FastAPI and Postgres inside a Docker container
- [x] Run unit and integration tests with code coverage inside a Docker container
- [x] Check your code for any code quality issues via a linter
- [x] Configure GitHub Actions for continuous integration and deployment
- [x] Use GitHub Packages to store Docker Images
- [x] Speed up a Docker-based CI build with Docker Cache
- [x] Deploy FastAPI, Uvicorn, and Postgres to Heroku with Docker
- [x] Parameterize test functions and mock functionality in tests with pytest
- [x] Run tests in parallel with pytest-xdist
- [x] Document a RESTful API with Swagger/OpenAPI
- [x] Run a background process outside the request/response flow


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