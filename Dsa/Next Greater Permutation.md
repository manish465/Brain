---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/next-greater-permutation_6929564?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

You are given an array ‘a’ of ‘n’ integers.
You have to return the lexicographically next to greater permutation.

Note:

```
If such a sequence is impossible, it must be rearranged in the lowest possible order.
```

Example:

```
Input: 'a' = [1, 3, 2]

Output: 2 1 3

Explanation: All the permutations of [1, 2, 3] are [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1], ]. Hence the next greater permutation of [1, 3, 2] is [2, 1, 3].
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1:**

```
3
3 1 2
```

**Sample Output 1:**

```
3 2 1
```

**Explanation Of Sample Input 1:**

```
Input:
A = [3, 1, 2]
Output:
3 2 1

Explanation: All the permutations of [1, 2, 3] are [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1], ]. Hence the next greater permutation of [3, 1, 2] is [3, 2, 1].
```

**Sample Input 2:**

```
3
3 2 1
```

**Sample Output 2:**

```
1 2 3
```

**Constraints:**

```
1 <= n <= 100
1 <= a[ i ] <= 100
Time Limit: 1 sec
```

```Java
import java.util.*;
public class Solution {
    public static List< Integer > nextGreaterPermutation(List< Integer > A) {
        // Write your code here.
        int firstDipFromRight = getFirstDipFromRight(A);

        if(firstDipFromRight != -1) {
            int minIdxFromRight = getMinIdxFromRight(A, A.get(firstDipFromRight));
            swap(A, firstDipFromRight, minIdxFromRight);
            rev(A, firstDipFromRight + 1, A.size() - 1);

            return A;
        }

        rev(A, 0, A.size() - 1);
        return A;
    }

    private static int getFirstDipFromRight(List<Integer> nums) {
        int n = nums.size();

        for(int i=n-2; i >= 0; i--) {
            if(nums.get(i) < nums.get(i + 1)) {
                return i;
            }
        }

        return -1;
    }

    private static int getMinIdxFromRight(List<Integer> nums, int curr) {
        int n = nums.size();
    
        for(int i=n-1; i >= 0; i--) {
            if(nums.get(i) > curr) {
                return i;
            }
        }

        return -1;
    }

    private static void rev(List<Integer> nums, int start, int end) {
        while(start < end) {
            swap(nums, start, end);
            start++;
            end--;
        }
    }

    private static void swap(List<Integer> nums, int a, int b) {
        int temp = nums.get(a);
        nums.set(a, nums.get(b));
        nums.set(b, temp);
    }
}
```