*Bubble sort* is a simple sorting algorithm that works by repeatedly stepping through the list to be sorted, comparing each pair of adjacent items, and swapping them if they are in the wrong order. This process is repeated until no swaps are needed, indicating that the list is sorted. 

The algorithm gets its name because smaller elements "bubble" to the top of the list (beginning), while larger elements "sink" to the bottom (end) with each pass.

``` python
def bubble_sort(arr):
    n = len(arr)
    # Traverse through all elements in the list
    for i in range(n):
        # Last i elements are already in place, so we skip them
        swapped = False
        for j in range(0, n-i-1):
            # Traverse the array from 0 to n-i-1
            # Swap if the element found is greater than the next element
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                swapped = True
        # If no two elements were swapped by the inner loop, then break
        if not swapped:
            break

# Example usage:
if __name__ == "__main__":
    arr = [64, 34, 25, 12, 22, 11, 90]
    print("Unsorted array:", arr)
    bubble_sort(arr)
    print("Sorted array:", arr)

```

During the sorting algorithm, the total count of swapping action is the number of the [[Inversion|inversions]] in the original list. 