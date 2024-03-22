# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
  - [References](#references)

## Explanation
> Bubble sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process is repeated until the list is sorted. In each pass, the largest (or smallest, depending on the sorting order) unsorted element "bubbles" up to its correct position. Bubble sort has a time complexity of O(n^2), making it inefficient for large lists but easy to understand and implement. It is primarily used for educational purposes or for sorting small datasets.

- Traverse from left to right and compare adjacent elements move the higher value element to the right.
- We perform swapping when we find that current element is larger the next element
- In this way, the largest element is moved to the rightmost end at first. 
- This process is then continued to find the second largest and place it and so on until the data is sorted.

**First Pass:** 
The largest element is placed in its correct position, i.e., the end of the array.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/bd5890a8-e118-40fa-a4dc-4195d34ae76f)


**Second Pass:**
Place the second largest element at correct position

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/c2f76fa5-fb06-4a02-a46f-f9255836573f)

**Third Pass:**
Place the remaining two elements at their correct positions.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/92531ccd-a26c-450a-907e-a4859680b12f)


### Complexity
<table>
  <tr>
    <td><I>Time Complexity<I></td> 
    <td>Best</td> 
    <td>O(n)</td>  
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

public static void bubbleSort() {
    int[] arr = {7, 8, 3, 1, 2};

    for (int i = 0; i < arr.length - 1; i++) {
        for (int j = 0; j < arr.length - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    for (int i = 0; i < arr.length; i++)
        System.out.print(arr[i] + " ");
}

```

## References
* [BubbleSort Scaler](https://www.scaler.com/topics/data-structures/bubble-sort/)
* [BubbleSort GeeksForGeeks](https://www.geeksforgeeks.org/bubble-sort/)
* [BubbleSort Javapoint](https://www.javatpoint.com/bubble-sort)

