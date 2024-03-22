# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
    - [Divide](#Divide)
    - [Conqure](#Conqure)
    - [Main](#Main) 
  - [References](#references)

## Explanation
> Merge sort is a popular sorting algorithm that follows the divide-and-conquer approach. It recursively divides the input array into smaller subarrays until each subarray consists of only one element, which is inherently sorted. Then, it merges these subarrays back together, combining them in a sorted order until the entire array is sorted. The merging process involves comparing elements from the divided subarrays and arranging them in the correct order. Merge sort has a time complexity of O(n log n), making it efficient for large datasets, and it's stable, meaning it preserves the order of equal elements.

<ins>***Divide and Conquer Strategy***</ins>

- Now that we have a fair understanding of what divide and conquer is, let us try and understand how that is done to sort an array of integers.
- Let us consider an array, array that consists of n unsorted integers. Our end goal is to sort the array.
- Let us consider an array = `{38,27,43,3,9,82,10}.`
  
![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/50ead0fc-098c-4466-b22f-4d777a2836ae)


***1. Divide***
   - In this step, we find the midpoint of the given array by using the formula `mid = start + (end-start)/2`

***2. Conquer***
   - In this step, we divide the array into subarrays using the midpoint calculated. We recursively keep dividing the array and keep calculating the midpoint for doing the same. It is important to note that a single array element is always sorted.
   - So, our aim is to continuously divide until all elements in the array are single array elements. Once that is done, the array elements are combined back to form a sorted array.
     
![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/d13b3353-9ce7-4109-89d7-dcbf29b00c2d)
   - As mentioned above, our goal is to keep dividing till all elements in the array are single array elements hence, this is the base case i.e. when there are n subarrays of the original array that consisted of n integers. It is now the turn is to sort them and combine them.

***3. Combine***
   - Now that all our subarrays are formed, it is now time to combine them in sorted order.
     
![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/1f2e5d6c-ff72-4231-a13b-1e5953f4426f)

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
    <td>O(nLogn)</td>
  </tr>
  <tr>
    <td><I>Space Complexity<I></td>
    <td>Worst</td>
    <td>O(n)</td>
  </tr>  
</table>

## Code
### Divide
```Java
public static void divide(int[] arr, int si, int ei) {
    if (si >= ei)
        return;

    int mid = si + (ei - si) / 2; //(si + ei)/2 the addition ei + si can go beyond int range

    divide(arr, si, mid);
    divide(arr, mid + 1, ei);
    conquer(arr, si, mid, ei);
}
```

### Conqure
```Java
public static void conquer(int[] arr,int si,int mid, int ei){
    int merged[] = new int[ei - si + 1];

    int idx1 = si;
    int idx2 = mid + 1;
    int x = 0;

    while(idx1 <= mid && idx2 <= ei)
    {
        if(arr[idx1] <= arr[idx2])
        {
            merged[x] = arr[idx1];
            x++;
            idx1++;
        } else {
            merged[x] = arr[idx2];
            x++;
            idx2++;
        }
    }
    while(idx1 <= mid )
    {
        merged[x] = arr[idx1];
        x++;
        idx1++;
    }
    while(idx2 <= ei )
    {
        merged[x] = arr[idx2];
        x++;
        idx2++;
    }

    for(int i = 0,j =si; i < merged.length;i++,j++)
    {
        arr[j] = merged[i];
    }
}
```

### Main
```Java
MergeSort mergeSort = new MergeSort();
int[] arr1 = {6, 3, 9, 5, 2, 8};
n = arr1.length;
mergeSort.divide( arr1, 0, n-1);
for (int i = 0; i < n; i++) {
    System.out.print(arr[i] + " ");
}
```

## References
* [MergeSort Scaler](https://www.scaler.com/topics/data-structures/merge-sort-algorithm/)
* [MergeSort Scaler](https://www.scaler.com/topics/merge-sort-program-in-java/)
