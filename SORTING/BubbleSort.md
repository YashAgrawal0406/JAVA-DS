# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)

## Explanation
- traverse from left and compare adjacent elements and the higher one is placed at right side. 
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
