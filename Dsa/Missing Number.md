---
tags:
  - dsa
  - interview-prep
link: https://www.naukri.com/code360/problems/missing-number_6680467?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

Given an array _**‘a’**_ of size _**‘n’**_-1 with elements of range 1 to ‘n’. The array does not contain any duplicates. Your task is to find the missing number.

**For example:**

```
Input:
'a' = [1, 2, 4, 5], 'n' = 5

Output :
3

Explanation: 3 is the missing value in the range 1 to 5.
```

Detailed explanation ( Input/output format, Notes, Images )

##### Sample Input 1 :

```
4 
1 2 3
```

##### Sample Output 1:

```
4
```

##### Explanation Of Sample Input 1:

```
4 is the missing value in the range 1 to 4.
```

##### Sample Input 2:

```
8
1 2 3 5 6 7 8
```

##### Sample Output 2:

```
4
```

##### Explanation Of Sample Input 2:

```
4 is the missing value in the range 1 to 8.
```

##### Expected time complexity:

```
The expected time complexity is O(n).
```

##### Constraints:

```
1 <= 'n' <= 10^6 
1 <= 'a'[i] <= 'n'
Time Limit: 1 sec
```

```Java
public class Solution {
    public static int missingNumber(int []a, int N) {
        // Write your code here.
        int expSum = (N * (N + 1)) / 2;
        int accSum = 0;

        for(int num : a) {
            accSum+= num;
        }

        return expSum - accSum;
    }
}
```

```Java
public class Solution {
    public static int missingNumber(int []a, int N) {
        // Write your code here.
        int xor1 = 0;
        int xor2 = 0;

        for(int i=0; i < a.length; i++) {
            xor1 = xor1 ^ a[i];
            xor2 = xor2 ^ (i + 1);
        }

        return xor1 ^ xor2;
    }
}
```