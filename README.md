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
