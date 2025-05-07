---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/find-the-single-element_6680465?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=SUBMISSION
---
## Problem statement

You are given an array _**‘ARR’**_ of length _**‘N’**_ consisting of only ‘0’s and ‘1’s. Your task is to determine the maximum length of the consecutive number of 1’s.

**For Example:**

```
ARR = [0, 1, 1, 0, 0, 1, 1, 1], here you can see the maximum length of consecutive 1’s is 3. Hence the answer is 3.
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1:**

```
2
8
0 1 1 0 0 1 1 1
4
0 1 1 0
```

**Sample Output 1:**

```
3
2
```

**Explanation for Sample Output 1:**

```
For the first test case, ‘ARR’ = [0, 1, 1, 0, 0, 1, 1, 1], here you can see the maximum length of consecutive 1’s is 3 when we select ARR[5], ARR[6] and ARR[7]. Hence the answer is 3.

For the second test, ‘ARR’ = [0, 1, 1, 0], here you can see the maximum length of consecutive 1’s is 2 when we select ARR[1] and ARR[2]. Hence the answer is 2.
```

**Sample Input 2:**

```
2
6
1 1 1 1 0 0
4
1 1 1 1
```

**Sample Output 2:**

```
4
4
```

**Constraints:**

```
1 ≤ T ≤ 10
1 ≤ N ≤ 1000
ARR[i] = {0, 1}

Time Limit: 1 sec
```

```Java
import java.util.* ;
import java.io.*; 
public class Solution {
	public static int consecutiveOnes(int n, int[] arr) {
		// Write your code here.
		int len = 0,  maxLen = 0;

		for(int a : arr) {
			if(a == 1) len++;
			else len = 0;

			maxLen = Math.max(maxLen, len);
		}

		return maxLen;
	}
}
```