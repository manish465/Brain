## Problem statement

Ninja and his friend are playing a game of subarrays. They have an array ‘NUMS’ of length ‘N’. Ninja’s friend gives him an arbitrary integer ‘K’ and asks him to find the length of the longest subarray in which the sum of elements is equal to ‘K’.

Ninjas asks for your help to win this game. Find the length of the longest subarray in which the sum of elements is equal to ‘K’.

If there is no subarray whose sum is ‘K’ then you should return 0.

**Example:**

```
Input: ‘N’ = 5,  ‘K’ = 4, ‘NUMS’ = [ 1, 2, 1, 0, 1 ]

Output: 4

There are two subarrays with sum = 4, [1, 2, 1] and [2, 1, 0, 1]. Hence the length of the longest subarray with sum = 4 is 4.
```

Detailed explanation ( Input/output format, Notes, Images )

**Constraints :**

```
1 <= T <= 10
1 <= N <= 10^5
-10^6 <= NUMS[ i ] <= 10^6
-10^6 <= K <= 10^6

Sum of N Over all the Test cases <= 10^5

Time Limit: 1 sec
```

**Sample Input 1 :**

```
2
3 5
2 3 5
3 1
-1 1 1
```

**Sample Output 1 :**

```
2
3
```

**Explanation Of Sample Input 1 :**

```
For the first case:
There are two subarrays with sum = 5, [2, 3] and [5]. Hence the length of the longest subarray is 2.

For the second case:
Longest subarray with sum = 1 is [1, -1, 1].
```

**Sample Input 2 :**

```
2
3 4
1 1 1
3 2
-50 0 52
```

**Sample Output 2 :**

```
0 
3
```

```Java
import java.util.* ;
import java.io.*;

public class Solution {
	public static int getLongestSubarray(int []nums, int k) {
		// Write your code here.
		int n = nums.length;
        Map<Long, Integer> preSum = new HashMap<>();
        int maxLen = 0;
        long sum = 0;

        for(int i=0; i < n; i++) {
            sum += nums[i];
            
            if(sum == k) {
                maxLen = Math.max(maxLen, (i + 1));
            }

            long rem = sum - k;

            if(preSum.containsKey(rem)) {
                int len = i - preSum.get(rem);
                maxLen = Math.max(maxLen, len);
            }

            if(!preSum.containsKey(sum)) {
                preSum.put(sum, i);
            }
        }

        return maxLen;
	}
}
```