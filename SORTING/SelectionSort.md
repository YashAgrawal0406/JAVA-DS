# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
  - [References](#references)

## Explanation
> Selection sort is a simple sorting algorithm that works by repeatedly selecting the minimum (or maximum) element from an unsorted portion of the list and moving it to the beginning (or end) of the sorted portion. The algorithm divides the input list into two parts: the sorted sublist and the unsorted sublist. Initially, the sorted sublist is empty, and the unsorted sublist contains all the elements. In each iteration, the algorithm finds the smallest element in the unsorted sublist and swaps it with the leftmost unsorted element, thus expanding the sorted sublist by one element. This process continues until the entire list is sorted. Selection sort has a time complexity of O(n^2), making it inefficient for large lists but suitable for small lists or nearly sorted lists due to its simplicity.

`[9, 3, 2, 1, 5]`

<ins>***Iteration 1 (i = 0)***</ins>
* Find the smallest element in the unsorted list i.e. min(a[i]) where 0 <= i < 5.
* It can be said that the smallest element is 1 at index 3.
* Swap a[0] and a[3].
* Now array will look like a = [ 1, 3, 2, 9, 5 ]

<ins>***Iteration 2 (i = 1)***</ins>
* Find the smallest element in the unsorted list i.e. min(a[i]) where 1 <= i < 5.
* It can be said that the smallest element is 2 at index 2.
* Swap a[1] and a[2].
* Now array will look like a = [ 1, 2, 3, 9, 5 ]

<ins>***Iteration 3 (i = 2)***</ins>
* Find the smallest element in the unsorted list i.e. min(a[i]) where 2 <= i < 5.
* It can be said that the smallest element is 3 at index 3.
* Swap a[3] and a[3].
* Now array will look like a = [ 1, 2, 3, 9, 5 ]

<ins>***Iteration 4 (i = 3)***</ins>
* Find the smallest element in the unsorted list i.e. min(a[i]) where 3 <= i < 5.
* It can be said that the smallest element is 5 at index 4.
* Swap a[3] and a[4].
* Now array will look like a = [ 1, 3, 2, 9, 5 ]

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/c789e18d-294e-4c48-b80c-be507b8ea9b8)

### Complexity
<table>
  <tr>
    <td><I>Time Complexity<I></td> 
    <td>Best</td> 
    <td>O(n^2)</td>  
  </tr>
  <tr>
    <td></td>
    <td>Average</td>
    <td>O(n^2)</td>
  </tr>
  <tr>
    <td></td>
    <td>Worst</td>
    <td>O(n^2)</td>
  </tr>
  <tr>
    <td><I>Space Complexity<I></td>
    <td>Worst</td>
    <td>O(1)</td>
  </tr>  
</table>

## Code

```Java
public static void selectionSort() {
    int[] arr = {7, 8, 3, 1, 2};

    for (int i = 0; i < arr.length; i++) {
        int smallest = i;
        for (int j = i; j < arr.length; j++) {
            if (arr[j] < arr[smallest]) {
                smallest = j;
            }
        }
        int temp = arr[i];
        arr[i] = arr[smallest];
        arr[smallest] = temp;
    }
    for (int i = 0; i < arr.length; i++)
        System.out.print(arr[i] + " ");
}
```

## References
* [SelectionSort Scaler](https://www.scaler.com/topics/data-structures/selection-sort/)
* [SelectionSort Scaler](https://www.scaler.com/topics/selection-sort-java/)
