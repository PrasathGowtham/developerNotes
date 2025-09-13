
# Types of Algorithms

Algorithms are classified based on how problems are solved or the approach used to solve the problem.

---

## 1️⃣ Brute Force Algorithm
👉 Tries all possible solutions until it finds the correct one.  
Simple but inefficient for large data.

**📌 Example:**  
Forget your mobile PIN → You try `0000`, `0001`, `0002` … until the phone unlocks.

---

## 2️⃣ Divide and Conquer
👉 Breaks the problem into smaller sub-problems, solves them individually, then combines results.

**📌 Example:**  
Searching a word in a dictionary:  
Open the middle page → check if the word is before or after → repeat with half section.

---

## 3️⃣ Greedy Algorithm
👉 Makes the best choice at each step hoping it leads to the global solution.

**📌 Example:**  
Coin change problem 🪙: To make ₹43 using minimum coins → Pick the largest coin first  
(₹20 → ₹20 → ₹2 → ₹1).

---

## 4️⃣ Dynamic Programming (DP)
👉 Solves problems by storing past results and reusing them (avoids recalculating).

**📌 Example:**  
Climbing stairs: You can take 1 or 2 steps. To reach step `n`,  
store results of `n-1` and `n-2` to avoid recalculating.

---

## 5️⃣ Backtracking
👉 Tries solutions step by step, goes back (undoes) if a path doesn’t work.

**📌 Example:**  
Sudoku solving 🌀: Move forward until stuck → go back → try another path.

---

## 6️⃣ Recursive Algorithm
👉 A function calls itself until it reaches a base case.

**📌 Example:**  
Factorial of 5 → `5 * factorial(4)` → `4 * factorial(3)` … until `1`.

---

## 7️⃣ Searching Algorithms
👉 Used to find data in a collection of data.

- **Linear Search** → Check one by one (like finding a name in attendance register).  
- **Binary Search** → Divide and search (like finding a word in dictionary).

---

## 8️⃣ Sorting Algorithms
👉 Arrange data in a particular order.

- **Bubble Sort** → Compare neighbors, swap if needed.  
- **Quick Sort / Merge Sort** → Divide and conquer approach.  

**📌 Example:**  
Sorting student marks from lowest to highest.

---

## 9️⃣ Graph Algorithms
👉 Work on graph structures (nodes + edges).

**📌 Example:**  
- Shortest path (Google Maps 🚗).  
- Connect computers with minimum cable cost.  

⚡ **Used in:** Navigation, social networks, networking.

---

## 🔟 Hashing Algorithms
👉 Use a hash function to map data into fixed-size values.  
Gives very fast access (**O(1)** on average).

**📌 Example:** 
	-	Dictionary: Word → Key, Meaning → Value.	
	-	Instead of scanning all pages, jump directly.
	⚡ **Used in:** Password storage, caches, database indexing.

