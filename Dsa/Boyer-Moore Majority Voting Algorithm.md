---
tags:
  - dsa
---
The ***Boyer-Moore voting*** algorithm is one of the popular optimal algorithms which is used to find the majority element among the given elements that have more than N/ 2 occurrences. This works perfectly fine for finding the majority element which takes 2 traversals over the given elements, which works in O(N) time complexity and O(1) space complexity.

****Input :****{1,1,1,1,2,3,5}  
****Output :**** 1  
****Explanation :**** 1 occurs more than 3 times.  
****Input :**** {1,2,3}  
****Output :**** -1

```Java
import java.io.*;

class GFG
{

  // Function to find majority element
  public static int findMajority(int[] nums)
  {
    int count = 0, candidate = -1;

    // Finding majority candidate
    for (int index = 0; index < nums.length; index++) {
      if (count == 0) {
        candidate = nums[index];
        count = 1;
      }
      else {
        if (nums[index] == candidate)
          count++;
        else
          count--;
      }
    }

    // Checking if majority candidate occurs more than
    // n/2 times
    count = 0;
    for (int index = 0; index < nums.length; index++) {
      if (nums[index] == candidate)
        count++;
    }
    if (count > (nums.length / 2))
      return candidate;
    return -1;

    // The last for loop and the if statement step can
    // be skip if a majority element is confirmed to
    // be present in an array just return candidate
    // in that case
  }

  // Driver code
  public static void main(String[] args)
  {
    int arr[] = { 1, 1, 1, 1, 2, 3, 4 };
    int majority = findMajority(arr);
    System.out.println(" The majority element is : "
                       + majority);
  }
}

// This code is contributed by Arnav Sharma
```