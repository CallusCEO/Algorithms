### Quick Sort

**Quick Sort**, a highly efficient and widely used sorting algorithm. Like Merge Sort, it follows a divide-and-conquer strategy, but it operates differently by sorting the array in-place (in its optimized form) and using a pivot to partition the data. Let’s dive into what Quick Sort is, how it works, and see it in action with an example.

#### What is Quick Sort?

Quick Sort is a sorting algorithm that selects a "pivot" element from the array and rearranges the other elements around it—those less than the pivot go to the left, and those greater go to the right. It then recursively applies the same process to the two resulting subarrays until the entire array is sorted. Its average-case efficiency and ability to sort in-place make it a favorite in practice.

#### How Quick Sort Works

Here’s the step-by-step process:

1. **Choose a Pivot**: Pick an element from the array to act as the pivot. A common choice is the last element, but it could be the first, middle, or even a random element.
2. **Partition**: Rearrange the array so that:
    - Elements less than or equal to the pivot are on its left.
    - Elements greater than the pivot are on its right.
    - The pivot ends up in its final sorted position.
3. **Recursively Sort**: Apply the same process to the subarrays on the left and right of the pivot.
4. **Base Case**: If a subarray has one or zero elements, it’s already sorted—no further action is needed.

#### Example in Python

Here’s a simple implementation of Quick Sort to illustrate how it works:

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[-1]  # Choose the last element as pivot
    left = [x for x in arr[:-1] if x <= pivot]  # Elements <= pivot
    right = [x for x in arr[:-1] if x > pivot]  # Elements > pivot
    return quick_sort(left) + [pivot] + quick_sort(right)

# Example usage
arr = [64, 34, 25, 12, 22, 11, 90]
sorted_arr = quick_sort(arr)
print(sorted_arr)  # Output: [11, 12, 22, 25, 34, 64, 90]
```

**Note**: This version uses extra space for clarity. In practice, Quick Sort is often implemented in-place by swapping elements within the array, reducing space usage.

#### How It Sorts: A Walkthrough

Let’s see how `[64, 34, 25, 12, 22, 11, 90]` becomes sorted:

-   Pivot = 90: Left = `[64, 34, 25, 12, 22, 11]`, Right = `[]`
-   Pivot = 11: Left = `[]`, Right = `[64, 34, 25, 12, 22]`
-   Pivot = 22: Left = `[12]`, Right = `[64, 34, 25]`
-   Pivot = 25: Left = `[]`, Right = `[64, 34]`
-   Pivot = 34: Left = `[]`, Right = `[64]`
-   Combine: `[11, 12, 22, 25, 34, 64, 90]`

#### Key Characteristics

-   **Time Complexity**:
    -   **Best and Average Case**: O(n log n) – very efficient for most inputs.
    -   **Worst Case**: O(n²) – occurs if the pivot is consistently the smallest or largest element (e.g., already sorted arrays with a bad pivot choice).
-   **Space Complexity**: O(log n) – due to the recursion stack in the in-place version.
-   **In-Place**: Yes, in optimized implementations (unlike the example above).
-   **Stability**: Unstable – equal elements may swap positions.

#### Why Use Quick Sort?

-   **Speed**: Its average-case O(n log n) performance is excellent for large datasets.
-   **Memory Efficiency**: In-place sorting minimizes extra memory usage.
-   **Flexibility**: Optimizations like random pivot selection can avoid the worst case, making it practical for real-world use.

#### Applications

-   General-purpose sorting of large datasets.
-   Memory-constrained environments due to its in-place capability.
-   Systems where average-case performance is prioritized over worst-case guarantees.

Quick Sort is a natural follow-up to Merge Sort, offering a different perspective on divide-and-conquer sorting with its own strengths.
