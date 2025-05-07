---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/sort-an-array-of-0s-1s-and-2s_892977?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

You have been given an array/list _**'arr'**_ consisting of _**'n'**_ elements.
Each element in the array is either 0, 1 or 2.
Sort this array/list in increasing order.
Do not make a new array/list. Make changes in the given array/list.

**Example :**

```
Input: 'arr' = [2, 2, 2, 2, 0, 0, 1, 0]

Output: Final 'arr' = [0, 0, 0, 1, 2, 2, 2, 2]

Explanation: The array is sorted in increasing order.
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1:**

```
8
2 2 2 2 0 0 1 0
```

**Sample Output 1:**

```
0 0 0 1 2 2 2 2
```

**Explanation of sample input 1 :**

```
The initial array 'arr' is [2, 2, 2, 2, 0, 0, 1, 0].

After sorting the array in increasing order, 'arr' is equal to:
[0, 0, 0, 1, 2, 2, 2, 2]
```

**Sample Input 2:**

```
5
1 1 1 1 1
```

**Sample Output 2:**

```
1 1 1 1 1
```

**Expected time complexity :**

```
The expected time complexity is O(n).
```

**Constraints:**

```
1 <= 'n' <= 10 ^ 4
0 <= 'arr[i]' <= 2

Time limit: 1 second
```

```Java
import java.util.* ;
import java.io.*; 
public class Solution {
    public static void sortArray(ArrayList<Integer> arr, int n) {
        // Write your code here.
        int low = 0, mid = 0, high = n - 1;

        while(mid <= high) {
            if(arr.get(mid) == 0) {
                swap(arr, mid, low);
                low++;
                mid++;
            } else if(arr.get(mid) == 1) {
                mid++;
            } else {
                swap(arr, mid, high);
                high--;
            }
        }
    }

    private static void swap(ArrayList<Integer> arr, int a, int b) {
        int temp = arr.get(a);
        arr.set(a, arr.get(b));
        arr.set(b, temp);
    }
}
```