# docker-airflow

A fork of [puckel/docker-airflow](https://github.com/puckel/docker-airflow), with added [`codeql`](https://github.com/github/codeql-cli-binaries) goodness. 

Currently contains the packages needed to build **Python** and **JavaScript** databases.

## Information

* Based on Python (3.7-slim-stretch) official Image [python:3.7-slim-stretch](https://hub.docker.com/_/python/) and uses the official [Postgres](https://hub.docker.com/_/postgres/) as backend and [Redis](https://hub.docker.com/_/redis/) as queue
* Install [Docker](https://www.docker.com/)
* Install [Docker Compose](https://docs.docker.com/compose/install/)
* Following the Airflow release from [Python Package Index](https://pypi.python.org/pypi/apache-airflow)
* [LTS version of `node.js`](https://hub.docker.com/_/node)

## Installation

Pull the image from the Docker repository.

```bash
docker pull annarailton/airflow-codeql-js-py
```

## Build

This uses a chain of docker images, starting from `node:lts-slim`. 
```bash
docker build -t annarailton/node-lts-python3.7-slim node-lts-python3.7-slim
docker build -t annarailton/node-lts-python3.7-slim-codeql node-lts-python3.7-slim-codeql
docker build -t annarailton/airflow-codeql-js-py .
```

Or 
```bash
docker build -t annarailton/airflow_codeql https://github.com/annarailton/docker-airflow.git
```

## Usage

By default, docker-airflow runs Airflow with **SequentialExecutor** :
```bash
docker run -d -p 8081:8080 annarailton/airflow-codeql-js-py webserver
```
If you want to run with `LocalExecutor` (recommended as then you get a proper database behind it), do 

```bash
docker-compose up -d
```
For other instructions, see the [original repo](https://github.com/puckel/docker-airflow) for this fork.
