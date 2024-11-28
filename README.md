# JWT User Authentication API

## Description
**JWT User Authentication API** is a Spring Boot project designed to manage user authentication and authorization using JSON Web Tokens (JWT). It provides endpoints for user registration and login, leveraging Spring Security for secure access control. The API supports role-based access and is structured to ensure scalability and maintainability.

## Table of Contents

- [Description](#description)
- [How to Use](#how-to-use)
- [Features](#features)
- [Dependencies](#dependencies)
- [Execution](#execution)
- [API Endpoints](#api-endpoints)

## How to Use

### 1. Clone the Repository
Clone the repository to your local machine:
```bash
git clone <repository-link>
```

### 2. Open in an IDE
Open the project in your preferred IDE (e.g., IntelliJ IDEA, Eclipse). Ensure Maven is configured to manage dependencies.

### 3. Configure the Application
Update the `application.properties` file with your database credentials and other necessary configurations. Example:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/testedb
spring.datasource.username=postgres
spring.datasource.password=postgres
spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update

# App Properties
bezkoder.app.jwtSecret=bezKoderSecretKey
bezkoder.app.jwtExpirationMs=86400000
```

### 4. Run the Application
Start the Spring Boot application using your IDE or the terminal:
```bash
mvn spring-boot:run
```

### 5. Test the API
Use tools like Postman or curl to interact with the API.

## Features

- **JWT-Based Authentication**: Secure authentication using JSON Web Tokens.
- **User Registration**: Create new user accounts with role-based access control.
- **Login Endpoint**: Authenticate users and issue JWT tokens.
- **Role Management**: Assign roles (e.g., USER, ADMIN) to control access.

## Dependencies

The project relies on the following dependencies:

- `spring-boot-starter-security` (for authentication and authorization)
- `spring-boot-starter-data-jpa` (for database interaction)
- `spring-boot-starter-web` (for REST API development)
- `jjwt` (for JWT generation and validation)

Ensure these dependencies are included in the `pom.xml` file.

## Execution

### From an IDE

1. Open the project in your IDE.
2. Locate the main class `JwtAuthenticationApplication`.
3. Run the application directly from the IDE.

### From the Command Line

1. Package the application:
   ```bash
   mvn clean package
   ```

2. Run the packaged application:
   ```bash
   java -jar target/<your-application>.jar
   ```

## API Endpoints

### **Authentication Endpoints**

- **POST** `/api/auth/signin`
  - **Description**: Authenticate a user and return a JWT token.
  - **Request Body**:
    ```json
    {
      "username": "user1",
      "password": "password123"
    }
    ```
  - **Response**:
    ```json
    {
      "token": "jwt-token",
      "id": 1,
      "username": "user1",
      "email": "user1@example.com",
      "roles": ["ROLE_USER"]
    }
    ```

- **POST** `/api/auth/signup`
  - **Description**: Register a new user.
  - **Request Body**:
    ```json
    {
      "username": "newuser",
      "email": "newuser@example.com",
      "password": "password123",
      "role": ["admin"]
    }
    ```
  - **Response**:
    ```json
    {
      "message": "User registered successfully!"
    }
    ```

---

This project provides a robust foundation for user authentication and authorization in a Spring Boot application. Modify and extend the functionality as needed to meet your specific requirements.

