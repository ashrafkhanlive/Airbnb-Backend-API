🏨 Airbnb Backend Clone

A production-ready Airbnb Backend Clone built using **Spring Boot**, **Spring Security**, **JWT Authentication**, **PostgreSQL**, **JPA/Hibernate**, and **Stripe Payment Gateway**.
If you mean **"How can someone use or run this project after downloading it from GitHub?"**, add this section to your `README.md`.

---

# 🚀 Getting Started

Follow these steps to run the project on your local machine.

## 📋 Prerequisites

Make sure you have installed:

* ☕ Java 21 or later
* 📦 Maven 3.9+
* 🐘 PostgreSQL
* 💻 IntelliJ IDEA / VS Code / Eclipse
* 🐳 Docker (Optional)
* 🛠 Git

Verify installation:

```bash
java -version
mvn -version
git --version
```

---

# 📥 Clone the Repository

```bash
git clone https://github.com/your-username/airbnb-backend.git
```

Move into the project directory:

```bash
cd airbnb-backend
```

---

# ⚙️ Configure Database

Create a PostgreSQL database:

```sql
CREATE DATABASE airbnb_db;
```

Open:

```text
src/main/resources/application.properties
```

Update your database settings:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/airbnb_db
spring.datasource.username=postgres
spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

# 🔐 Configure JWT

Add your secret key:

```properties
jwt.secret=your-super-secret-key
jwt.expiration=86400000
```

---

# 💳 Configure Stripe

If you're using Stripe payments:

```properties
stripe.secret.key=sk_test_xxxxxxxxxxxxxxxxxxxxx
```

---

# 📦 Install Dependencies

```bash
mvn clean install
```

This downloads all required libraries automatically.

---

# ▶️ Run the Application

Using Maven:

```bash
mvn spring-boot:run
```

Or run the main class:

```text
AirBnbApplication.java
```

The server will start at:

```text
http://localhost:8080
```

---

# 📖 Open Swagger UI

Open your browser and visit:

```text
http://localhost:8080/api/v1/swagger-ui/index.html
```

From there you can test all available APIs interactively. The uploaded Swagger documentation shows modules for authentication, hotels, rooms, bookings, guests, inventory, and user profiles. 

---

# 🔑 Test the APIs

1. **Sign Up**

```http
POST /auth/signup
```

2. **Login**

```http
POST /auth/login
```

3. Copy the JWT token from the login response.

4. Click **Authorize** in Swagger.

5. Enter:

```text
Bearer YOUR_JWT_TOKEN
```

6. Now you can access protected endpoints.

---

# 🐳 Run with Docker (Optional)

Build the Docker image:

```bash
docker build -t airbnb-backend .
```

Run the container:

```bash
docker run -p 8080:8080 airbnb-backend
```

---

This project provides REST APIs for hotel management, room management, booking flow, inventory management, user authentication, and payment integration.

---

## 🚀 Features

### 🔐 Authentication
- User Registration
- User Login
- JWT Authentication
- Refresh Token Support
- Role-Based Authorization (Admin/User)

### 🏨 Hotel Management
- Create Hotel
- Update Hotel
- Delete Hotel
- Activate Hotel
- Hotel Details
- Hotel Reports

### 🛏 Room Management
- Add Room
- Update Room
- Delete Room
- Get Room Details
- Manage Room Inventory

### 🔎 Hotel Search
- Search Hotels
- View Hotel Information
- Filter Available Hotels

### 📅 Booking System
- Initialize Booking
- Booking Status
- Cancel Booking
- Add Guests
- View My Bookings

### 👥 Guest Management
- Add Guest
- Update Guest
- Delete Guest
- View Guests

### 💳 Payment
- Stripe Payment Integration
- Booking Payment API

### 📄 API Documentation
- Swagger UI
- OpenAPI 3

---

# 🛠 Tech Stack

- Java 21
- Spring Boot 4
- Spring Security
- Spring Data JPA
- Hibernate
- PostgreSQL
- JWT
- ModelMapper
- Lombok
- Stripe API
- Swagger OpenAPI
- Maven
- Docker
Absolutely. A good GitHub README should also explain the `src` folder because recruiters and developers want to understand the project architecture.

You can add the following section to your `README.md`.

---

# 📂 Project Structure

```
src
└── main
    ├── java
    │   └── com
    │       └── coderberojgar
    │           └── projects
    │               └── airBnbApp
    │                   ├── config
    │                   ├── controller
    │                   ├── dto
    │                   ├── entity
    │                   ├── exception
    │                   ├── repository
    │                   ├── security
    │                   ├── service
    │                   │    ├── impl
    │                   │    └── interfaces
    │                   ├── mapper
    │                   ├── util
    │                   └── AirBnbApplication.java
    │
    └── resources
        ├── application.properties
        ├── static
        └── templates
```

