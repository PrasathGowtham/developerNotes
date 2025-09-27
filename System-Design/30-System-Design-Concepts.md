# 1. CLIENT-SERVER ARCHITECTURE

- Client could be a web browser, mobile app or any other frontend application.  
- Server is a machine that runs continuously and waits to handle incoming requests.  
- A client will send a request to store, retrieve or modify data to the server.  
- A server receives a request, processes it, performs necessary actions, and then sends back a response to the client.  

---

# 2. IP ADDRESS

- How does the client even know where to find the server?  
- It needs an address to locate and communicate with it.  
- Computers identify each other using **IP Addresses** on the internet.  

---

# 3. DOMAIN NAME SYSTEM (DNS)

- When we visit any website, instead of typing an IP Address we just enter names — why?  
- Because IP Addresses are hard to remember; instead, we use Domain Names which are much more human-friendly.  
- To map an IP Address with Domain Names we use a service called **Domain Name System (DNS)**.  

---

# 4. PROXY / REVERSE PROXY

- When we send a request from client to server, it is not always sent directly — it may go through a proxy or reverse proxy.  
- A **Proxy Server** is a middleman between client and the internet.  
- Proxy Server receives requests from client, forwards them to the target server, then receives the response and sends it back to the client.  
- Proxy Server hides IP Address, location, and identity, keeping users private.  
- A **Reverse Proxy** is a middleman between internet and server.  
- Reverse Proxy intercepts client requests and forwards them to servers based on predefined rules.  

---

# 5. LATENCY

- Whenever client communicates with server there are always delays — one of the biggest causes is **physical distance**.  
- If the server is in New York and client is in India, the request travels half the world, and the response must travel back.  
- This round-trip delay is called **Latency**.  
- High latency makes applications feel slow and unresponsive.  
- One way to reduce latency is keeping servers all over the world.  

---

# 6. HTTP / HTTPS

- Once the connection is made, how do client and server actually work?  
- They communicate using a set of rules called **HTTP/HTTPS**.  
- Client sends a request to server — request contains headers (type, browser, cookies) and a body with additional data.  
- Server processes the request and sends back a response.  
- **HTTP** sends data in plain text.  
- **HTTPS** sends data with encryption using SSL/TLS to ensure privacy and integrity.  

---

# 7. APIs

- Client and server don’t just send raw HTTP requests/responses; HTTP is only the transport protocol.  
- HTTP doesn’t define:  
  - How requests should be structured.  
  - What format responses should be in.  
  - How different clients should interact with a server.  
- This is where **APIs** come in.  
- API is a middleman that allows structured communication between client and server.  
- Client sends a request to API → API processes it → interacts with database → prepares and sends response back.  
- Different API styles exist to serve different needs.  

---

# 8. REST API

- **REST** defines how client and server communicate over HTTP in a structured way.  
- REST is **stateless** → every request is independent.  
- REST uses standard HTTP methods:  
  - GET  
  - POST  
  - PUT  
  - DELETE  
- REST APIs are simple and scalable but have limitations with complex data retrieval.  
- REST endpoints often return more data than needed → inefficient network usage.  

---

# 9. GraphQL

- Introduced by Facebook in 2015 to address REST limitations.  
- GraphQL lets clients ask for exactly what they need — nothing more, nothing less.  
- In REST, to get profile + recent posts → need multiple API calls.  
- In GraphQL, both can be retrieved in a **single request**.  

---

# 10. DATABASES

- Where is the actual data stored?  
- Small apps could store data in variables or files, but modern apps handle massive data.  
- For that we need dedicated **Databases**.  
- Database is the **backbone** of any modern application.  
- Ensures data is stored, retrieved, and managed efficiently while being secure, consistent, and durable.  
- Client → Server → Database → fetch data → return to client.  

---

# 11. SQL vs NoSQL

- Not all databases are the same.  
- **SQL Databases**:  
  - Data stored in tables with predefined schema.  
  - Strong consistency.  
  - Follow ACID properties.  
  - Structured relationships.  
- **NoSQL Databases**:  
  - Designed for scalability and performance.  
  - Flexible schema, no fixed structure.  
  - Different models:  
    - Key-Value  
    - Document  
    - Graph  
    - Wide-Column  
- Use SQL for structured + strong consistency.  
- Use NoSQL for scalability + flexibility.  
- Many modern applications use **both**.  

---

# 12. VERTICAL SCALING

- As users grow, requests increase → server slows down.  
- Quick solution: upgrade server by adding CPU, RAM, Storage = **Vertical Scaling**.  
- Limitations:  
  - Can’t upgrade forever, machines have limits.  
  - Powerful servers become exponentially expensive.  
  - Single point of failure → if it crashes, system goes down.  
- Vertical scaling = quick fix, not long-term.  

---

# 13. HORIZONTAL SCALING

- Instead of upgrading one server, add **multiple servers** to share load = **Horizontal Scaling**.  
- More servers → more capacity → better traffic handling.  
- If one server fails, others continue = improved reliability.  
- Challenge: how does client know which server to connect?  
- Solution: **Load Balancer**.  

---

# 14. LOAD BALANCERS

- Load Balancer sits between client and servers as a **traffic manager**.  
- Distributes requests across multiple servers.  
- If one server crashes, it redirects to another healthy server.  
- Uses algorithms like:  
  - Round-Robin  
  - Least Connections  
  - IP Hashing  

---

# 15. DATABASE INDEXING

- As data grows, queries get slower.  
- Indexing speeds up database queries.  
- Works like a book index → jump directly to required section.  
- Database index stores column values with pointers to actual rows.  
- Common on primary keys, foreign keys, frequently used `WHERE` columns.  
- Trade-off: indexes speed up reads but slow down writes.  

---

# 16. REPLICATION

- Even indexing is not enough with massive reads.  
- Solution: **Replication**.  
- Primary database handles writes.  
- Replicas handle reads.  
- Improves performance and availability.  
- If primary fails, replica can take over.  

---

# 17. SHARDING

- Needed when data is too large for one server.  
- Split database into smaller parts = **Shards**.  
- Each shard contains a subset of total data.  
- Example: shard by UserID.  
- Queries distributed across shards = improved read/write performance.  
- Sharding = **Horizontal Partitioning**.  

---

# 18. VERTICAL PARTITIONING

- Problem not rows, but too many **columns**.  
- Split database by columns = **Vertical Partitioning**.  
- Example: `User` table split into details, login history, billing info.  
- Improves query performance by reducing scanned columns.  
- Reduces unnecessary disk I/O.  

---

# 19. CACHING

- Disk retrieval is always slower than memory.  
- Store frequently accessed data in memory = **Caching**.  
- Improves system performance.  
- Common pattern: **Cache-Aside**.  
  - Client requests data → Server checks cache.  
  - If found → return from cache.  
  - If not → fetch from DB, store in cache, return.  
- Use **TTL (Time-to-Live)** to avoid outdated cache.  

---

# 20. DENORMALIZATION

- Normalization splits data into multiple tables to reduce redundancy → but requires **joins**.  
- Joins become slower as data grows.  
- Solution: **Denormalization** = combine related data into fewer tables.  
- Used in read-heavy applications for speed.  
- Trade-off: more storage, complex updates.  

---
