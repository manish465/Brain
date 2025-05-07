---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/longest-successive-elements_6811740?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

There is an integer array ‘A’ of size ‘N’.
A sequence is successive when the adjacent elements of the sequence have a difference of 1.
You must return the length of the longest successive sequence.

Note:

```
You can reorder the array to form a sequence. 
```

For example,

```
Input:
A = [5, 8, 3, 2, 1, 4], N = 6
Output:
5
Explanation: 
The resultant sequence can be 1, 2, 3, 4, 5.    
The length of the sequence is 5.
```

Detailed explanation ( Input/output format, Notes, Images )

**Constraints:**

```
1 <= N <= 10^5
1 <= A[i] <= 10^9
Time Limit: 1 sec
```

```Java
import java.util.*;

public class Solution {
    public static int longestSuccessiveElements(int []a) {
        // Write your code here.
        Arrays.sort(a);

        int last = a[0], len = 1, maxLen = 1;

        for(int num : a) {
            if(last == num) continue;
            else if(last + 1 == num) {
                last = num;
                len++;
                maxLen = Math.max(maxLen, len);
            } else {
                last = num;
                len = 1;
            }
        }

        return maxLen;
    }
}
```

```Java
import java.util.*;

public class Solution {
    public static int longestSuccessiveElements(int []a) {
        // Write your code here.
        Set<Integer> set = new HashSet<>();
        for(int num : a) set.add(num);

        int maxLen = 1;

        for(int num : set) {
            if(set.contains(num - 1)) continue;

            int len = 1;
            int curr = num;

            while(set.contains(curr + 1)) {
                len++;
                curr++;
            }

            maxLen = Math.max(maxLen, len);
        }

        return maxLen;
    }
}
```