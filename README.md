# Sequence Calculator API

![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk&logoColor=white)
![Quarkus](https://img.shields.io/badge/Quarkus-3-4695EB?logo=quarkus&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-Build-C71A36?logo=apachemaven&logoColor=white)
![Swagger](https://img.shields.io/badge/OpenAPI-Swagger-85EA2D?logo=swagger&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-Container-2496ED?logo=docker&logoColor=white)

REST API built with Quarkus to calculate a numeric sequence with in-memory caching and OpenAPI documentation.

## Project Goal

This project was created as a technical exercise to demonstrate backend development with Quarkus, REST APIs, caching, API documentation, and containerized execution.

## Stack

- Java
- Quarkus
- Maven
- SmallRye OpenAPI / Swagger UI
- Docker

## Features

- Calculate sequence values through a REST endpoint
- In-memory caching for repeated requests
- OpenAPI documentation with Swagger UI
- Dockerized execution
- Local development with hot reload

## Endpoints

- `GET /labseq/{n}`  
  Calculates the sequence value for `n`

- `GET /labseq/clean-cache`  
  Clears the in-memory cache

## Example Response

```json
{
  "transactionTime": 3,
  "error": "",
  "result": "12"
}
```

## Running Locally

```bash
./mvnw quarkus:dev
```

The API will be available at:

- `http://localhost:8080/labseq/{n}`
- `http://localhost:8080/labseq/clean-cache`

Swagger UI:

- `http://localhost:8080/swagger-ui`

OpenAPI spec:

- `http://localhost:8080/openapi`

## Running with Docker

Build the image:

```bash
docker build -t sequence-calculator-api .
```

Run the container:

```bash
docker run --rm -p 8080:8080 sequence-calculator-api
```

## Technical Notes

- The API uses in-memory caching to avoid recalculating previously requested values.
- `transactionTime` represents execution time in milliseconds.
- For large calculations, the response may include an error message if execution exceeds the allowed time.
- All JSON responses are returned through a dedicated DTO.

## Notes

- This repository is kept as a technical sample project.
- The main focus is backend implementation and API behavior rather than product-level UI or persistence.
