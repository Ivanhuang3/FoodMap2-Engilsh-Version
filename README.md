# FoodMAP2 Project Architecture 🍽️

## Project Overview 📖
FoodMAP2 is a Spring Boot-based food map application that provides restaurant search, review, and user management features, aiming to create a personalized culinary exploration experience for users.

### Technology Stack ⚙️
- **Backend Framework**: Spring Boot 3.2.3
- **Database**: H2 (Development Environment)
- **Security Framework**: Spring Security + JWT
- **Template Engine**: Thymeleaf
- **Cache**: Caffeine
- **Build Tool**: Maven
- **Java Version**: 17

## Project Structure 📂

```plaintext
src/main/java/com/foodmap2/
├── auth/                           # 🔐 Authentication Module
│   ├── controller/                 # Authentication Controller
│   ├── service/                    # Authentication Service
│   ├── dto/                        # Authentication-related DTOs
│   └── config/                     # Authentication Configuration
├── user/                           # 👤 User Module
│   ├── controller/                 # User Controller
│   ├── service/                    # User Service
│   ├── dto/                        # User-related DTOs
│   ├── entity/                     # User Entity
│   └── repository/                 # User Repository
├── restaurant/                     # 🍴 Restaurant Module
│   ├── controller/                 # Restaurant Controller
│   ├── service/                    # Restaurant Service
│   ├── dto/                        # Restaurant-related DTOs
│   ├── entity/                     # Restaurant Entity
│   └── repository/                 # Restaurant Repository
├── review/                         # ⭐ Review Module
│   ├── controller/                 # Review Controller
│   ├── service/                    # Review Service
│   ├── dto/                        # Review-related DTOs
│   ├── entity/                     # Review Entity
│   └── repository/                 # Review Repository
├── common/                         # 🛠️ Common Components
│   ├── config/                     # Common Configuration
│   ├── exception/                  # Exception Handling
│   ├── util/                       # Utility Classes
│   └── constant/                   # Constant Definitions
├── security/                       # 🛡️ Security Module
│   ├── config/                     # Security Configuration
│   ├── filter/                     # Security Filters
│   └── util/                       # Security Utility Classes
├── cache/                          # ⚡ Cache Module
│   ├── config/                     # Cache Configuration
│   └── service/                    # Cache Service
├── async/                          # 🔄 Asynchronous Processing Module
│   ├── config/                     # Asynchronous Configuration
│   └── service/                    # Asynchronous Service
├── monitoring/                     # 📊 Monitoring Module
│   ├── config/                     # Monitoring Configuration
│   └── service/                    # Monitoring Service
└── integration/                    # 🔗 External Integration Module
    ├── google/                     # 🌍 Google API Integration
    ├── oauth2/                     # 🔑 OAuth2 Integration
    └── email/                      # ✉️ Email Service Integration
```

## Frontend Resources 🖼️

```plaintext
src/main/resources/
├── templates/                      # 📄 Thymeleaf Templates
│   ├── layout/                     # Layout Templates
│   ├── index.html                  # Homepage
│   ├── login.html                  # Login Page
│   └── register.html               # Registration Page
├── static/                         # 📁 Static Resources
│   ├── css/                        # Style Files
│   ├── js/                         # JavaScript Files
│   └── images/                     # Image Resources
├── application.properties          # ⚙️ Application Configuration
└── logback-spring.xml             # 📜 Log Configuration
```

## Module Descriptions 📚

### 🔐 Authentication Module (auth)
- **Function**: User login, registration, JWT token management
- **Main Components**: 
  - `AuthController`: Handles login/registration requests
  - `AuthService`: Authentication business logic
  - `LoginRequest`/`LoginResponse`/`RegisterRequest`: Authentication-related DTOs

### 👤 User Module (user)
- **Function**: User data management, profile maintenance, restaurant favorites
- **Main Components**:
  - `UserController`: User data CRUD operations
  - `UserService`: User business logic
  - `User`: User entity class
  - `UserRepository`: User data access

