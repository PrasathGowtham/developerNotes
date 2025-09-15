# What is System Design?

System Design is the process of defining the:  
- **Architecture**  
- **Components**  
- **Modules**  
- **Interfaces**  
- **Data flow**  

of a system to meet specific requirements.

It’s about **planning how a software system will work before we build it**.  
It’s like creating a **blueprint for a house before construction**.

- **How many rooms required**  
  *(What all are the services/modules required)*  

- **Where doors/windows should come**  
  *(How many APIs required and how they connect)*  

- **How Water & electricity flow should be**  
  *(Data flow between multiple services)*  

- **What Materials to use**  
  *(What databases, frameworks are required)*  

---

# Where is System Design Used?

System design is used whenever you’re **building or scaling a complex software system**.

### Social Media App (Instagram, Twitter)
- Handle millions of users.  
- Store photos, videos, comments.  
- Show personalized feeds.  
- Ensure fast performance.  

### E-commerce (Amazon, Flipkart)
- Manage products, orders, payments, delivery tracking.  
- Handle peak traffic (sales/festivals).  
- Prevent downtime.  

### Banking/Payment System (UPI, Paytm)
- Secure transactions.  
- Real-time updates to accounts.  
- Fraud detection.  

---

# When Do We Use System Design?

✅ **Before starting large-scale projects**  
If you’re building a large product (like **Zomato, Ola, Netflix**), you must do system design.  

✅ **When scaling existing systems**  
- If your app starts with **100 users → fine**.  
- But when it grows to **1M users → you need redesign** (load balancers, caching, microservices).  

---

# High-Level Design (HLD)

## 📌 Definition
HLD is the **blueprint/architecture view** of the entire system.  
It focuses on the **big picture** — how different modules interact, what technologies are used, and how data flows.  

👉 Think of HLD as the **map of a city**:
- You see roads, neighborhoods, bridges, airports.  
- You don’t see each house’s layout — only the overall structure.  

## 🔑 Key Points in HLD
- Architecture style: Monolithic vs Microservices vs Event-driven.  
- Components/Modules: What are the main services? (e.g., Auth service, Payment service).  
- Data flow: How modules talk (APIs, queues, events).  
- Database choice: SQL or NoSQL? One DB or multiple?  
- Scalability considerations: Load balancer, cache, CDN, sharding.  
- Tech stack: Frameworks, servers, cloud infra.  

---

# Low-Level Design (LLD)

## 📌 Definition
LLD is the **detailed implementation plan** for individual components/modules.  
It focuses on **class diagrams, methods, database schemas, APIs, validations, error handling**.  

👉 Think of LLD as the **blueprint of a single house in the city**:
- You know where each room, door, and window is placed.  
- Detailed wiring, plumbing, furniture layout.  

## 🔑 Key Points in LLD
- Class diagrams (UML) with relationships.  
- API design: Request/response structures.  
- Database schema: Tables, primary keys, foreign keys.  
- Algorithms: Sorting, searching, caching, load handling.  
- Error handling & validations.  
- Security rules.  
