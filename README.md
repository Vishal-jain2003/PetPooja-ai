<p align="center">
  <img src="assets/logo.png" alt="PetPooja-AI Logo" width="120"  style="border-radius: 50%; border: 2px solid #ddd;"/>
</p>


<h1 align="center"> PetPooja AI-Powered Food Ordering Platform</h1>

<p align="center">
  <b>Live Demo:</b> <a href="https://petpooja-ai.vercel.app" target="_blank">https://petpooja-ai.vercel.app</a><br/>
  <i>Frontend: React.js • Backend: Spring Boot • DB: MongoDB • AI: Gemini API • Payments: Razorpay</i>
</p>

---

> ⚠️ **Note**: The backend is hosted on [Render] so the first request may take **20–30 seconds** to spin up (cold start).
> Please wait a few moments for food data or Chef AI to load properly.

---




A full-stack food ordering system powered by **Spring Boot**, **React**, **Gemini AI**, and **Razorpay**.
It includes secure authentication, smart recipe suggestions, admin/user separation, and full e-commerce functionality.

---

## 🧠 Architecture Diagram

![Architecture](assets/bestscalepetpoojaai.png)

---

---

## 📸 Full Website Screenshots

Here’s a complete walkthrough of the PetPooja-AI website for both users and admin.

---

### 👨‍🍳 User Flow

#### 🔐 Login Page
<img src="assets/login.png" alt="Login Page" width="700"/>

#### 🏠 Home Page
<img src="assets/homepage.png" alt="Home Page" width="700"/>

#### 🍽️ Display Food
<img src="assets/displayfood.png" alt="Display Food Page" width="700"/>

#### 🔍 Explore by Search
<img src="assets/explore.png" alt="Explore Search Page" width="700"/>

#### 🤖 Chef AI Suggestions
<img src="assets/chefai.png" alt="Chef AI Suggestions" width="700"/>

#### 🛒 Cart Page
<img src="assets/cart.png" alt="Cart Page" width="700"/>

#### 🚚 Order Placement Page
<img src="assets/orderpage.png" alt="Order Page" width="700"/>

#### 💳 Razorpay Payment Flow
<img src="assets/rz1.png" alt="Razorpay 1" width="700"/>
<img src="assets/rz2.png" alt="Razorpay 2" width="700"/>
<img src="assets/rz3.png" alt="Razorpay 3" width="700"/>
<img src="assets/rz4.png" alt="Razorpay 4" width="700"/>

#### 📦 My Orders
<img src="assets/myorders.png" alt="My Orders Page" width="700"/>

---

### 🧑‍💼 Admin Flow

#### 🍕 Add Food
<img src="assets/admin_addfood.png" alt="Admin Add Food" width="700"/>

#### 📋 List Food
<img src="assets/admin_listfood.png" alt="Admin List Food" width="700"/>

#### 📦 Orders Management
<img src="assets/admin_orders.png" alt="Admin Orders Page" width="700"/>



## 🛠️ Backend (Spring Boot) Project Structure

The backend follows a clean layered architecture using Java Spring Boot. It exposes REST APIs secured with JWT and integrates with Cloudinary, Razorpay, and Gemini AI.

### 📁 Package: `in.vishal.foodiesapi`

```
in.vishal.foodiesapi/
├── config/             # Spring Security, Cloudinary setup
├── controller/         # All REST APIs (Auth, User, Food, Orders, ChefAI, etc.)
├── entity/             # MongoDB @Document models (UserEntity, FoodEntity, etc.)
├── filters/            # JWT authentication filter
├── io/                 # Request & Response DTOs
├── repository/         # Spring Data MongoDB Repositories
├── service/            # Interfaces & Implementations (Business Logic)
├── util/               # Utility classes like JWT and Cloudinary helpers
└── FoodiesapiApplication.java  # Main Spring Boot application entry point
```




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


---

## 🌐 Frontend (React) Project Structure

The frontend is built using **React.js** and structured into two separate panels:

- 🧑‍🍳 **Admin Panel** – for managing food items and orders.
- 👨‍👩‍👧‍👦 **User Panel** – for placing orders, exploring food, and interacting with Chef AI.

---

### 🧑‍🍳 Admin Panel (`/admin`)

```
frontend/src/
├── components/
│ ├── Menubar/ # Top navigation for admin
│ └── Sidebar/ # Side navigation links
├── pages/
│ ├── AddFood/ # Form to add new food item
│ ├── ListFood/ # List and manage food items
│ └── Orders/ # View all customer orders
├── services/
│ └── foodService.js # API calls for admin (CRUD food)
├── App.jsx, App.css
```



> ⚙️ Functionality: Admin can add, update, and delete food items with images (via Cloudinary), and manage orders in real-time.

---

### 👤 User Panel (Main Website)