---

# 📖 Folder Explanation

## 📁 config/

Contains all application configuration classes.

**Examples**

* Security Configuration
* Swagger/OpenAPI Configuration
* ModelMapper Bean
* CORS Configuration
* Password Encoder
* JWT Configuration

**Purpose**

Keeps all project configurations centralized.

---

## 📁 controller/

Contains all REST API endpoints.

Examples

```
AuthController
HotelController
BookingController
RoomController
UserController
InventoryController
```

Responsibilities

* Receive HTTP Requests
* Validate Request Data
* Call Service Layer
* Return JSON Response

---

## 📁 dto/

DTO = Data Transfer Object

Used to transfer data between Client and Server.

Examples

```
LoginDTO
SignupDTO
BookingDTO
HotelDTO
RoomDTO
GuestDTO
UserDTO
InventoryDTO
HotelSearchRequest
```

Benefits

* Hide Entity Objects
* Prevent Sensitive Data Exposure
* Better API Design

---

## 📁 entity/

Contains Database Models.

Examples

```
UserEntity
HotelEntity
RoomEntity
BookingEntity
GuestEntity
InventoryEntity
```

Responsibilities

* Database Tables
* JPA Annotations
* Entity Relationships

Example

```java
@Entity
@Table(name="users")
public class UserEntity {
}
```

---

## 📁 repository/

Contains JPA Repository Interfaces.

Example

```java
UserRepository

HotelRepository

BookingRepository

RoomRepository
```

Responsibilities

* Database Operations
* CRUD
* Custom Queries

Example

```java
extends JpaRepository<UserEntity, Long>
```

---

## 📁 service/

Contains Business Logic.

Structure

```
service
│
├── interfaces
└── impl
```

Responsibilities

* Business Rules
* Validation
* Payment Processing
* Booking Logic
* Hotel Search Logic

Example

```
BookingService

BookingServiceImpl
```

---

## 📁 security/

Contains Spring Security implementation.

Examples

```
JWT Filter

JWT Utility

SecurityConfig

AuthenticationProvider

UserDetailsService
```

Responsibilities

* Login Authentication
* JWT Token Validation
* Authorization
* Role-Based Access

---

## 📁 mapper/

Responsible for Entity ↔ DTO conversion.

Uses

```
ModelMapper
```

Example

```
HotelEntity

↓

HotelDTO
```

Benefits

* Clean Code
* Less Boilerplate
* Easy Object Conversion

---

## 📁 exception/

Contains Global Exception Handling.

Examples

```
GlobalExceptionHandler

ResourceNotFoundException

BookingException

HotelException
```

Responsibilities

* Handle Errors
* Return Proper HTTP Status Codes
* Standardize Error Responses

---

## 📁 util/

Contains Utility Classes.

Examples

```
JWT Utility

Date Utility

File Utility

Common Constants

Helper Methods
```

---

## 📁 resources/

Contains application configuration and static resources.

Files

```
application.properties
application.yml

logback.xml

messages.properties
```

Responsibilities

* Database Configuration
* JWT Secret
* Stripe Keys
* Server Port
* Logging Configuration

---

## 📁 AirBnbApplication.java

This is the entry point of the Spring Boot application.

```java
@SpringBootApplication
public class AirBnbApplication {

    public static void main(String[] args) {
        SpringApplication.run(AirBnbApplication.class, args);
    }

}
```

---

# 🔄 Request Flow

```
Client
   │
   ▼
Controller
   │
   ▼
Service
   │
   ▼
Repository
   │
   ▼
PostgreSQL Database
   ▲
   │
Response (DTO)
```

---

# 🏗 Architecture

```
                REST API
                   │
                   ▼
            Controller Layer
                   │
                   ▼
             Service Layer
                   │
         Business Logic Layer
                   │
                   ▼
          Repository Layer
                   │
                   ▼
              PostgreSQL
```

---

# 🔐 Authentication Flow

```
User Login
      │
      ▼
Spring Security
      │
      ▼
JWT Token Generated
      │
      ▼
Client Stores Token
      │
      ▼
Every API Request
      │
      ▼
JWT Filter
      │
      ▼
Authenticated User
```

---

# 💳 Payment Gateway

Integrated with

- Stripe API

---

# 📈 Future Improvements

- Image Upload (AWS S3 / Cloudinary)
- Email Verification
- OTP Login
- Review & Ratings
- Wishlist
- Coupons
- Redis Cache
- Elasticsearch
- CI/CD Pipeline
- Kubernetes Deployment

---

# 👨‍💻 Author

**Ashraf Khan**

Backend Developer | Java | Spring Boot | PostgreSQL

# ⭐ Support

If you found this project helpful, please give it a ⭐ on GitHub.

Happy Coding! 
