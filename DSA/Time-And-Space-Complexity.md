
# What is Time Complexity?

Time complexity is a way to measure how the runtime of an algorithm grows as the size of input data (n) increases.

# What is Space Complexity?

Space complexity is a way to measure how much extra memory an algorithm uses as input size (n) increases.

# What is Big-O?

Big-O tells us how fast or slow an algorithm grows when the input size grows.

---

## 1. O(1) → Constant Time
No matter how much data you have, the time is the same.

- **Example in coding:** `arr[5]` → directly access index 5.  
- **Real-world analogy:** Looking at the 10th page of a book directly (you don’t care if the book has 20 pages or 1000 pages).  

✅ Always takes the same time.

---

## 2. O(n) → Linear Time
Time increases in the same proportion as input.

- **Example in coding:** Searching a number in an unsorted list (check one by one).  
- **Real-world analogy:** Taking attendance in class by calling each student’s name.  

If 10 students → 10 checks.  
If 100 students → 100 checks.  

✅ Grows straight with input.

---

## 3. O(log n) → Logarithmic Time
You cut the problem in half every time.

- **Example in coding:** Binary Search.  
- **Real-world analogy:** Searching a word in a dictionary:  
  - Don’t start from the first page.  
  - Open the middle, decide left or right, keep dividing.  

If 1000 pages → you don’t flip 1000 times, only ~10 flips.  

✅ Very fast for large inputs.

---

## 4. O(n²) → Quadratic Time
For each item, you check every other item.

- **Example in coding:** Bubble Sort (compare each pair of numbers).  
- **Real-world analogy:** In a class of students, everyone shakes hands with everyone else 🤝.  

Work multiplies because of nested loops.  
10 students → 100 handshakes.  
100 students → 10,000 handshakes.  

✅ Grows very quickly as input increases.

---

## 5. O(2ⁿ) → Exponential Time
You try all possibilities.

- **Example in coding:** Recursive Fibonacci (without memoization).  
- **Real-world analogy:** Packing outfits — if you try every possible combination of shirts and pants.  

Work doubles for each new input.  
If 5 items → 32 possibilities.  
If 10 items → 1024 possibilities.  

✅ Becomes impossible very fast.

---

## 6. O(n!) → Factorial Time
You check all arrangements of data.

- **Example in coding:** Traveling Salesman Problem (brute force).  
- **Real-world analogy:** Seating 5 friends in chairs → all possible seatings = 120 ways.  
  Seating 10 friends → 3,628,800 ways!  

✅ Totally unmanageable for large inputs.

---

# ✅ In short:
- **O(1):** Same time always. (Direct access)  
- **O(n):** Grows with input. (Attendance)  
- **O(log n):** Divide & conquer. (Dictionary search)  
- **O(n²):** Compare everything with everything. (Handshakes)  
- **O(2ⁿ):** All possibilities. (Outfits)  
- **O(n!):** All arrangements. (Seating)  

---

# Ordering (from fastest → slowest growth)
`O(1)  <  O(log n)  <  O(n)  <  O(n²)  <  O(2ⁿ)  <  O(n!)`

**Constant < Logarithmic < Linear < Quadratic < Exponential < Factorial**
