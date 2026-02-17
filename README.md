# 🎓 ilm-boot – Academic Document Sharing Platform

## **Project Description**

**ilm-boot** is a web application designed for students to **share, search, and access academic resources** such as notes, past papers, assignments, and quizzes. Students can **upload PDFs**, rate documents, leave comments, and generate AI-powered summaries of academic documents.

The goal is to **centralize study materials** and create a collaborative academic environment where students can **easily find and share resources**, improving learning efficiency.

**Key Features:**

* Upload academic documents (PDF) with metadata: name, type, course, teacher.
* Search documents using filters: teacher, course, document type, keywords.
* Download PDFs directly.
* Comment and rate documents.
* AI-powered summaries for documents (via Google AI).
* JWT-based authentication and authorization.
* Paginated results for better performance.

**Tech Stack:**

* **Backend:** Java Spring Boot, Spring Data JPA, PostgreSQL, Spring AI
* **Frontend:** React
* **Security:** Spring Security + JWT
* **File Storage:** Local filesystem for PDF uploads
* **AI Integration:** Google AI for automatic summaries

---

## **Table of Contents**

* [Project Description](#project-description)
* [Features](#features)
* [Installation](#installation)
* [Environment Setup](#environment-setup)
* [API Endpoints](#api-endpoints)
* [Testing](#testing)

---

## **Features**

1. **User Authentication & Authorization**

   * JWT-based login and registration
   * Secure endpoints for uploading documents, commenting, and rating

2. **Document Management**

   * Upload PDF files with document metadata
   * Download documents
   * Paginated listing of all documents

3. **Search & Filter**

   * Filter by teacher, course, document type, or keywords
   * Dynamic search using Spring Data JPA Specification

4. **Comments & Ratings**

   * Comment on documents
   * Rate documents (1–5 stars)
   * View average rating per document

5. **AI Summaries**

   * Generate short summaries of documents automatically

---

## **Installation**

1. **Clone the Repository**

```bash
git clone https://github.com/ShahidOulanMansha786/ilm-boot.git
cd ilm-boot
```

2. **Set up the Database**

* Install PostgreSQL
* Create a database:

```sql
CREATE DATABASE ilm_boot;
```

* Update `application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ilm_boot
spring.datasource.username=postgres
spring.datasource.password=<your-password>
spring.jpa.hibernate.ddl-auto=update
```

3. **Run Backend**

```bash
./mvnw spring-boot:run
```

Or in IDE (VS Code / IntelliJ) → Run `IlmbootApplication.java`

4. **Upload Directory**

* PDFs are stored locally by default: `uploads/` folder at project root
* Make sure this folder exists:

```bash
mkdir uploads
```

---

## **Environment Setup**

* Java 21+
* Maven 4+
* PostgreSQL 15+
* Optional: Postman for API testing

---

## **API Endpoints**

### **Auth**

| Method | Endpoint         | Description             |
| ------ | ---------------- | ----------------------- |
| POST   | `/auth/register` | Register new user       |
| POST   | `/auth/login`    | Login and get JWT token |

### **Documents**

| Method | Endpoint                       | Description                                     |
| ------ | ------------------------------ | ----------------------------------------------- |
| POST   | `/api/documents`               | Upload a document                               |
| GET    | `/api/documents`               | Get all documents (paginated)                   |
| GET    | `/api/documents/search`        | Search documents                                |
| GET    | `/api/documents/download/{id}` | Download PDF by ID                              |
| GET    | `/api/documents/{id}/summary`  | Generate and return AI summary for the document |

### **Comments**

| Method | Endpoint                     | Description                     |
| ------ | ---------------------------- | ------------------------------- |
| POST   | `/api/comments/{documentId}` | Add comment to a document       |
| GET    | `/api/comments/{documentId}` | Get all comments for a document |

### **Ratings**

| Method | Endpoint                                  | Description                        |
| ------ | ----------------------------------------- | ---------------------------------- |
| POST   | `/api/ratings/{documentId}?ratingValue=5` | Rate a document (1–5)              |
| GET    | `/api/ratings/{documentId}`               | Get average rating & total ratings |

---

## **Testing**

1. Register a user → login → get JWT token
2. Use JWT token in `Authorization` header for protected endpoints:

```
Authorization: Bearer <token>
```

3. Upload PDF → check `/api/documents` → download file
4. Add comments and ratings → check results → test AI summary generation

---

