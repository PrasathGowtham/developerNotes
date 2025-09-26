# Database Sharding

Sharding is a database architecture pattern where large datasets are **split (partitioned)** across multiple smaller databases (called **shards**).

- Each shard holds a portion of the data, and together they form the complete dataset.  
- It’s mainly used when a single database server cannot handle huge data volume or high query load.  

---

## Why Sharding?

- A single database has limits (storage, CPU, RAM, connections).  
- As data grows (millions of users, billions of rows), queries become slow.  
- Sharding distributes the data, so each shard handles a smaller portion → **better performance & scalability**.  

---

## How Sharding Works

- Instead of keeping all rows in one big table, rows are **distributed across different shards** based on a **shard key**.  
- **Shard Key** → A chosen column (e.g., UserID, CustomerID, Region) that decides which shard stores the row.  
- Each shard has the same schema (tables, columns), but different rows of data.  

👉 It’s like cutting a big cake into slices 🍰 — easier to handle and serve.  

---

## Types of Sharding

### 1. Range-Based Sharding
- Rows divided based on ranges of values.  
- Example:  
  - Shard 1 → UserID `1–1M`  
  - Shard 2 → UserID `1M–2M`  
  - Shard 3 → UserID `2M–3M`  

### 2. Hash-Based Sharding
- Use a **hash function** on the shard key to decide which shard stores the row.  
- Example: `UserID % 4`  

### 3. Geo/Directory-Based Sharding
- Shard based on **location or group**.  
- Example:  
  - Shard 1 → North America users  
  - Shard 2 → Europe users  
  - Shard 3 → Asia users  

---

## Example – E-commerce Application

Imagine we run an **Amazon-like app**.  

### Users Table (before sharding)