```
frontend/src/
├── components/
│ ├── Header/ # Site header with navigation
│ ├── Login/, Register/ # Auth components
│ ├── ExploreMenu/ # Lists categories and items
│ ├── FoodItem/ # Food card component
│ └── FoodDisplay/ # Display food details
├── context/
│ └── StoreContext.jsx # Global context for user & cart
├── pages/
│ ├── Home/ # Landing page
│ ├── Explore/ # Browse food items
│ ├── FoodDetails/ # Individual food page
│ ├── Cart/ # Cart with items
│ ├── PlaceOrder/ # Address form + Razorpay
│ ├── MyOrders/ # View previous orders
│ ├── ChefAI/ # AI-generated recipe suggestions
│ └── Contact/ # Contact form
├── services/
│ ├── authService.js # Login/register APIs
│ ├── cartService.js # Cart-related APIs
│ └── foodService.js # Fetch food and order data
├── util/
│ └── cartUtils.js # Cart helper functions
├── App.jsx, App.css
```



> 💡 Functionality: Users can explore food, get smart recipe suggestions using **Gemini AI**, add items to the cart, pay via **Razorpay**, and view order history.

---

## 🧩 State Management

- Uses `StoreContext.jsx` (React Context API) to manage:
  - 🧑 Logged-in user state
  - 🛒 Cart items
  - 💬 Notifications and UI state

---



## 🔐 Routing

- React Router used for:
  - Public Pages (`/`, `/explore`, `/login`)
  - Protected Pages (`/cart`, `/placeorder`, `/orders`)
  - Admin Pages (`/admin/add-food`, `/admin/orders`)

---
---

## 🔄 API Flow – From Frontend to Backend to External Services

This section explains how data flows across the system when a user interacts with the app:

---

### 1️⃣ **User Registration & Login**
- 🔸 **Frontend**: `authService.js` → API call with user credentials
- 🔸 **Backend**: `AuthController` validates via Spring Security
- 🔸 🔐 JWT Token is generated using `JwtUtil` and sent back
- ✅ Token is stored in localStorage and used for secured routes

---

### 2️⃣ **Explore & View Food Items**
- 🔸 **Frontend**: `foodService.js` fetches food list
- 🔸 **Backend**: `FoodController.getAllFoods()` → fetches from `FoodRepository`
- 🔸 **Database**: MongoDB returns all food items

---

### 3️⃣ **Add to Cart & Manage Cart**
- 🔸 **Frontend**: `cartService.js` sends add/remove item requests
- 🔸 **Backend**: `CartController` → `CartServiceImpl` → `CartRepository`
- 🔄 Cart state is synced per user and returned to update UI

---

### 4️⃣ **Place Order with Address & Payment**
- 🔸 **Frontend**: On checkout, order address is submitted
- 🔸 **Backend**: 
  - `OrderController` creates order
  - `Razorpay API` is triggered
- 🔸 **External**: Razorpay returns payment ID
- 🔸 **Backend**: Confirms payment and stores order in MongoDB

---

### 5️⃣ **View My Orders**
- 🔸 **Frontend**: Calls `orderService.js`
- 🔸 **Backend**: `OrderController.getOrdersByUser()` returns orders
- 🧾 Orders shown in MyOrders page

---

### 6️⃣ **AI Recipe Suggestions (Chef AI)**
- 🔸 **Frontend**: User gives preference → sent via `ChefAI.jsx`
- 🔸 **Backend**: `GeminiController` → `GeminiService` calls Gemini API
- 🔸 **External**: Gemini returns recipe suggestion
- 🔸 **Frontend**: UI displays generated recipe with ingredients & instructions

---

### 7️⃣ **Image Upload for Food (Admin Panel)**
- 🔸 **Frontend**: Admin uploads image via `AddFood.jsx`
- 🔸 **Backend**: `FoodController.addFood()` calls `CloudinaryImage.uploadImage()`
- 🔸 **External**: Cloudinary stores image and returns `secure_url` + `public_id`
- 🔸 **Backend**: URL is saved with food data in MongoDB

---

### 8️⃣ **Contact Form (Email Support)**
- 🔸 **Frontend**: User fills form on `Contact.jsx`
- 🔸 **Backend**: `ContactController` → `MailService` sends email to admin

---

## 🧠 Summary

| Interaction          | Frontend Component     | Backend Controller    | External API        |
|----------------------|------------------------|------------------------|----------------------|
| Login/Register       | `authService.js`       | `AuthController`       | —                    |
| View Foods           | `foodService.js`       | `FoodController`       | MongoDB              |
| Cart Operations      | `cartService.js`       | `CartController`       | MongoDB              |
| Place Order + Pay    | `PlaceOrder.jsx`       | `OrderController`      | Razorpay             |
| My Orders            | `MyOrders.jsx`         | `OrderController`      | MongoDB              |
| Chef AI Suggestions  | `ChefAI.jsx`           | `GeminiController`     | Gemini API           |
| Image Upload         | `AddFood.jsx`          | `FoodController`       | Cloudinary           |
| Contact Support      | `Contact.jsx`          | `ContactController`    | SMTP (via MailService) |

---








