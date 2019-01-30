---
title: "Building an API with R and Plumber"
subjects: ['R']
subjects_weight: 120
draft: false
---

[Plumber](https://www.rplumber.io/) is a package which makes it possible to expose R functions as API endpoints. This makes building an API simple and fun.

- What is a REST API?
- A Quick API
  - Function decoration
  - Input and output
  - [Swagger](https://swagger.io/)
- Input
  - Types of endpoints (mostly `GET` and `POST` but also `PUT`, `DELETE` and `HEAD`)
  - Filters
  - Dynamic routing
  - Parameters
  - The request object
  - JSON input
- Output
  - The response object
  - Types of output (mostly JSON but also HTML, JPG, PNG and PDF)
  - Serving static files
  - Dealing with Errors
- Documentation
- Security
- Deploying an API
  - DigitalOcean and AWS
  - Docker
