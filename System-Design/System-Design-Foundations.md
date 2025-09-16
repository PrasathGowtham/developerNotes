
# 📘 Foundations

---

## 1️⃣ What is System Design?

System Design is the process of planning how different components of a software system will work together to meet requirements.  

It’s like creating a blueprint before building a house.  

**Example: If you’re building Instagram:**
- What services do you need? (User, Post, Notification, Search)  
- How do they communicate? (APIs, databases)  
- How do you handle millions of users at once? (scaling, caching, load balancing)  

👉 **System Design ensures your app is scalable, reliable, and efficient.**

---

## 2️⃣ HLD vs LLD

| **Aspect** | **High-Level Design (HLD)** | **Low-Level Design (LLD)** |
|------------|------------------------------|-----------------------------|
| **Focus** | Overall architecture & system structure | Detailed internal logic & implementation |
| **Granularity** | Big picture (modules, data flow, tech stack) | Small picture (classes, methods, DB schema) |
| **Audience** | Architects, Senior Engineers, Stakeholders | Developers implementing the system |
| **Output** | Architecture diagrams, data flow diagrams, module breakdown | Class diagrams, sequence diagrams, SQL schema |
| **Example (Food Delivery App)** | Modules: User Service, Restaurant Service, Order Service, Payment Service | Database tables (`orders`, `users`), APIs (`POST /order`), class methods (`createOrder()`) |

---

## 3️⃣ Client–Server Architecture

👉 This is the most common software model.

**Client (Frontend):**
- Runs on browser/mobile.  
- Sends requests (login, fetch posts, etc.).  

**Server (Backend):**
- Runs on a machine (cloud/server).  
- Processes requests, applies business logic.  

**Database:**
- Stores data (users, orders, messages).  

📌 **Flow Example (Login System):**
1. User enters username & password (client).  
2. Request goes to server (`POST /login`).  
3. Server checks credentials in database.  
4. If valid → Server responds with "Login success" + session token.  
5. Client stores token → user is logged in.  

---

## 4️⃣ Basics of Networking

### 🔹 HTTP (HyperText Transfer Protocol)
- Protocol for communication between client and server.  
- Uses requests and responses.  
- **Example:** `GET /users/123` → returns user info.  

---

### 🌐 REST APIs (Representational State Transfer)

#### 1️⃣ What is a REST API?
- REST is an **architectural style** used to design web services.  
- A REST API allows two systems (client & server) to communicate over the web using HTTP.  
- Data is usually sent in **JSON format**.  

#### Methods:
- `GET` → Read data  
- `POST` → Create new data  
- `PUT` → Replace existing data  
- `PATCH` → Update partially  
- `DELETE` → Remove data  

---

### 🔹 DNS (Domain Name System)
- Converts human-friendly names → IP addresses.  

**Example:**  
`www.google.com` → `142.250.182.14`  

---

### 🔹 Load Balancer
- A service that distributes traffic across multiple servers.  

**Why?**
- Prevents one server from crashing due to heavy load.  
- Ensures high availability.  

📌 **Example:**
- Without LB → All users hit one server → overload.  
- With LB → Requests spread across **Server A, B, C**.  
