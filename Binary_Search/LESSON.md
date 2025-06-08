## Binary Search

Binary Search is an efficient algorithm for finding a specific element in a **sorted list** or array. Unlike linear search, which checks every element sequentially, Binary Search takes advantage of the sorted order to eliminate half of the remaining elements with each step, making it much faster for large datasets.

### How Binary Search Works

Binary Search operates by repeatedly dividing the search range in half. Here’s the step-by-step process:

1. **Initialization**: Start with the entire sorted array, defining two pointers: `low` (the start of the array) and `high` (the end of the array).
2. **Find the Middle**: Calculate the middle index of the current range using `mid = (low + high) // 2`.
3. **Comparison**:
    - If the middle element is the target value, return its index.
    - If the target is less than the middle element, adjust `high` to `mid - 1` and search the left half.
    - If the target is greater than the middle element, adjust `low` to `mid + 1` and search the right half.
4. **Repeat**: Continue dividing and searching until the target is found or `low` exceeds `high`, indicating the target isn’t in the array.

### Example in Python

Here’s a simple implementation of Binary Search:

```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid  # Target found, return its index
        elif arr[mid] < target:
            low = mid + 1  # Search right half
        else:
            high = mid - 1  # Search left half
    return -1  # Target not found

# Test it
arr = [2, 3, 4, 10, 40, 50, 60, 70]
target = 10
result = binary_search(arr, target)
print(f"Element {target} found at index {result}")  # Output: Element 10 found at index 3
```

### Key Characteristics

-   **Time Complexity**:
    -   Best Case: O(1) if the target is at the middle on the first try.
    -   Average and Worst Case: O(log n), as the search space halves with each step.
-   **Space Complexity**:
    -   O(1) for the iterative version (shown above).
    -   O(log n) for the recursive version due to the call stack.
-   **Prerequisite**: The input array must be sorted. If it’s not, you’d need to sort it first (e.g., using an O(n log n) algorithm like Merge Sort), which would affect the overall complexity.

### Applications

Binary Search is widely used due to its efficiency:

-   **Searching**: Finding an element in a sorted dataset (e.g., database records, phonebooks).
-   **Problem Solving**: Used as a building block in algorithms like finding square roots or solving equations numerically.
-   **Data Structures**: Underpins operations in balanced binary search trees and other sorted collections.

### Optimizations and Notes

-   **Avoid Overflow**: In languages with fixed integer sizes, use `mid = low + (high - low) // 2` instead of `(low + high) // 2` to prevent integer overflow.
-   **Recursive vs. Iterative**: The iterative version (shown above) is generally preferred for better space efficiency, though a recursive version is also common and easier to understand for some.

### Example Walkthrough

For `arr = [2, 3, 4, 10, 40, 50, 60, 70]` and `target = 10`:

1. `low = 0`, `high = 7`, `mid = 3`, `arr[3] = 10` → Found at index 3.
   If the target were 5:
1. `low = 0`, `high = 7`, `mid = 3`, `arr[3] = 10 > 5`, `high = 2`.
1. `low = 0`, `high = 2`, `mid = 1`, `arr[1] = 3 < 5`, `low = 2`.
1. `low = 2`, `high = 2`, `mid = 2`, `arr[2] = 4 < 5`, `low = 3`.
1. `low > high`, return -1 (not found).

Binary Search’s logarithmic efficiency makes it a cornerstone of computer science, ideal for large, sorted datasets where quick lookups are needed.
