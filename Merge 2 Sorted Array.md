---
tags:
  - interview-prep
  - dsa
link: https://www.naukri.com/code360/problems/sorted-array_6613259?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=PROBLEM
---
## Problem statement

Given two sorted arrays, _**‘a’**_ and _**‘b’**_, of size _**‘n’**_ and _**‘m’**_, respectively, return the union of the arrays.

The union of two sorted arrays can be defined as an array consisting of the common and the distinct elements of the two arrays. The final array should be sorted in ascending order.

Note: 'a' and 'b' may contain duplicate elements, but the union array must contain unique elements.

**Example:**

```
Input: ‘n’ = 5 ‘m’ = 3
‘a’ = [1, 2, 3, 4, 6]
‘b’ = [2, 3, 5]

Output: [1, 2, 3, 4, 5, 6]

Explanation: Common elements in ‘a’ and ‘b’ are: [2, 3]
Distinct elements in ‘a’ are: [1, 4, 6]
Distinct elements in ‘b’ are: [5]
Union of ‘a’ and ‘b’ is: [1, 2, 3, 4, 5, 6]
```

Detailed explanation ( Input/output format, Notes, Images )

**Sample Input 1 :**

```
5 3
1 2 3 4 6
2 3 5
```

**Sample Output 1 :**

```
1 2 3 4 5 6
```

**Explanation Of Sample Input 1 :**

```
Input: ‘n’ = 5 ‘m’ = 3
‘a’ = [1, 2, 3, 4, 6]
‘b’ = [2, 3, 5]

Output: [1, 2, 3, 4, 5, 6]

Explanation: Common elements in ‘a’ and ‘b’ are: [2, 3]
Distinct elements in ‘a’ are: [1, 4, 6]
Distinct elements in ‘b’ are: [5]
Union of ‘a’ and ‘b’ is: [1, 2, 3, 4, 5, 6]
```

**Sample Input 2:**

```
4 3
1 2 3 3
2 2 4
```

**Sample Output 2:**

```
1 2 3 4
```

**Explanation Of Sample Input 2 :**

```
Input: ‘n’ = 5 ‘m’ = 3
‘a’ = [1, 2, 3, 3]
‘b’ = [2, 2, 4]

Output: [1, 2, 3, 4]

Explanation: Common elements in ‘a’ and ‘b’ are: [2]
Distinct elements in ‘a’ are: [1, 3]
Distinct elements in ‘b’ are: [4]
Union of ‘a’ and ‘b’ is: [1, 2, 3, 4]
```

**Expected Time Complexity:**

```
O(( N + M )), where 'N' and ‘M’ are the sizes of Array ‘A’ and ‘B’.
```

**Constraints :**

```
1 <= 'n', 'm' <= 10^5
-10^9 <= 'a'[i], 'b'[i] <= 10^9

Time Limit: 1 sec
```

```Java
import java.util.*;
public class Solution {
    public static List<Integer> sortedArray(int []a, int []b) {
        // Write your code here
        int n = a.length;
        int m = b.length;
        int i = 0;
        int j = 0;

        List<Integer> out = new ArrayList<>();

        while(i < n && j < m) {
            if(a[i] <= b[j]) {
                if(out.size() == 0 || out.get(out.size() - 1) != a[i]) {
                    out.add(a[i]);
                }
                i++;
            } else {
                if(out.size() == 0 || out.get(out.size() - 1) != b[j]) {
                    out.add(b[j]);
                }
                j++;
            }
        }

        while(i < n) {
            if(out.size() == 0 || out.get(out.size() - 1) != a[i]) {
                out.add(a[i]);
            }
            i++;
        }

        while(j < m) {
            if(out.size() == 0 || out.get(out.size() - 1) != b[j]) {
                    out.add(b[j]);
            }
            j++;
        }

        return out;
    }
}
```