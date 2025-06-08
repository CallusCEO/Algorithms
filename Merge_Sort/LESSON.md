### Merge Sort

Merge Sort is a divide-and-conquer sorting algorithm that splits an array into smaller subarrays, sorts them, and then merges them back together in sorted order. It’s highly efficient for large datasets and is a stable sorting method, meaning it preserves the relative order of equal elements.

#### How Merge Sort Works

1. **Divide**: Split the array into two halves recursively until each subarray contains a single element (which is inherently sorted).
2. **Conquer**: Merge the subarrays back together in sorted order by comparing elements from each half and combining them into a single sorted array.
3. **Repeat**: Continue merging until the entire array is sorted.

#### Example in Python

Here’s a clear implementation of Merge Sort:

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    # Divide the array into two halves
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    # Merge the sorted halves
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0

    # Compare elements from both halves and merge in sorted order
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    # Add remaining elements from left, if any
    result.extend(left[i:])
    # Add remaining elements from right, if any
    result.extend(right[j:])

    return result

# Example usage
arr = [64, 34, 25, 12, 22, 11, 90]
sorted_arr = merge_sort(arr)
print(sorted_arr)  # Output: [11, 12, 22, 25, 34, 64, 90]
```

#### Key Characteristics

-   **Time Complexity**: O(n log n) in all cases (best, average, worst), where n is the number of elements.
-   **Space Complexity**: O(n), as it requires additional space to store the merged arrays.
-   **Stable**: Maintains the relative order of equal elements.
-   **Not In-Place**: Requires extra memory, unlike some other sorting algorithms (e.g., Quick Sort).

#### Applications

-   **Large Datasets**: Ideal for sorting big data, especially when stability is needed.
-   **Linked Lists**: Efficient for sorting linked lists, as it doesn’t require random access to elements.
-   **External Sorting**: Used in scenarios where data doesn’t fit in memory (e.g., database sorting).

Merge Sort’s predictable performance and stability make it a go-to choice for many sorting tasks, especially when working with complex or large-scale data.
