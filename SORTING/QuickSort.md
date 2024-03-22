# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
    - [QuickSort](#QuickSort)
    - [Partition](#Partition)
    - [Main](#Main) 
  - [References](#references)
 

## Explanation
> Quick sort is a fast and efficient sorting algorithm that follows the divide-and-conquer approach. It works by selecting a pivot element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot. The process is recursively applied to the sub-arrays until they are sorted. Unlike merge sort, quick sort does not require additional space for merging, making it space-efficient. Quick sort has an average time complexity of O(n log n) and a worst-case time complexity of O(n^2) when the pivot selection is poor, but its average-case performance is often superior to other sorting algorithms.

<ins>***Steps for Sorting***</ins>
- An element will be selected as the pivot (middle element in our example). 
- The original array would be split into a subarray on the left of the pivot and the other subarray on the right of it.
- The partition will be done on the left subarray and right subarray in the same way.

<ins>***The Idea for Partition***</ins>
- Two pointers i and j will be taken where the pointer i is on the leftmost and j is on the rightmost element. 
- We'll keep moving pointer I from left to right until we find any element greater than the pivot lying at its left.
- Similarly, pointer j will be moved from right to left until an element smaller than the pivot is found at its right.
- When both the pointer stops due to the above-highlighted conditions, both the elements at positions i and j will be swapped. After swapping, both the pointers will start moving again in their aforementioned direction. It continues until both pointers reach the pivot. 
- Finally, we have two subarrays on which the same steps would be performed again until we approach a single element in any of the subarrays.
> We have an example of an array, say num, that needs to be sorted with the help of the Quicksort algorithm.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/2f5e8335-6ae4-48ba-9291-9d70d53fd3a7)

> Let us consider a situation where a pivot is a middle element of the array. There is a pointer for the leftmost element as well as the rightmost element. The left pointer moves forward till it finds the elements smaller than the pivot. On the contrary, the right pointer continues moving to the left till it finds greater than the pivot.

> Initially, the pivot will be 7. The element at the 0th index is not smaller than the pivot. Also, the rightmost element at index 6 is not greater than the pivot. So, the pointers stop at this position and wait for the number to get swapped, following which, i increases and j decreases.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/c9d71932-e1fe-457e-9e2c-3d7b3ed07562)

> The element at the 1st index is not smaller than the pivot. The rightmost element at index 5 is greater than the pivot. So, the pointer i stops at this position while j gets decremented.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/f192cc3f-8993-43b5-84af-331b7963b99d)

> Again, the element at the 1st index is not smaller than the pivot, so the left pointer stays at index 1. The rightmost element at index 4 is greater than the pivot. So, j gets decremented.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/690a2ce4-bf22-4abe-8eae-74564af308d6)

> Now, the element at 3rd index is the pivot itself, which cannot be less than itself (upon checking if num[3]<pivot), so this is where pointer j stops and the elements 23 and 7 are swapped. Then, i increases while j decreases.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/813672b1-e9c8-4036-8791-e5c510ba2dc9)

> When pointer i and j are at the same position, the loop terminates and finally, pivot 7 is now at its appropriate position. Now, the same recursive quick sort method will be called on the left as well as the right subarrays.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/00fc22a7-cb41-45d9-bde5-ef5ef23b6824)

> Element 6, being the only element in the left subarray, is already sorted. So, we need to perform Quicksort on the right subarray in the same manner as we did above.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/e193a151-24ee-4fc8-81fb-044283b39e1d)

> Finally, the sorted array would be obtained.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/b8ce100d-a344-41a5-ad4c-64b4f640f9ce)


### Complexity
<table>
  <tr>
    <td><I>Time Complexity<I></td> 
    <td>Best</td> 
    <td>O(nLogn)</td>  
  </tr>
  <tr>
    <td></td>
    <td>Average</td>
    <td>O(nLogn)</td>
  </tr>
  <tr>
    <td></td>
    <td>Worst</td>
    <td>O(n^2)</td>
  </tr>
  <tr>
    <td><I>Space Complexity<I></td>
    <td>Worst</td>
    <td>O(log n)</td>
  </tr>  
</table>



## Code
### QuickSort
```Java
public static void quickSort(int[] arr, int low, int high) {
    if (low < high) {
        int pivot = partition(arr, low, high);
        quickSort(arr, low, pivot - 1);
        quickSort(arr, pivot + 1, high);
    }
}
```
    
### Partition
```Java
public static int partition(int[] arr, int low, int high) {
  int pivot = arr[high];
  int i = low - 1;
  
  for (int j = low; j < high; j++) {
      if (arr[j] < pivot) {
          i++;
          //swap
          int temp = arr[i];
          arr[i] = arr[j];
          arr[j] = temp;
      }
  }
  i++;
  int temp = arr[i];
  arr[i] = arr[high];
  arr[high] = temp;
  return i; //this my pivot index
}
```

### Main
```Java
int[] arr = {6,3,9,5,2,8};
int n = arr.length;
QuickSort.quickSort(arr,0,n-1);
//print
for (int i = 0; i < n; i++) {
    System.out.print(arr[i] + " ");
}
```


## References
* [QuickSort Scaler](https://www.scaler.com/topics/data-structures/quick-sort-algorithm/)
* [QuickSort Scaler](https://www.scaler.com/topics/quick-sort-in-java/)
