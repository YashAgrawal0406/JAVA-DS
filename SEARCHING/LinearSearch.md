
# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
    - [Linear Search](Linear-Search)
    - [Main](Main)  
  - [References](#references)


## Explanation
> Linear search is a straightforward searching algorithm that sequentially checks each element of a collection until the target element is found or the entire collection has been traversed. It starts from the beginning of the collection and compares each element with the target element until a match is found. If the target element is found, the algorithm returns the index of that element; otherwise, it returns -1 to indicate that the element is not present in the collection. Linear search is simple to implement and works efficiently on unsorted or small collections but may become inefficient on large datasets due to its linear time complexity of O(n), where n is the number of elements in the collection.

### Complexity
<table>
  <tr>
    <td><I>Time Complexity<I></td> 
    <td>O(n)</td>  
  </tr>
  <tr>
    <td><I>Space Complexity<I></td>
    <td>O(1)</td>
  </tr>  
</table>

## Code
### Linear Search
```Java
public static int linearSearch(int[] arr, int target) {
    // Iterate through each element of the array
    for (int i = 0; i < arr.length; i++) {
        // If the current element matches the target, return its index
        if (arr[i] == target) {
            return i;
        }
    }
    // If the target element is not found, return -1
    return -1;
}
```

### Main
```Java
int[] arr = {4, 2, 8, 1, 9, 5, 7};
int target = 5;
int index = linearSearch(arr, target);
if (index != -1) {
    System.out.println("Element " + target + " found at index " + index + ".");
} else {
    System.out.println("Element " + target + " not found in the list.");
}
```

## References
* [Linear Search Scaler](https://www.scaler.com/topics/data-structures/linear-search-algorithm/)
* [Linear Search Scaler](https://www.scaler.com/topics/linear-search-in-java/)
