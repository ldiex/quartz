*Quicksort* is a highly efficient sorting algorithm that works by partitioning an array into smaller sub-arrays based on a chosen pivot element. It's a divide-and-conquer algorithm that sorts elements in place.

The process of quicksort is:
1. **Choose a Pivot**: Select an element from the array to serve as the *pivot*. The pivot selection can greatly affect the performance of the algorithm. A common approach is to choose the first, last, or middle element as the pivot, but more sophisticated methods exist for choosing pivots to improve performance, such as the median-of-three method
2. **Partitioning**: Rearrange the elements of the array so that all elements smaller than the pivot are moved to its left, and all elements greater than the pivot are moved to its right. After this operation, the pivot element is in its correct sorted position. This is often done using two pointers ($i$ and $j$) that move towards each other, swapping elements as necessary.
3. **Recursion**: Recursively apply the above steps to the sub-arrays formed by the partition until the entire array is sorted. This step effectively divides the problem into smaller sub-problems and solves each recursively.
4. **Combine**: As the recursion unwinds, the sorted sub-arrays are combined to produce the final sorted array.

``` python
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[0]
        less_than_pivot = [x for x in arr[1:] if x <= pivot]
        greater_than_pivot = [x for x in arr[1:] if x > pivot]
        return quicksort(less_than_pivot) + [pivot] + quicksort(greater_than_pivot)

# Example usage
arr = [3, 6, 8, 10, 1, 2, 1]
sorted_arr = quicksort(arr)
print(sorted_arr)  # Output: [1, 1, 2, 3, 6, 8, 10]

```


