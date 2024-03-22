# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity) 
  - [Code](#Code)
  - [References](#references)

## Explanation
**Iteration 1 (i = 0)**
* Find the smallest element in the unsorted list i.e. min(a[i]) where 0 <= i < 5.
* It can be said that the smallest element is 1 at index 3.
* Swap a[0] and a[3].
* Now array will look like a = [ 1, 3, 2, 9, 5 ]

**Iteration 2 (i = 1)**
* Find the smallest element in the unsorted list i.e. min(a[i]) where 1 <= i < 5.
* It can be said that the smallest element is 2 at index 2.
* Swap a[1] and a[2].
* Now array will look like a = [ 1, 2, 3, 9, 5 ]

**Iteration 3 (i = 2)**
* Find the smallest element in the unsorted list i.e. min(a[i]) where 2 <= i < 5.
* It can be said that the smallest element is 3 at index 3.
* Swap a[3] and a[3].
* Now array will look like a = [ 1, 2, 3, 9, 5 ]

**Iteration 4 (i = 3)**
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
