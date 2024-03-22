# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
  - [References](#references)

## Explanation
> Binary search is an efficient searching algorithm used to find a target element within a sorted collection. It works by repeatedly dividing the search interval in half until the target element is found or the interval is empty.

<ins>***Procedure:***</ins>
- Begin with the entire sorted collection.
- Compare the target element with the middle element of the collection.
- If the target element matches the middle element, the search is complete.
- If the target is less than the middle element, continue searching in the left half.
- If the target is greater than the middle element, continue searching in the right half.
- Repeat the process until the target is found or the search interval is empty.

<ins>***Algorithm :***</ins> `mid = (low + high) / 2`
- Below is the algorithm of Binary Search.
  1. Initialise `n = size` of array, `low = 0`, `high = n-1`. We will use low and high to determine the left and right ends of the array in which we will be searching at any given time
  2. if `low > high`, it means we cannot split the array any further and we could not find K. We return -1 to signify that the element K was not found
  3. else `low <= high`, which means we will split the array between low and high into two halves as follows:
      - Initialise `mid = (low + high) / 2`, in this way we split the array into two halves with arr[mid] as its middle element
      - if `arr[mid] < K`, it means the middle element is less than K. Thus, all the elements on the left side of the mid will also be less than K. Hence, we repeat step 2 for the right side of mid. We do this by setting the value of `low = mid+1`, which means we are ignoring all the elements from low to mid and shifting the left end of the array to mid+1
      - if `arr[mid] > K`, it means the middle element is greater than K. Thus, all the elements on the right side of the mid will also be greater than K. Hence, we repeat step 2 for the left side of mid. We do this by setting the value of `high = mid-1`, which means we are ignoring all the elements from mid to high and shifting the right end of the array to mid-1
      - else `arr[mid] == K`, which means the middle element is equal to K and we have found the element K. Hence, we do not need to search anymore. We return mid directly from here signifying that mid is the index at which K was found in the array

### Complexity
<table>
  <tr>
    <td><I>Time Complexity<I></td> 
    <td>Best</td> 
    <td>O(1)</td>  
  </tr>
  <tr>
    <td></td>
    <td>Average</td>
    <td>O(logN)</td>
  </tr>
  <tr>
    <td></td>
    <td>Worst</td>
    <td>O(logN)</td>
  </tr>
  <tr>
    <td><I>Space Complexity<I></td>
    <td></td>
    <td>O(1)</td>
  </tr>  
</table>

## References
* [Binary Search Scaler](https://www.scaler.com/topics/data-structures/binary-search-algorithm/)
