#  PetPooja-AI — AI-Powered Food Ordering System

A full-stack food ordering system powered by **Spring Boot**, **React**, **Gemini AI**, and **Razorpay**.
It includes secure authentication, smart recipe suggestions, admin/user separation, and full e-commerce functionality.

---

## 🧠 Architecture Diagram

![Architecture](assets/bestscalepetpoojaai.png)

---

## 🛠️ Backend (Spring Boot) Project Structure

The backend follows a clean layered architecture using Java Spring Boot. It exposes REST APIs secured with JWT and integrates with Cloudinary, Razorpay, and Gemini AI.

### 📁 Package: `in.vishal.foodiesapi`

in.vishal.foodiesapi/
├── config/
├── controller/
├── entity/
├── filters/
├── io/
├── repository/
├── service/
├── util/
├── FoodiesapiApplication.java




---

### 🔹 `config/`

Handles application-wide configuration.

- **`CloudinaryConfig`**: Initializes Cloudinary for uploading food images.
- **`SecurityConfig`**: Configures JWT-based security, role-based access, and filters.

---

### 🔹 `controller/`

Houses all REST API endpoints.

- **`AuthController`**: Signup/login with JWT token.
- **`UserController`**: User profile-related APIs.
- **`FoodController`**: CRUD operations on food items.
- **`OrderController`**: Place and fetch orders.
- **`CartController`**: Add/remove items from cart.
- **`ContactController`**: Contact form submission handling.
- **`RecipeController`**: Placeholder for static recipe calls.
- **`GeminiController`**: Calls Gemini API to generate recipes.

---

### 🔹 `entity/`

JPA entity classes mapped to MongoDB collections.

- **`UserEntity`**: Stores user details (roles, credentials).
- **`FoodEntity`**: Stores food item metadata and image info.
- **`CartEntity`**: Cart structure with multiple items.
- **`OrderEntity`**: Complete order record with address, items, user info.

---

### 🔹 `filters/`

- **`JwtAuthenticationFilter`**: Intercepts requests and validates JWT tokens.

---

### 🔹 `io/`

Contains **Request/Response DTOs** used between frontend and backend.

- **Authentication**: `AuthenticationRequest`, `AuthenticationResponse`
- **Cart**: `CartRequest`, `CartResponse`
- **Food**: `FoodRequest`, `FoodResponse`
- **Order**: `OrderRequest`, `OrderResponse`, `OrderItem`
- **User**: `UserRequest`, `UserResponse`
- **Contact**: `ContactRequest`

---

### 🔹 `repository/`

Spring Data interfaces to interact with MongoDB.

- `UserRepository`, `FoodRepository`, `OrderRepository`, `CartRepository`

---

### 🔹 `service/`

Contains business logic interfaces and implementations.

- **Authentication & Security**:
  - `AppUserDetailsService`, `AuthenticationFacade`, `AuthenticationFacadeImpl`
- **Cart Management**:
  - `CartService`, `CartServiceImpl`
- **Food Management**:
  - `FoodService`, `FoodServiceImplementation`
- **Order Management**:
  - `OrderService`, `OrderServiceImpl`
- **User Services**:
  - `UserService`, `UserServiceImplementation`
- **AI Integration**:
  - `GeminiService`: Calls Gemini API
- **Communication**:
  - `MailService`: Sends mail from contact form

---

### 🔹 `util/`

Helper classes for utilities.

- `JwtUtil`: JWT token creation and validation
- `CloudinaryImage`: Utility for Cloudinary upload/delete

---

### 🔹 `FoodiesapiApplication.java`

Main entry point to the Spring Boot application.

---

### 🔹 `resources/`

- `application.properties`: Configs (Cloudinary keys, Mongo URI, Razorpay, etc.)


