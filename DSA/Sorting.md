
# What is Sorting?

Sorting means arranging data in a particular order:

- **Ascending** (oldest → newest)  
- **Descending** (newest → oldest)  

---

## Why Sorting?

- **Faster Searching**  
  If data is sorted, searching becomes faster.  

- **Better for Organizing Data**  
  Helps present data in a meaningful way.  

---

## When to Use Sorting?

- When you want to **remove duplicates efficiently**  
- When **presenting data to users**  

👉 To organize data, improve efficiency, speed up searching, and present meaningful results.  

---

## Types of Sorting

### 1. Bubble Sort
- Repeatedly swap adjacent elements if they are in the wrong order.  
- The “largest” element bubbles up to the end in each pass.  

### 2. Selection Sort
- Repeatedly find the minimum element from the unsorted part and put it at the beginning.  

### 3. Insertion Sort
- Insert one element at a time into the correct position.  

### 4. Merge Sort
- Divide the array into two halves recursively until each subarray has one element.  
- Merge the subarrays back together in sorted order.  

### 5. Quick Sort
- Pick a pivot element.  
- Partition the array so that elements smaller than pivot go to the left, and greater than pivot go to the right.  
- Recursively apply the same logic to left and right subarrays.  

### 6. Heap Sort
- Build a max-heap (largest element at the root).  
- Extract the root (largest element), place it at the end, and heapify the remaining elements.  
- Repeat until the array is sorted.  

### 7. Radix Sort
- Sorts numbers digit by digit, starting either from the least significant digit (LSD) or the most significant digit (MSD).  
