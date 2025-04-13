---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/ninja-and-the-second-order-elements_6581960?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

You have been given an array _**‘a’**_ of _**‘n’**_ unique non-negative integers.
Find the second largest and second smallest element from the array.
Return the two elements (second largest and second smallest) as another array of size 2.

**Example :**

```
Input: ‘n’ = 5, ‘a’ = [1, 2, 3, 4, 5]
Output: [4, 2]

The second largest element after 5 is 4, and the second smallest element after 1 is 2.
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1 :**

```
4
3 4 5 2
```

**Sample Output 1 :**

```
4 3
```

**Explanation For Sample Input 1 :**

```
The second largest element after 5 is 4 only, and the second smallest element after 2 is 3.
```

**Sample Input 2 :**

```
5
4 5 3 6 7
```

**Sample Output 2 :**

```
6 4
```

**Expected Time Complexity:**

```
O(n), Where ‘n’ is the size of an input array ‘a’.
```

**Constraints:**

```
2 ≤ 'n' ≤ 10^5
0 ≤ 'a'[i] ≤ 10^9

Time limit: 1 sec
```

  

**Hints:**

```
1. Sort the array.
2. More efficiently, can you use the largest and smallest elements to find the required elements?
```


```Java
public class Solution {
    public static int[] getSecondOrderElements(int n, int []a) {
        // Write your code here.
        int firstL = Integer.MIN_VALUE, secondL = Integer.MIN_VALUE;
        int firstS = Integer.MAX_VALUE, secondS = Integer.MAX_VALUE;

        for(int num : a) {
            if(num > firstL) {
                secondL = firstL;
                firstL = num;
            } else if(num > secondL && num != firstL) {
                secondL = num;
            }

            if(num < firstS) {
                secondS = firstS;
                firstS = num;
            } else if(num < secondS && num != firstS) {
                secondS = num;
            }
        }

        return new int[]{secondL, secondS};
    }
}
```