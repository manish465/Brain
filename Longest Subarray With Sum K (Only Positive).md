---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/longest-subarray-with-sum-k_6682399?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

You are given an array _**'a'**_ of size _**'n'**_ and an integer _**'k'**_.
Find the length of the longest subarray of 'a' whose sum is equal to 'k'.

**Example :**

```
Input: ‘n’ = 7 ‘k’ = 3
‘a’ = [1, 2, 3, 1, 1, 1, 1]

Output: 3

Explanation: Subarrays whose sum = ‘3’ are:

[1, 2], [3], [1, 1, 1] and [1, 1, 1]

Here, the length of the longest subarray is 3, which is our final answer.
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1 :**

```
7 3
1 2 3 1 1 1 1
```

  

**Sample Output 1 :**

```
3
```

  

**Explanation Of Sample Input 1 :**

```
Subarrays whose sum = ‘3’ are:
[1, 2], [3], [1, 1, 1] and [1, 1, 1]
Here, the length of the longest subarray is 3, which is our final answer.
```

  

**Sample Input 2 :**

```
4 2
1 2 1 3
```

  

**Sample Output 2 :**

```
1
```

  

**Sample Input 3 :**

```
5 2
2 2 4 1 2 
```

  

**Sample Output 3 :**

```
1
```

  

**Expected time complexity :**

```
The expected time complexity is O(n).
```

  

**Constraints :**

```
1 <= 'n' <= 5 * 10 ^ 6
1 <= 'k' <= 10^18
0 <= 'a[i]' <= 10 ^ 9

Time Limit: 1-second
```


```Java
import java.util.* ;
import java.io.*; 

public class Solution {
    public static int longestSubarrayWithSumK(int []a, long k) {
        // Write your code here
        int n = a.length;
        int left = 0, right = 0;
        long sum = 0;
        int maxLen = 0;

        while(right < n) {
            sum += a[right];

            while(sum > k) {
                sum -= a[left];
                left++;
            }

            if(sum == k) {
                maxLen = Math.max(maxLen, (right - left + 1));
            }

            right++;
        }

        return maxLen;
    }
}
```