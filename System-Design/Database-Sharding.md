# Database Sharding

Database sharding is a database architecture pattern in which large datasets are split (or partitioned) across multiple smaller databases, known as shards.  
Each shard contains a portion of the overall data, and collectively, they represent the complete dataset.  
This approach is primarily used when a single database server is unable to manage massive data volumes or high query loads.

## Why Sharding?

A single database server has limitations in terms of storage capacity, CPU power, RAM, and the number of connections it can handle.  
As the amount of data increases—such as millions of users or billions of rows—query performance begins to degrade.  
Sharding helps distribute the data so that each shard manages a smaller portion, resulting in improved performance and scalability.

## How Sharding Works

Instead of storing all rows in one large table, the rows are distributed across different shards based on a shard key.  
A shard key is a selected column (such as UserID, CustomerID, or Region) that determines which shard will store a particular row.  
Each shard maintains the same schema (i.e., tables and columns), but contains different rows of data.  
This concept is similar to slicing a large cake into smaller pieces 🍰—making it easier to manage and serve.

## Types of Sharding

### Range-Based Sharding

In range-based sharding, rows are divided based on specific ranges of values.  
**Example:**  
- Shard 1 stores UserIDs from 1 to 1 million  
- Shard 2 stores UserIDs from 1 million to 2 million  
- Shard 3 stores UserIDs from 2 million to 3 million  

### Hash-Based Sharding

Hash-based sharding uses a hash function on the shard key to determine which shard will store the row.  
**Example:**  
- Shard assignment based on `UserID % 4`

### Geo/Directory-Based Sharding

Geo-based sharding divides data based on geographic location or user group.  
**Example:**  
- Shard 1 stores data for users in North America  
- Shard 2 stores data for users in Europe  
- Shard 3 stores data for users in Asia  

## Example – E-commerce Application

Imagine we are running an Amazon-like e-commerce application.  
We have a `Users` table structured as follows:

### Users Table

| UserID | Name  | Country | Email              |
|--------|-------|---------|--------------------|
| 1      | Alex  | USA     | alex@example.com   |
| 2      | Priya | India   | priya@example.com  |
| 3      | John  | UK      | john@example.com   |
| ...    | ...   | ...     | ...                |
| 100M   | Chen  | China   | chen@example.com   |

With 100 million users, executing queries such as `SELECT * FROM Users WHERE UserID=67890123` becomes extremely slow because all rows are stored in a single location.

## How to Apply Sharding

To improve performance, we decide to shard the `Users` table based on country using geo-based sharding.  
- Shard 1 stores users from North America (USA, Canada, Mexico)  
- Shard 2 stores users from Europe (UK, Germany, France)  
- Shard 3 stores users from Asia (India, China, Japan)  

👉 When a user from India logs in, the application queries only Shard 3 instead of scanning the entire 100 million rows.

## Choosing the Shard Key

The shard key determines how data is distributed across shards.  
Common choices include:  
- `UserID` for hash-based sharding (e.g., `UserID % N`)  
- `Region` or `Country` for geo-based sharding  
- `CustomerID` for range-based sharding  

👉 **Example (Hash Sharding):**  
If we use `UserID % 4` as the shard key:  
- Users with IDs divisible by 4 go to Shard 1  
- IDs ending in 1 go to Shard 2  
- IDs ending in 2 go to Shard 3  
- IDs ending in 3 go to Shard 4  

So, a user with `UserID = 9` would be stored in Shard 2.

## 🔹 Advantages

- 🚀 **Performance:** Queries are faster because each shard contains less data.  
- 📈 **Scalability:** It is easy to add more shards as the data grows.  
- ⚡ **Parallelism:** Multiple shards can be queried simultaneously.

## 🔹 Disadvantages

- ❌ **Complexity:** The application must be aware of how to route queries to the correct shard.  
- ❌ **Joins Across Shards:** Performing joins across shards requires additional logic and can be difficult.  
- ❌ **Re-sharding:** Redistributing data when the shard key changes is expensive and complex.  
- ❌ **Consistency:** Ensuring data consistency across shards can be challenging.

## ✅ Summary

Database sharding involves dividing a large database into smaller, faster, and more manageable units called shards, typically based on a shard key.  
It is commonly used in large-scale applications such as social media platforms, e-commerce websites, and banking systems where a single database server cannot handle the workload efficiently.
