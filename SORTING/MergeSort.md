# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
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
