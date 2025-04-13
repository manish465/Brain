---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/largest-element-in-the-array-largest-element-in-the-array_5026279?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems
---
## Problem statement

Given an array _**‘arr’**_ of size _**‘n’**_ find the largest element in the array.

Example:

```
Input: 'n' = 5, 'arr' = [1, 2, 3, 4, 5]

Output: 5

Explanation: From the array {1, 2, 3, 4, 5}, the largest element is 5.
```

Detailed explanation ( Input/output format, Notes, Images )

##### Sample input 1:

```
6
4 7 8 6 7 6 
```

##### Sample output 1:

```
8
```

##### Explanation of sample input 1:

```
The answer is 8.
From {4 7 8 6 7 6}, 8 is the largest element.
```

##### Sample input 2:

```
8
5 9 3 4 8 4 3 10 
```

##### Sample output 2:

```
10
```

##### Expected Time Complexity:

```
O(n), Where ‘n’ is the size of an input array ‘arr’.
```

##### Constraints :

```
1 <= 'n' <= 10^5
1 <= 'arr[i]' <= 10^9

Time Limit: 1 sec
```

```Java
import java.util.* ;
import java.io.*; 

public class Solution {

    static int largestElement(int[] arr, int n) {
        // Write your code here.
        int largest = arr[0];

        for(int a : arr) {
            largest = Math.max(largest, a);
        }

        return largest;
    }
}
```