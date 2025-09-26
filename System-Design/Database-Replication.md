# What is a Database Replica?

A **database replica** is a copy of a database that mirrors the data of the primary (original) database.  

The replica keeps itself updated by receiving changes from the primary database, either **synchronously (immediately)** or **asynchronously (with some delay)**.  

Think of it like a **backup that can also serve requests**.

---

## Why Use Database Replication?

### High availability
If the primary database goes down, replicas can serve data so the system doesn’t fail.

### Load balancing
- Primary handles writes (`INSERT`, `UPDATE`, `DELETE`).  
- Replicas handle reads (`SELECT`).  
- This improves performance when there are millions of users.

### Disaster recovery
If something corrupts the primary, you have a replica with recent data.

### Geographical distribution
Place replicas in different regions for faster access for users worldwide.

---

## Types of Replication

| Type                        | Description                                        | Pros                        | Cons                          |
|-----------------------------|----------------------------------------------------|-----------------------------|-------------------------------|
| **Master-Slave (Primary-Replica)** | Primary handles writes; replicas handle reads      | Simple, scalable for reads  | Writes still depend on primary |
| **Master-Master (Multi-Primary)** | Multiple databases handle writes & reads, synchronize among themselves | High availability for writes too | Complex conflict resolution   |
| **Synchronous**             | Changes are immediately applied to replicas        | Strong consistency          | Slower writes                 |
| **Asynchronous**            | Changes are applied with some delay                | Fast writes                 | Replicas may lag slightly     |

---

## Real-World Examples

### Facebook / Instagram
- Users worldwide reading feeds → replicas in multiple regions.  
- Writes (posts, likes) go to primary, reads (feeds) served from replicas.  

### E-commerce Site
- Checkout transactions → primary database.  
- Product catalog browsing → replicas to reduce load.  

### Banking Systems
- Transactions → primary database.  
- Account balance queries → replicas in branches worldwide.  

---

## Key Considerations

### Lag time
Asynchronous replicas may not reflect the very latest changes immediately, but they catch up after a short delay.

### Consistency vs Availability
Synchronous ensures strong consistency, asynchronous favors availability.

### Conflict resolution
Especially in master-master setups, you need to handle conflicts when the same data changes in two databases.
