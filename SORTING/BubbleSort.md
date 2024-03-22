# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
  - [Code](#Code)

## Explanation
- traverse from left and compare adjacent elements and the higher one is placed at right side. 
- In this way, the largest element is moved to the rightmost end at first. 
- This process is then continued to find the second largest and place it and so on until the data is sorted.

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
