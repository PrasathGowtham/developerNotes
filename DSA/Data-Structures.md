
# What is Data Structures?

A **data structure** is a way of organizing data so that it can be used.  
We can manipulate the data like **search, insert, delete, update** efficiently.

---

# Types of Data Structures

## 1. Primitive Data Structure
These can hold only a single value.  

- **Integer, Float, Double** → store numbers  
- **Character** → store single letters  
- **Boolean** → true/false values  
- **Pointer** → stores memory addresses  

---

## 2. Non-Primitive Data Structure
These are more advanced and can hold multiple values.  
They are further divided into **Linear** and **Non-Linear**.

---

### A. Linear Data Structures
Data is stored in a **sequence (one after another)**.

#### (i) Array
- Fixed-size collection of elements of the same type.  
- We can access by index.  

**Example:**  
Seats in a theater 🎭. Each seat (index) holds exactly one person (value).  
We can directly go to seat no. 10 (like `arr[10]`).  

---

#### (ii) Linked List
- Collection of nodes where each node has: **Data** and **Pointer**  
- Pointer links to the next node.  

**Example:**  
Treasure hunt game 🗺️: Each clue tells you where the next clue is.  
Each Node links to another one by one.  

---

#### (iii) Stack
- Follows **LIFO (Last In, First Out)**.  
- Insert & delete only from the **top**.  

**Example:**  
Stack of plates 🍽️ — Always remove and insert the **top plate first**.  
Undo/Redo in text editors also works like a stack.  

---

#### (iv) Queue
- Follows **FIFO (First In, First Out)**.  
- Insert at the **back**, remove from the **front**.  

**Example:**  
People standing in a line at a ticket counter 🎟️.  
The first person in line gets the ticket first.  

---

#### (v) Deque (Double Ended Queue)
- Can insert and delete from **both ends**.  

**Example:**  
Bus with two doors 🚌 — passengers can enter/exit from **front or back**.  

---

#### (vi) Hash Table (Hash Map)
- Stores data in **key-value pairs**.  
- Very fast access using a **hash function**.  

🔑 **Hash Function:**  
A formula that takes an input (key) and converts it into a fixed-size number (hash code).  
That number is used as an index in the hash table.  

**Example:**  
Imagine a **library** 📚:  
- You don’t scan every shelf to find a book.  
- Instead, you assign a formula (hash function) to decide which shelf the book goes on.  

- Book “Harry Potter” → Shelf 12  
- Book “Lord of the Rings” → Shelf 5  

When someone asks for “Harry Potter”, you jump directly to Shelf 12.  

---

### B. Non-Linear Data Structures
Data is stored in a **hierarchical or network-like structure**.

#### (i) Tree
- Hierarchical structure with **root node** and **child nodes**.  

**Example:**  
Family tree 👨‍👩‍👧 — grandparents → parents → children.  
File system on your computer (folders inside folders).  

---

#### (ii) Binary Tree / Binary Search Tree (BST)
- Each node has at most **2 children**.  

**Example:**  
Yes/No decision making game (20 Questions).  

---

#### (iii) Heap
- A special tree used for **priority-based tasks**.  
- **Max Heap** → largest element at top.  
- **Min Heap** → smallest element at top.  
- **Uses** → Priority queues, scheduling, heap sort.  

**Example:**  
Hospital emergency room 🚑 — patients with high priority are treated first.  

---

#### (iv) Graph
- Collection of **nodes (vertices)** and **connections (edges)**.  

- **Nodes (Vertices):** represent entities (people, cities, computers).  
- **Edges (Links):** represent relationships or paths.  

**Example:**  
- Google Maps 🗺️ — Cities = nodes, Roads = edges.  
- Social media 👥 (Facebook friends network).  

**Why Graphs are Useful?**  
- Navigation → Google Maps shortest route  
- Social Networks → Friend recommendations  
- Search Engines → Ranking web pages (Google’s PageRank uses graphs)  

---
