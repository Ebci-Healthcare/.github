# Hospital Management System

> A full-stack hospital management application built with Spring Boot (Java 17), PostgreSQL (Docker), and Next.js (Node 18.20.2).

---

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Prerequisites](#prerequisites)  
3. [Getting Started](#getting-started)  
   - [Import Database (ongoing)](#import-database-ongoing)  
   - [Run PostgreSQL DB](#run-postgresql-db)  
   - [Rebuild the DB Container](#rebuild-the-db-container)  
   - [Run the Backend](#run-the-backend)  
   - [Run the Frontend](#run-the-frontend)  
4. [Directory Structure](#directory-structure)  
5. [Configuration](#configuration)  
6. [Generating the API Client](#generating-the-api-client)  
7. [EBCI Developer Guidelines](#ebci-developer-guidelines)  
8. [Swagger Documentation](#swagger-documentation)  
9. [Todos](#todos)  
10. [License](#license)

---

## Project Overview

This repository contains two main components:

- **Backend**: Spring Boot 3.4.5 application packaged as a Docker image, exposing a REST-ful API for hospital data management.  
- **Frontend**: Next.js application (Node 18.20.2 + Tailwind) consuming the backend API.

---

## Prerequisites

- **Java 17 (JDK)**  
- **Docker** (Engine & CLI)  
- **Node.js 18.20.2**  
- **pnpm** (as package manager for the frontend/API client)

---

## Getting Started

### Import Database (ongoing)

> ⚠️ _Import scripts and seed data are a work in progress._

---

### Run PostgreSQL DB

1. **Build the image**  
   ```bash
   docker build -t hospital-postgres:15 .


2. **Run the container**

docker run -d \
  --name hospital-pg \
  -p 5432:5432 \
  hospital-postgres:15

3. **Access via psql**
   
psql -U app -d hospital
# then list tables:
\dt

### Rebuild the DB Container

1. **Stop & remove old container**
   
docker rm -f hospital-pg

2. **Run updated image**  
docker run -d \
  --name hospital-pg \
  -p 5432:5432 \
  hospital-postgres:15

### Run the Backend

1. **Build**
docker build -t hospital-backend:latest .
2. **Run**
docker run -d \
  --name hospital-backend \
  -p 8091:8091 \
  --env-file ./env.list \
  hospital-backend:latest

### Run the Frontend

1. **Build**
docker build -t hospital-frontend .
2. **Run**
docker run -d \
  --name frontend \
  -p 3000:3000 \
  hospital-frontend

### Generating the API Client

pnpm dlx @openapitools/openapi-generator-cli generate \
  -i http://localhost:8091/v3/api-docs \
  -g typescript-axios \
  -o ./src/api
### EBCI Developer Guidelines

All contributors must follow these “commandments”:

1. **Branch Naming**
Name branches after Linear ticket IDs (e.g. EB-123).

2. **Exception Handling**
Cover all edge cases; surface meaningful HTTP errors.

3. **Swagger Docs**
Document every endpoint, including request/response schemas.

4. **Roles & Permissions**
Annotate backend controllers with @PreAuthorize.

5. **Frontend Pagination**
All lists must support server-side pagination.
   
6. **Responsive UI**
Mobile-first design using Tailwind.
   
7. **Internationalization (i18n)**

No hard-coded text—use translation files everywhere.
8. **Typography Component**
Consistent text styles via a shared component.

9. **React Query**
Fetch and cache all API calls with React Query.

10. **Default Credentials**
Username: admin  
Password: admin
