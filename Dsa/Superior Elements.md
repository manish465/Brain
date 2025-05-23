---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/superior-elements_6783446?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

There is an integer array ‘a’ of size ‘n’.
An element is called a Superior Element if it is greater than all the elements present to its right.
You must return an array all Superior Elements in the array ‘a’.

Note:

```
The last element of the array is always a Superior Element. 
```

Example

```
Input: a = [1, 2, 3, 2], n = 4

Output: 2 3

Explanation: 
a[ 2 ] = 3 is greater than a[ 3 ]. Hence it is a Superior Element. 
a[ 3 ] = 2 is the last element. Hence it is a Superior Element.
The final answer is in sorted order.
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1:**

```
4 
1 2 2 1
```

**Sample Output 1:**

```
1 2
```

**Explanation of Sample Input 1:**

```
Element present at the last index is '1' and is a superior element since there are no integers to the right of it.
Element present at index 2 (0-indexed) is '2' and is greater than all the elements to the right of it.
There are no other superior elements present in the array.
Hence the final answer is [1,2].
```

**Sample Input 2:**

```
3
5 4 3
```

**Sample Output 2:**

```
3 4 5 
```

**Expected Time Complexity:**

```
Try to solve this in O(n).
```

**Constraints:**

```
1 <= n <=10^5 
1 <= a[i] <= 10^9
Time Limit: 1 sec
```

```Java
import java.util.*;
public class Solution {
    public static List< Integer > superiorElements(int []a) {
        // Write your code here.
        List<Integer> out = new ArrayList<>();
        int max = Integer.MIN_VALUE;

        for(int i=a.length - 1; i >= 0; i--) {
            if(a[i] > max) {
                out.add(a[i]);
                max = a[i];
            }
        }

        return out;
    }
}
```