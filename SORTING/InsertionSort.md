# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
  - [References](#references)

## Explanation
> Insertion sort is a simple sorting algorithm that builds the final sorted array one item at a time. It iterates through the input list, removing one element at a time and finding its correct position within the sorted portion of the array. It does this by shifting all elements greater than the current element one position to the right. This process continues until all elements are sorted. Insertion sort is efficient for small datasets or nearly sorted lists and has a time complexity of O(n^2). It's also considered efficient for small datasets and often used in combination with other sorting algorithms.

Let's understand this by sorting an array of integers, 

`Initial Array: [ 13, 12, 18, 2, 5 ]`

<ins>***First Pass:***</ins>
- Compare the first two elements (13 and 12). Since 13 is greater than 12, they are swapped to maintain ascending order.
- New array: `[ 12, 13, 18, 2, 5 ]`
  
<ins>***Second Pass:***</ins>
- Move to the next element (18) and compare it with its predecessors. It's already in the correct position relative to 12 and 13, so no swaps are needed.
- Array remains: `[ 12, 13, 18, 2, 5 ]`

<ins>***Third Pass:***</ins>
- The focus shifts to the fourth element (2), which is compared with its predecessors to find its rightful spot.
- Initial comparison with 18 shows 2 is smaller, swap 2 and 18: `[ 12, 13, 2, 18, 5 ]`
- Continuing the comparison, 2 is also smaller than 13, leading to another swap: `[ 12, 2, 13, 18, 5 ]`
- Finally, 2 is compared with 12 and, being smaller, is swapped again, positioning it correctly at the array's start: `[ 2, 12, 13, 18, 5 ]` Now, 2 is it correct position.
  
<ins>***Fourth Pass:***</ins>
- Attention now turns to the last element (5).
- Initially, 5 is compared with 18 and found to be smaller, swap 18 and 5: `[ 2, 12, 13, 5, 18 ]`
- The comparison continues with 13, and since 5 is smaller, another swap occurs: `[ 2, 12, 5, 13, 18 ]`
- Lastly, 5 is compared with 12, and being smaller, necessitates the final swap, placing it in its proper position: `[ 2, 5, 12, 13, 18 ]`
- This final pass ensures that 5 is inserted between 2 and 12, completing the sorting process with the array now fully sorted.
Finally, the array is sorted completely.