### 🍴 Restaurant Module (restaurant)
- **Function**: Restaurant information management, search, map integration
- **Main Components**:
  - `RestaurantController`: Restaurant CRUD operations
  - `RestaurantService`: Restaurant business logic
  - `Restaurant`: Restaurant entity class
  - `RestaurantRepository`: Restaurant data access

### ⭐ Review Module (review)
- **Function**: Restaurant reviews, rating system
- **Main Components**:
  - `ReviewController`: Review CRUD operations
  - `ReviewService`: Review business logic
  - `Review`: Review entity class
  - `ReviewRepository`: Review data access

### 🛠️ Common Components (common)
- **Function**: Provides shared tools and configurations for all modules
- **Main Components**:
  - `ApiResponse`: Unified API response format
  - `BusinessException`: Business exception handling
  - `WebConfig`: Web-related configuration
  - Various utility classes and constants

### 🛡️ Security Module (security)
- **Function**: Application security control
- **Main Components**:
  - `SecurityConfig`: Spring Security configuration
  - `JwtUtil`: JWT token utility class
  - Security filters and authentication mechanisms

### ⚡ Cache Module (cache)
- **Function**: Enhances application performance
- **Main Components**:
  - `CacheConfig`: Cache configuration
  - `CacheService`: Cache service

### 🔄 Asynchronous Processing Module (async)
- **Function**: Handles time-consuming operations
- **Main Components**:
  - `AsyncConfig`: Asynchronous configuration
  - `AsyncService`: Asynchronous service

### 📊 Monitoring Module (monitoring)
- **Function**: Application monitoring and logging
- **Main Components**:
  - `MonitoringConfig`: Monitoring configuration
  - `MonitoringService`: Monitoring service

### 🔗 External Integration Module (integration)
- **Function**: Integration with external services
- **Main Components**:
  - `GoogleIntegration`: Google Maps API integration
  - `OAuth2Integration`: OAuth2 authentication integration
  - `EmailService`: Email sending service

## Quick Start 🚀

### Environment Requirements
- Java 17+
- Maven 3.6+

### Startup Steps
1. Clone the project
   ```bash
   git clone [repository-url]
   cd FoodMAP2
   ```
2. Compile the project
   ```bash
   mvn clean compile
   ```
3. Start the application
   ```bash
   mvn spring-boot:run
   ```
4. Access the application
   - Homepage: http://localhost:8080
   - H2 Database Console: http://localhost:8080/h2-console

## API Documentation 📜

### Authentication API
- `POST /api/auth/login` - User login
- `POST /api/auth/register` - User registration
- `GET /api/auth/check-email` - Check if email exists

### Restaurant API
- `GET /api/restaurants` - Retrieve all restaurants
- `GET /api/restaurants/{id}` - Retrieve a specific restaurant
- `GET /api/restaurants/search` - Search restaurants

### User API
- `GET /api/users/{id}` - Retrieve user data
- `PUT /api/users/{id}` - Update user data

## Development Guidelines 🛠️

### Adding New Features
1. Create controller, service, entity, etc., classes under the corresponding module
2. Follow existing naming conventions and architectural patterns
3. Add appropriate unit tests
4. Update API documentation

### Code Standards
- Use Lombok to reduce boilerplate code
- Follow RESTful API design principles
- Use a unified exception handling mechanism
- Add appropriate log records

## Deployment ☁️

### Docker Deployment
```bash
# Build Docker image
docker build -t foodmap2 .

# Run container
docker run -p 8080:8080 foodmap2
```

### Kubernetes Deployment
```bash
kubectl apply -f deploy/kubernetes/
```

## Contribution Guidelines 🤝

1. Fork the project
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Contact Information 📧

- Project Maintainer: [Ivan Huang]
- Email: [saucyking3@gmail.com]
- Project Link: [https://github.com/Ivanhuang3/foodmap2]
  
